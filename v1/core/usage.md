# Using the Core Submodule

## Summary

Explains how multiple applications share the Core submodule, what kinds of entities live in each application versus Core, and when to add new shared code to Core.

## Details

Once the shared Core submodule is separated and imported into each application, your platform can look like the example below:

- API + Core
- Admin + Core
- Queue + Core

![Diagram of API, Admin, and Queue applications each paired with the shared Core submodule](https://docs.dotkernel.org/img/headless-platform/core-queue2.png)

> Each box in the image is a different Git repository.

Whenever work begins on a new feature or update, the devs should normally have the most recent Core in their development environment.
In our example we have four code bases which will be kept in four separate repositories.

The Dotkernel applications include various entities to get you started quickly.
This is not a complete list, but it should help you understand what each application is aimed toward, for example:

- **Admin** has admins, admin logins, and settings entities.
- **API** has both users and admins, as well as authentication entities.

There are already shared entities which are identical, so the best place for them is within the Core submodule.
Whenever you create new shared code, you should add it in the Core submodule and make sure to keep it updated in all your applications.

> This does not mean that all new code should be in Core, as there are plenty of instances when certain functionality is designed to be used by only one application.

## FAQ

**Q: What does a platform using the Core submodule look like?**

A: Each application (API, Admin, Queue) pairs with Core, with each box being a separate Git repository.

**Q: Should all new code go into Core?**

A: No, only shared code should go into Core — functionality used by only one application can stay in that application.

**Q: What kinds of entities are already split between applications?**

A: For example, Admin has admins, admin logins, and settings entities, while API has users, admins, and authentication entities.

## See also

- [Introduction](introduction.md)
- [Benefits of the Core Submodule](benefits.md)
- [Architecture Overview](../architecture.md)
