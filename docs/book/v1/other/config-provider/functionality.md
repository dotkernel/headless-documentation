## How the ConfigProvider works

The ConfigProvider is automatically picked up by the framework during application bootstrap.
Let's look at it step by step:

- **Merge the global configuration** - All ConfigProviders are merged into one array.
- **Read the configuration array** - The call is similar to the below and expects an array of entries:

```php
$config = $container->get('config')['key'] ?? [];
```

- **Resolve item** - `$app->pipe()` is called to resolve one of the below instances:
    - Resolve the service name from the container
    - Wrap the middleware, if an array is provided
    - Call the closure or invokable object.
- **Handle errors** - This middleware is the last one in the pipeline to make sure it handles any exceptions.
- **Execute at runtime** - [Laminas Stratigility](https://docs.laminas.dev/laminas-stratigility/) iterates over the pipeline in the order it was registered.
    - Each middleware can **handle** the request and return a response, or **delegate** execution to the next middleware in the pipeline, until a `ResponseInterface` is returned to the client.

Below you can see how Mezzio and Dotkernel merge and use ConfigProviders to build the middleware pipeline and dependencies.

![Headless Platform with Core Submodule](https://docs.dotkernel.org/img/headless-platform/ConfigProvider.png)
