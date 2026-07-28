# Introduction

## Summary

Introduces the Core submodule as the shared codebase and single source of truth for database entities across Dotkernel applications.

## Details

The Core submodule is a common codebase set up to be used by the Dotkernel applications you added to your project.
The project setup may differ - e.g. two APIs, one Admin, 3 Frontends - but the Core submodule can be included in all of them.

By having a common module in your Dotkernel applications, you ensure that each of them uses entities and services in the same way.
It helps to make service updates easier to sync across all the applications in your platform.

General rules:

- The golden rule for the Core codebase is that it is the only place which manages the database entities.
- As much as possible, all Doctrine entities must reside in Core.
- The current location of the Core submodule is `src/Core`.

[Shared Core Submodule in Dotkernel Headless Platform](https://www.dotkernel.com/headless-platform/shared-core-submodule-in-dotkernel-headless-platform/)

## FAQ

**Q: Can the same Core submodule be used across multiple applications?**
A: Yes, it can be included in any combination of APIs, Admins, and Frontends in your project.

**Q: What is the golden rule for the Core codebase?**
A: It's the only place that manages the database entities.

**Q: Where is the Core submodule located?**
A: At `src/Core`.

## See also

- [Benefits of the Core Submodule](benefits.md)
- [Creating a Core Submodule](creation.md)
- [Using the Core Submodule](usage.md)
