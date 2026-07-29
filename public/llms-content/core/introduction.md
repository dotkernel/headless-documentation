---
title: Introduction
description: Introduces the Core submodule as the shared codebase and single source of truth for database entities across Dotkernel applications.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/core/introduction"
category: "Development"
language: "en"
---

# Introduction

## TL;DR

The Core submodule is a common codebase that can be included in any combination of Dotkernel applications in your project (e.g. two APIs, one Admin, three Frontends), ensuring they all use entities and services the same way and making service updates easier to sync across the platform. Its golden rule is that Core is the only place that manages database entities — as much as possible, all Doctrine entities should live there, currently at `src/Core`.

## FAQ

**Q: Can the same Core submodule be used across multiple applications?**
A: Yes, it can be included in any combination of APIs, Admins, and Frontends in your project.

**Q: What is the golden rule for the Core codebase?**
A: It's the only place that manages the database entities.

**Q: Where is the Core submodule located?**
A: At `src/Core`.
