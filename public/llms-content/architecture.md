---
title: Architecture Overview
description: Ties together the four building blocks of the Dotkernel Headless Platform — API, Admin, Queue, and the Core submodule — and shows how they combine into a single platform.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/architecture"
category: "Development"
language: "en"
---

# Architecture Overview

## TL;DR

The Dotkernel Headless Platform implements the headless principle with four independent building blocks, each in its own Git repository: API (exposes data), Admin (manages data via a table UI), Queue (asynchronous task processing), and a Core submodule (shared entities and services). You can start with just one piece — typically Admin or API — and add the others as requirements grow, sharing logic through Core once you're running more than one application; every piece boots the same way, through its own ConfigProvider.

## FAQ

**Q: What are the building blocks of the Dotkernel Headless Platform?**
A: Dotkernel API, Dotkernel Admin, Dotkernel Queue, and the Core submodule.

**Q: Do I need all four components to get started?**
A: No, you can start with just Admin or just API and add the others as your requirements grow.

**Q: How do multiple applications stay consistent with each other?**
A: By sharing a Core submodule for entities and services, and by each bootstrapping through its own ConfigProvider.
