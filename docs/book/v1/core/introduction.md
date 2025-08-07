# Introduction

The Core submodule is a common codebase set up to be used by the Dotkernel applications you added to your project.
The project setup may differ - e.g. two APIs, one Admin, 3 Frontends - but the Core submodule can be included in all of them.

By having a common module in your Dotkernel applications, you ensure that each of them uses entities and services in the same way.
It helps to make service updates easier to sync in all the application in your platform.

General rules:

- The golden rule for the Core codebase is that it is the only place which manages the database entities.
- As much as possible, all Doctrine entities must reside in Core.
- The current location of the Core submodule is `src/Core`.
