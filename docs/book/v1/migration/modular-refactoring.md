# Modular Refactoring

The Modular Refactoring is a migration strategy where you break a large, tightly coupled codebase into smaller, independent modules.
Once the modules are defined, you begin the migration to the new architecture.

## How It Works

- Identify logical boundaries in the business logic.
Search for sections of code that can function independently.
- Decouple dependencies.
Refactor code to reduce direct cross-module calls, often introducing interfaces or APIs for communication.
- Isolate each module.
Ensure each module can be built, tested, and deployed separately.
- Migrate module-by-module.
Move one module at a time to the new architecture, integrate it back into the system, and test its functionality before moving on.

## Pluses

- Controlled scope – Each migration step is focused on one module.
- Improved maintainability – As the migration progresses, the system becomes cleaner and more modular.
- Enables parallel work – You can assign different development teams to migrate different modules at the same time.
- Lower risk – If a migration fails, only one part of the system is affected.

## Minuses

- Refactoring cost – Breaking a monolith into modules takes time and effort.
- Possible temporary slowdown – You may need to allocate resources from new feature development to the refactoring effort.
- Requires strong design discipline – You need to carefully plan modules to avoid repeated rework.

## Conclusion

Modular Refactoring implies a great deal of preparation (proportional to the complexity of the application) before the migration takes place.
You take e.g. the existing monolith and reorganize it into clearly defined modules, while in the same repository.
You can the extract the modules into new repositories or move them into microservices, and create interfaces between the old and the new code.
For the actual code migration, you can opt for the Strangler Fig Pattern. 
