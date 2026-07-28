---
title: Choosing a Migration Strategy
description: A decision guide comparing the Full Rewrite, Modular Refactoring, and Strangler Fig migration strategies, to help you pick the right one for your situation.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/migration/choosing-a-strategy"
category: "Development"
language: "en"
---

# Choosing a Migration Strategy

## TL;DR

Full Rewrite, Modular Refactoring, and the Strangler Fig Pattern trade off risk, timeline, and cost differently: Full Rewrite suits small or simple systems (or ones too tightly coupled to migrate incrementally), Modular Refactoring is used to decompose a large monolith into independent modules first, and the Strangler Fig Pattern then migrates those modules one at a time with low risk and continuous delivery — in practice, the latter two are often used together.

## FAQ

**Q: Which migration strategy has the lowest risk?**
A: The Strangler Fig Pattern, since each change is small, reversible, and easy to test in isolation.

**Q: When does a Full Rewrite make sense?**
A: Mainly for small or simple systems, or when the existing codebase is too tightly coupled for an incremental migration to be practical.

**Q: How do Modular Refactoring and the Strangler Fig Pattern relate?**
A: Modular Refactoring prepares a large, tightly coupled codebase for migration by breaking it into modules; the Strangler Fig Pattern is then typically used to carry out the actual migration, module by module.
