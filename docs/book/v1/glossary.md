# Glossary

## Summary

Plain-language definitions for the standards, frameworks, and terms used throughout this documentation.

## Details

**ConfigProvider**
A PHP class, part of an application's bootstrap process, that returns an array of configuration such as dependency injection mappings, request handlers, and template paths.
See [ConfigProvider: Introduction](config-provider/introduction.md).

**Core submodule**
The shared codebase, included as a Git submodule, that centralizes database entities and services across the Dotkernel applications in your platform.
See [Core: Introduction](core/introduction.md).

**Dependency injection (DI) container**
A framework component (e.g. Laminas ServiceManager, PHP-DI, Pimple) that creates and wires together an application's objects based on configuration, instead of that wiring being hardcoded.

**Doctrine**
The object-relational mapper (ORM) Dotkernel API and Admin use to manage database entities against a relational database such as MariaDB or MySQL.

**Git submodule**
A Git feature that lets one repository include another repository at a fixed path, so shared code (like the Core submodule) can be versioned and updated independently of the applications that include it.
See [Creating a Core Submodule](core/creation.md).

**Headless Platform**
An architecture that decouples the user interface (frontend) from the backend services, so the backend's responses can be consumed by any number of other systems, such as websites or mobile apps.
See [Introduction](introduction.md).

**Mezzio**
The PHP micro-framework, part of the Laminas project, that Dotkernel API, Admin, and Queue are all built on.

**Middleware**
A unit of code that sits in a request/response pipeline, able to handle a request and return a response, or delegate to the next middleware in line.
Dotkernel applications use a PSR-Compliant Middleware Stack for this.

**Monolith**
A single, tightly coupled codebase where features aren't separated into independent modules — the usual starting point for a [Modular Refactoring](migration/modular-refactoring.md).

**PHP-FIG**
The PHP Framework Interop Group, the organization behind the PSR (PHP Standard Recommendation) specifications, including PSR-7 and PSR-15.

**PSR-7**
The PSR specification defining HTTP message interfaces (requests and responses) in PHP.

**PSR-15**
The PSR specification defining HTTP server request handlers and middleware interfaces in PHP.

**Replatforming**
Moving a software system to a new infrastructure or environment — for example, from on-premises servers to the cloud — as part of a broader [migration](migration/introduction.md).

**Service**
A class that holds business logic — the rules and the sequence of steps an operation requires — kept separate from request handlers, entities, and repositories, and injected through the DI container behind an interface.
See [The Service Layer](services.md).

**Stratigility**
The Laminas library that implements the middleware pipeline Mezzio applications run on, iterating over registered middleware in order until a response is returned.
See [How the ConfigProvider works](config-provider/functionality.md).
