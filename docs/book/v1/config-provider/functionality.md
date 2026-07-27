# How the ConfigProvider works

## Summary

Walks through how the ConfigProvider is picked up during bootstrap, merged, resolved, and executed within the Mezzio middleware pipeline.

## Details

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

## FAQ

**Q: When is the ConfigProvider picked up?**
A: Automatically, by the framework during application bootstrap.

**Q: What happens during the "Resolve item" step?**
A: `$app->pipe()` resolves a service name from the container, wraps a middleware array, or calls a closure/invokable object.

**Q: Why does the error-handling middleware run last in the pipeline?**
A: So it can catch any exceptions raised by the preceding middleware.
