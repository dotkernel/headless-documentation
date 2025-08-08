# Full Rewrite or Big Bang Rewrite

A full rewrite is a software migration strategy that implies completely rebuilding the system from scratch in the new architecture or technology.

## How It Works

- You keep the old application in use, as-is.
- In parallel, you work with the development team to build a new version of the application in the target environment.
- Once the new application is complete and tested, you redirect all execution to the new application.
- You decommission the old application.

## Pluses

There are several advantages to this approach:

- Blank slate – No technical debt is carried over to the new application.
- Optimal architecture – You can code the new application without worrying about legacy code or outdated design patterns.
- Better maintainability and security – The new code can follow modern best practices which may be incompatible with the old code.

## Minuses

The disadvantages often weigh heavy against choosing this approach:

- High risk – Your release must work on the first try, there’s no partial rollback.
- Long timeline – There is no immediate user value during development.
- Expensive – Building a second product in parallel may prove to be just as costly as the original product.
- Feature drift – Since the old application is still running, any updates performed on it may cause further delay on the development of the new one and greater mismatching of business logic.

## Conclusion

Performing a full rewrite is no easy choice.
More often than not, the costs are the main reason you would not choose this migration strategy.
You may find yourself delaying its implementation until you are forced to do so by circumstance.
