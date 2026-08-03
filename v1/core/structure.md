# Structure of the Core Submodule

## Summary

Maps what lives inside the Core submodule — its five modules and the kind of code each one holds — and shows where the boundary falls between Core and the applications that include it.

## Details

[Core](introduction.md) is not a single directory of loose classes.
It is organized into five modules, each a PSR-4 namespace mapped under `src/Core/src/`, so the shared codebase is grouped by domain rather than by file type.

Every application that includes the submodule gets all five, and every application sees exactly the same definitions.

```text
   ┌───────────┐   ┌───────────┐   ┌───────────┐
   │    API    │   │   Admin   │   │   Queue   │
   │ handlers  │   │ templates │   │ consumers │
   │ HAL, HTTP │   │ forms, UI │   │ workers   │
   └─────┬─────┘   └─────┬─────┘   └─────┬─────┘
         │               │               │
         └───────────────┼───────────────┘
                         │  each includes Core
                         ▼
              ┌─────────────────────┐
              │        Core         │
              │  entities · repos   │
              │  enums · DBAL types │
              └──────────┬──────────┘
                         ▼
                ┌─────────────────┐
                │    database     │
                └─────────────────┘
```

Note that every arrow points one way.
The applications know about Core; Core knows nothing about any application.
Core contains no handler, no template, no route and no middleware — which is what makes it safe to include everywhere.

### The five modules

| Module | Namespace | Holds |
| --- | --- | --- |
| App | `Core\App` | The base entity and its traits, the abstract repository, DBAL enum and UUID types, table-prefix and entity-listener wiring, data fixtures, shared services (`MailService`, `IpService`), the paginator helper and shared messages |
| Admin | `Core\Admin` | The `Admin`, `AdminRole`, `AdminLogin` and `AdminIdentity` entities with their repositories, plus the admin role and status enums |
| User | `Core\User` | The `User`, `UserDetail`, `UserAvatar`, `UserRole` and `UserResetPassword` entities with their repositories, the user status and role enums, and the avatar event listener |
| Security | `Core\Security` | OAuth2 persistence — the access token, refresh token, auth code, client and scope entities, plus the repositories the authorization server requires |
| Setting | `Core\Setting` | The `Setting` entity, its identifier enum and repository, for platform-wide configuration kept in the database |

`Core\App` is the one module that is not a domain in its own right.
It holds the pieces the other four build on — the abstract entity every entity extends, the abstract repository every repository extends, and the Doctrine infrastructure that makes UUID identifiers and enum columns work.

### How the modules are registered

Each module ships its own [ConfigProvider](../config-provider/introduction.md), and every application registers all five in `config/config.php`:

```php
// Dotkernel modules
Core\Admin\ConfigProvider::class,
Core\App\ConfigProvider::class,
Core\Security\ConfigProvider::class,
Core\Setting\ConfigProvider::class,
Core\User\ConfigProvider::class,
```

This is why including the submodule is enough to get the whole domain layer: the entities, repositories and DBAL types register themselves, exactly as they do in every other application on the platform.

The PSR-4 map in `composer.json` points at the submodule path, so it needs no change when a plain `src/Core` folder becomes a submodule mounted at the same location:

```json
"autoload": {
    "psr-4": {
        "Core\\Admin\\": "src/Core/src/Admin/src/",
        "Core\\App\\": "src/Core/src/App/src/",
        "Core\\Security\\": "src/Core/src/Security/src/",
        "Core\\Setting\\": "src/Core/src/Setting/src/",
        "Core\\User\\": "src/Core/src/User/src/"
    }
}
```

### Where the boundary falls

The question that comes up on almost every feature is whether the new code belongs in Core or in the application.
The dividing line is delivery: Core describes what the data *is*, the application describes how it is *delivered*.

```text
  application (API / Admin / Queue)
  ┌──────────────────────────────────────────────────┐
  │  Handler / Consumer    HTTP or message entry     │
  │  InputFilter / Form    validates this interface  │
  │  Service               this application's flow   │
  └────────────────────────┬─────────────────────────┘
                           │  depends on
  Core                     ▼
  ┌──────────────────────────────────────────────────┐
  │  Service (shared)      MailService, IpService    │
  │  Repository            querying and persistence  │
  │  Entity + Enum         the model itself          │
  └──────────────────────────────────────────────────┘
```

Use this as a checklist:

- **Belongs in Core** — entities and the state changes intrinsic to them, repositories, enums, DBAL types, data fixtures, Doctrine listeners and factories, and any service that behaves identically no matter which application calls it.
- **Belongs in the application** — handlers and consumers, middleware, routes, input filters and forms, templates, HAL resources, OpenAPI annotations, and the services that express that application's own workflows.
- **Never in Core** — anything that imports a PSR-7 message, a template renderer, a session, a HAL type or a Messenger envelope.
If Core would need to know how the request arrived, the code is on the wrong side of the line.

The service layer is the case worth understanding properly, because it sits on both sides: shared services such as `MailService` live in Core, while application-specific ones do not.
API and Admin each have their own `UserService`, both operating on the same `Core\User\Entity\User` through the same `Core\User\Repository\UserRepository`.
That is deliberate rather than duplication — the two applications present the same operation very differently while the model underneath stays single.
[The Service Layer](../services.md) covers the reasoning in full.

### Core owns the schema

Because the entities live in Core, Doctrine generates migrations from Core's mappings.
That makes the schema a shared asset, and it needs a single owner.

Decide once which application is responsible for generating and running migrations — normally the API — and keep it there.
Two applications generating migrations independently against the same mappings will produce conflicting histories, and reconciling them after the fact is considerably harder than agreeing the convention up front.

## FAQ

**Q: How many modules does Core contain?**

A: Five — `Core\App`, `Core\Admin`, `Core\User`, `Core\Security` and `Core\Setting`, each mapped under `src/Core/src/`.

**Q: What is `Core\App` for, if it isn't a domain?**

A: It holds the foundations the other modules build on: the abstract entity and repository, the DBAL enum and UUID types, the Doctrine wiring, data fixtures and the shared services.

**Q: Do I have to register each Core module separately?**

A: Yes. All five ConfigProviders are listed in each application's `config/config.php`, which is what makes the entities and DBAL types available.

**Q: How do I decide whether new code goes in Core or in my application?**

A: Ask whether it describes the data or the delivery. Entities, repositories, enums and DBAL types describe the data and belong in Core; handlers, templates, input filters and application-specific services describe delivery and stay in the application.

**Q: Why do API and Admin each have their own `UserService` if Core is meant to prevent duplication?**

A: Because they are different workflows over the same model. Both use `Core\User\Entity\User` and `Core\User\Repository\UserRepository`, so the data has one definition even though the two applications present it differently.

**Q: Which application should run the Doctrine migrations?**

A: One of them, chosen deliberately — usually the API. Because Core owns the entities, migrations generated independently by two applications will conflict.

**Q: Does the `composer.json` autoload section change when Core becomes a submodule?**

A: No. The submodule is mounted at the same `src/Core` path, so the PSR-4 map continues to resolve. Run `composer dump-autoload` after the switch.

## See also

- [Introduction](introduction.md)
- [Creating a Core Submodule](creation.md)
- [Using the Core Submodule](usage.md)
- [The Service Layer](../services.md)
- [Architecture Overview](../architecture.md)
