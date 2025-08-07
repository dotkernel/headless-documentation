# Using the Core Submodule

Once the shared Core submodule is separated and imported into each application, your platform can look like in the example below:

- API + Core
- Admin + Core
- Queue + Core

![Headless Platform with Core Submodule](https://docs.dotkernel.org/img/headless-platform/core-queue2.png)

> Each box in the image is a different Git repository.

Whenever work begins on a new feature or update, the devs should normally have the most recent Core in their development environment.
In our example we have four code bases which will be kept in four separate repositories.

The Dotkernel applications include various entities to get you started quickly.
This is not a complete list, but it should help you understand what each application is aimed toward, for example:

- The admin has admins, admin logins and settings entities.
- The api has both users and admins, as well as authentication entities.

There are already shared entities which are identical, so the best place for them is within the Core submodule.
Whenever you create new shared code, you should add it in the Core submodule and make sure to keep it updated in all your applications.

> This does not mean that all new code should be in Core, as there are plenty of instances when certain functionality is designed to only be used by only one application.
