# The Service Layer

## Summary

Explains why Dotkernel keeps business logic in dedicated Service classes instead of in request handlers, entities, or repositories, and lists the advantages of that separation over the alternatives.

## Details

Every Dotkernel module splits its code by responsibility, and business logic gets a directory of its own:

```text
src/User/src/
├── Handler/      # PSR-15 request handlers — HTTP in, HTTP out
├── InputFilter/  # validation of incoming data
├── Service/      # business logic
└── ConfigProvider.php
```

Entities and repositories live alongside them (in the [Core submodule](core/introduction.md), once you have one), so a single feature is spread across four narrow layers rather than one wide class:

- **Handler** — reads the request, calls a Service, turns the result into a response.
- **Service** — the business rules: what "activating a user" actually means.
- **Repository** — retrieving and persisting entities.
- **Entity** — the data and the state changes intrinsic to it.

### What that looks like in practice

A handler stays thin. It declares the Service it needs as a constructor dependency, delegates, and returns:

```php
class PatchUserActivateHandler extends AbstractHandler
{
    #[Inject(MailService::class, UserServiceInterface::class, RendererInterface::class)]
    public function __construct(
        protected MailService $mailService,
        protected UserServiceInterface $userService,
        protected RendererInterface $renderer,
    ) {
    }

    public function handle(ServerRequestInterface $request): ResponseInterface
    {
        $user = $request->getAttribute(User::class);
        if ($user->isActive()) {
            throw ConflictException::create(Message::USER_ALREADY_ACTIVATED);
        }

        $this->userService->activateUser($user);
        $this->mailService->sendActivationMail(
            $user,
            $this->renderer->render('user::activate', ['user' => $user])
        );

        return $this->infoResponse(Message::USER_ACTIVATED);
    }
}
```

The Service holds the rules and the orchestration, and it is the only layer that knows the *sequence* of steps a business operation requires:

```php
public function deleteUser(User $user): User
{
    $this->revokeTokens($user);

    return $this->anonymizeUser($user);
}
```

Note that separating Services does not mean emptying your entities.
`UserService::activateUser()` calls `$user->activate()` and then hands the entity to the repository.
State changes stay on the entity, while the surrounding workflow (revoking tokens, anonymizing, saving, notifying) stays in the Service.

### Services are injected, never instantiated

Each Service is registered in its module's [ConfigProvider](config-provider/introduction.md) and resolved through the DI container, and Dotkernel ships each one behind an interface (`UserServiceInterface`, `AdminServiceInterface`, `SettingServiceInterface`, etc.).
Consumers depend on the interface, so the implementation can be replaced without touching a single handler.
You can use your own subclass, a decorator that adds caching or logging, or a fake in a test.

### Advantages

- **Reuse across entry points** — the same Service backs an HTTP handler, a CLI command, and a [Queue](queue/introduction.md) consumer.
Business logic written inside a request handler can only ever be reached over HTTP.
- **Reuse across applications** — shared Services such as `MailService` and `IpService` live in the [Core submodule](core/usage.md) and are consumed identically by API, Admin, and Queue, so a fix lands once instead of once per repository.
- **Testable without a framework** — a Service takes repositories and config in its constructor, so you unit test it with plain objects.
Testing the same logic embedded in a handler means building a PSR-7 request and asserting against a response body.
- **Swappable implementations** — because consumers depend on `…ServiceInterface`, you override behavior by rebinding one entry in a ConfigProvider.
- **One obvious place to look** — "where does user deletion happen?" has a single answer.
This is what makes onboarding and bugfixing cheap as the platform grows (see [Benefits of the Core Submodule](core/benefits.md)).
- **Contained change** — switching from synchronous email to a queued job, or from one payment provider to another, touches the Service.
Handlers, routes, and templates stay as they are.
- **Consistent rules** — API and Admin can present the same operation very differently while both calling the same Service, so the two applications cannot drift into two subtly different definitions of the same business rule.

### Versus the alternatives

Let's consider the alternative architectures and what each one costs you.
These are the places where business logic ends up when it isn't given a layer of its own.

| Alternative                                         | What it looks like                                                       | Why Dotkernel avoids it                                                                                                                                              |
|-----------------------------------------------------|--------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Logic in the request handler** ("fat controller") | The handler validates, queries, applies rules, saves, and sends mail     | Reachable only over HTTP; needs a full request to test; the same rule gets copy-pasted into the next handler that needs it                                           |
| **Logic in the entity** ("fat model")               | `$user->activate()` also revokes tokens and sends the activation email   | Entities are hydrated by Doctrine, not by the DI container, so they can't cleanly receive a mailer or repository; persistence concerns end up tangled with workflows |
| **Logic in the repository**                         | Repository methods orchestrate several entities and trigger side effects | Repositories are about retrieving and persisting; mixing in orchestration makes them application-specific and no longer safe to share through Core                   |
| **Logic in middleware**                             | Business rules enforced by pipeline middleware                           | Only fires on HTTP paths, depends on pipeline ordering, and is invisible to CLI and Queue execution                                                                  |
| **Logic duplicated per application**                | API and Admin each implement user activation their own way               | Every bug is fixed twice, and the two implementations drift apart over time                                                                                          |
| **Static helpers / utility classes**                | `UserHelper::activate($user)`                                            | Nothing to inject and nothing to substitute, so tests and alternative implementations both have to reach around the helper                                           |

Every one of these alternatives works right up until a second caller, a second application, or a second developer arrives — and then the logic has to be found, untangled, and copied.
Dotkernel gives business logic its own layer from the start, so it is written once, injected wherever it is required, tested in isolation, and shared through [Core](core/introduction.md) instead of duplicated.
Adding a Queue consumer or an Admin screen on top of existing rules becomes a matter of calling a Service, not of reimplementing it.

## FAQ

**Q: Why not just put the business logic in the request handler?**

A: Because logic inside a handler is only reachable over HTTP. A Service can be called from a handler, a CLI command, or a Queue consumer, and it can be unit tested without constructing a request.

**Q: Does using Services mean my entities should have no behaviour?**

A: No. State changes intrinsic to the entity stay on the entity — `UserService::activateUser()` calls `$user->activate()`. The Service owns the surrounding workflow: saving, revoking tokens, and sending notifications.

**Q: What's the difference between a Service and a Repository?**

A: A repository retrieves and persists entities. A Service applies business rules and orchestrates the steps of an operation, calling one or more repositories to do so.

**Q: Why does every Service have an interface?**

A: So consumers depend on `…ServiceInterface` rather than a concrete class. You can swap in your own implementation, decorate it, or mock it in tests by rebinding one entry in a ConfigProvider.

**Q: Where should a Service live — in the application or in Core?**

A: In Core if more than one application needs it, as with `MailService` and `IpService`. Keep it in the application if only that application uses it.

## See also

- [Architecture Overview](architecture.md)
- [Using the Core Submodule](core/usage.md)
- [ConfigProvider: Introduction](config-provider/introduction.md)
- [Glossary](glossary.md)
