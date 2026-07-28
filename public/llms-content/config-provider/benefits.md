---
title: Benefits
description: Lists the benefits of using a ConfigProvider, including centralized, modular, container-friendly, and testable configuration.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/config-provider/benefits"
category: "Development"
language: "en"
---

# Benefits

## TL;DR

Using a ConfigProvider instead of hardcoding bootstrap logic gives you centralized, modular configuration that works with any DI container (Laminas ServiceManager, PHP-DI, Pimple), standardizes how services are defined, stays environment-agnostic across dev/test/prod, and makes isolated testing easier. In Dotkernel, ConfigProviders must be registered manually in `config/config.php`, since only the initial ConfigProviders required to install the applications are injected automatically.

## FAQ

**Q: Why use a ConfigProvider instead of hardcoding bootstrap code?**
A: It centralizes configuration so it's easy to read, change, or extend.

**Q: Does a ConfigProvider work with dependency injection containers?**
A: Yes, it's container-friendly and works with DI containers like Laminas ServiceManager, PHP-DI, or Pimple.

**Q: Do I need to register Dotkernel ConfigProviders manually?**
A: Yes, Dotkernel ConfigProviders must be added manually in `config/config.php`.
