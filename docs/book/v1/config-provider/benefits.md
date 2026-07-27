# Benefits

## Summary

Lists the benefits of using a ConfigProvider, including centralized, modular, container-friendly, and testable configuration.

## Details

- **Centralized setup** – Instead of hardcoding bootstrap code, you declare it in a config provider so it's easy to read, change, or extend.
- **Modular** – Each package can ship with its own config without interfering with others.
- **Container-friendly** – It works well with frameworks using DI containers like Laminas ServiceManager, PHP-DI, or Pimple.
- **Standardized service definitions** - It has consistent rules for object creation that are separate from business logic.
- **Environment-agnostic** - It returns an array that defines dev, test, or prod environments.
- **Testability** - The consistent, central configuration promotes isolated (e.g. per-module) testing, easier swapping of dependencies and the assertion of pipeline setup (e.g. check if a config key is present).

> **Dotkernel ConfigProviders** have to be **added manually** in `config/config.php`, because all the initial ConfigProviders required to install the applications are already injected.

## FAQ

**Q: Why use a ConfigProvider instead of hardcoding bootstrap code?**
A: It centralizes configuration so it's easy to read, change, or extend.

**Q: Does a ConfigProvider work with dependency injection containers?**
A: Yes, it's container-friendly and works with DI containers like Laminas ServiceManager, PHP-DI, or Pimple.

**Q: Do I need to register Dotkernel ConfigProviders manually?**
A: Yes, Dotkernel ConfigProviders must be added manually in `config/config.php`.
