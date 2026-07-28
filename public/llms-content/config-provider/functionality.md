---
title: How the ConfigProvider works
description: Walks through how the ConfigProvider is picked up during bootstrap, merged, resolved, and executed within the Mezzio middleware pipeline.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/config-provider/functionality"
category: "Development"
language: "en"
---

# How the ConfigProvider works

## TL;DR

The framework picks up every ConfigProvider automatically during bootstrap and merges them into one global configuration array. `$app->pipe()` then resolves each pipeline entry — a service name from the container, a middleware array, or a closure/invokable — with the error-handling middleware registered last so it can catch exceptions from everything before it. At runtime, Laminas Stratigility iterates the pipeline in registration order, letting each middleware handle the request or delegate to the next until a response is returned.

## FAQ

**Q: When is the ConfigProvider picked up?**
A: Automatically, by the framework during application bootstrap.

**Q: What happens during the "Resolve item" step?**
A: `$app->pipe()` resolves a service name from the container, wraps a middleware array, or calls a closure/invokable object.

**Q: Why does the error-handling middleware run last in the pipeline?**
A: So it can catch any exceptions raised by the preceding middleware.
