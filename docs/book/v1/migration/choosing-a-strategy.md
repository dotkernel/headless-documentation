# Choosing a Migration Strategy

## Summary

A decision guide comparing the Full Rewrite, Modular Refactoring, and Strangler Fig migration strategies, to help you pick the right one for your situation.

## Details

Each [migration strategy](introduction.md) documented in this section trades off risk, timeline, and cost differently:

|                 | [Full Rewrite](full-rewrite.md)                                                    | [Modular Refactoring](modular-refactoring.md)                                | [Strangler Fig](strangler-fig.md)                                      |
|-----------------|------------------------------------------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------|
| Risk            | High — no partial rollback                                                         | Moderate — contained to one module at a time once modularized                | Low — each change is small and reversible                              |
| Timeline        | Long, with no value delivered until launch                                         | Long upfront preparation, then incremental                                   | Incremental, with continuous delivery                                  |
| Team size       | Can be smaller, but works in isolation from the live system                        | Can scale across teams once modules are defined                              | Can be smaller, since work is isolated by feature                      |
| Best suited for | Small or simple systems, or codebases too tightly coupled to migrate incrementally | Large, tightly coupled monoliths that need to be decomposed before migrating | Complex, business-critical legacy systems that can't tolerate downtime |

As a general rule:

- If the system is small enough, or too tightly coupled to touch incrementally, a **Full Rewrite** may be the only practical option, despite its cost and risk.
- If the system is large but not yet split into independent parts, start with **Modular Refactoring** to establish clear module boundaries.
- Once boundaries exist (either because the system already has them, or because you just created them through Modular Refactoring), use the **Strangler Fig Pattern** to migrate module by module with low risk and continuous delivery.

In practice, Modular Refactoring and the Strangler Fig Pattern are often used together: refactor the monolith into modules first, then strangle each module into the new architecture one at a time.

## FAQ

**Q: Which migration strategy has the lowest risk?**

A: The Strangler Fig Pattern, since each change is small, reversible, and easy to test in isolation.

**Q: When does a Full Rewrite make sense?**

A: Mainly for small or simple systems, or when the existing codebase is too tightly coupled for an incremental migration to be practical.

**Q: How do Modular Refactoring and the Strangler Fig Pattern relate?**

A: Modular Refactoring prepares a large, tightly coupled codebase for migration by breaking it into modules; the Strangler Fig Pattern is then typically used to carry out the actual migration, module by module.
