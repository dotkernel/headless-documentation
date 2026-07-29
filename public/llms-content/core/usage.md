---
title: Using the Core Submodule
description: Explains how multiple applications share the Core submodule, what kinds of entities live in each application versus Core, and when to add new shared code to Core.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/core/usage"
category: "Development"
language: "en"
---

# Using the Core Submodule

## TL;DR

Once separated out, the Core submodule is imported into each application (e.g. API + Core, Admin + Core, Queue + Core), with each box representing its own Git repository that developers should keep up to date with the latest Core. Applications keep their own entities — Admin has admins, admin logins, and settings entities, while API has users, admins, and authentication entities — but any identical, shared entities belong in Core; not all new code needs to go there, since functionality used by only one application can stay in that application.

## FAQ

**Q: What does a platform using the Core submodule look like?**
A: Each application (API, Admin, Queue) pairs with Core, with each box being a separate Git repository.

**Q: Should all new code go into Core?**
A: No, only shared code should go into Core — functionality used by only one application can stay in that application.

**Q: What kinds of entities are already split between applications?**
A: For example, Admin has admins, admin logins, and settings entities, while API has users, admins, and authentication entities.
