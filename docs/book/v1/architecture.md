# Architecture Overview

## Summary

Ties together the four building blocks of the Dotkernel Headless Platform — API, Admin, Queue, and the Core submodule — and shows how they combine into a single platform.

## Details

The [Headless Platform](introduction.md) principle is to decouple the frontend from the backend services, so any number of outside systems can consume the same backend.
Dotkernel implements this with four building blocks, each its own Git repository, which you combine based on your needs:

- **[Dotkernel API](api/introduction.md)** exposes your data to 3rd-party frontends or backends.
- **[Dotkernel Admin](admin/introduction.md)** (optional) manages the data through a simple table-based UI, with built-in reports and graphs.
- **[Dotkernel Queue](queue/introduction.md)** (optional) handles asynchronous task processing as its own microservice.
- **[Core submodule](core/introduction.md)** is the shared codebase that any of the above applications can include, so they all manage database entities and services the same way.

You don't need every piece from the start.
You can begin with [just Admin](admin/usage.md) or [just API](api/usage.md) and add the others later as requirements grow.
Once you're running more than one application, pull the shared logic out into a [Core submodule](core/creation.md) and include it in each one — a typical setup looks like API + Core, Admin + Core, and Queue + Core, each in its own repository, all reading from the same shared entities and services (see [Using the Core Submodule](core/usage.md)).

Regardless of which pieces you use, every Dotkernel application and package boots the same way: through a [ConfigProvider](config-provider/introduction.md) that declares its dependencies, handlers, and configuration, merged together by the framework at [bootstrap time](config-provider/functionality.md).

## FAQ

**Q: What are the building blocks of the Dotkernel Headless Platform?**

A: Dotkernel API, Dotkernel Admin, Dotkernel Queue, and the Core submodule.

**Q: Do I need all four components to get started?**

A: No, you can start with just Admin or just API and add the others as your requirements grow.

**Q: How do multiple applications stay consistent with each other?**

A: By sharing a Core submodule for entities and services, and by each bootstrapping through its own ConfigProvider.
