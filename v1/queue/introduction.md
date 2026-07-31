# Introduction

## Summary

An overview of Dotkernel Queue, a Mezzio-based microservice for processing asynchronous tasks via message queues.

## Details

Dotkernel Queue is a standalone application (skeleton) for handling asynchronous task processing as its own microservice, separate from your API or Admin application.

Dotkernel Queue:

- Is built on the Mezzio microframework, sharing the same architecture and standards support as other Dotkernel tools and applications.
- Uses Laminas Messenger to dispatch and handle messages, so work can be processed outside the request/response cycle.
- Lets you offload slow or non-critical work — such as sending emails, generating exports, or processing uploads — from your API or Admin application.
- Has a PSR-Compliant Middleware Stack to promote a lean, modular architecture and create a common ground between components from various sources.
- Implements [PSR-7](https://www.php-fig.org/psr/psr-7/) (HTTP message interfaces) and [PSR-15](https://www.php-fig.org/psr/psr-15/) (HTTP Server Request Handlers) as defined by the [PHP Framework Interop Group](https://www.php-fig.org/).

## FAQ

**Q: What is Dotkernel Queue?**

A: A standalone microservice for processing asynchronous tasks, separate from your API or Admin application.

**Q: What is Dotkernel Queue built on?**

A: The Mezzio microframework, using Laminas Messenger to dispatch and handle messages.

**Q: Why would I use Dotkernel Queue?**

A: To offload slow or non-critical work, such as sending emails, generating exports, or processing uploads, so it doesn't block the request/response cycle.

## See also

- [Usage](usage.md) — how Queue fits alongside API and Admin.
- [Architecture Overview](../architecture.md) — how all the platform pieces fit together.
