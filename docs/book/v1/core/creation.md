# Creating a Core Submodule

The full steps for creating a submodule are described in [Git Tools – Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

> There is already a Core module in some of the Dotkernel applications, but it works like any other module (App, Page, or User).
> The Core modules are designed to be a starting point for the module’s transformation into a Git submodule.

First create a new Git repository that will contain the Core code.
To create the submodule in an application, you need to have Git create the `.gitmodules` file in the root of the main repository by running the command below.
Use the url from the new repository you just created instead of `<url>`:

```shell
git submodule add <url>
```

> You can have multiple submodules, but for this tutorial we will only create the Core submodule.

The `.gitmodules` file maps the submodules and its corresponding local directory within the main project (e.g. `src/Core`).
This allows Git to manage the submodule correctly, from cloning, to updating, to tracking its changes.

> None of the Dotkernel applications have the .gitmodules file out of the box.
> Only after isolating the Core into a Git submodule and pushing it to a separate Git repository does it become available to be included into any Dotkernel application.

From now on, any changes to the Core submodule must be commited from within the Core folder, like for any other Git repository, using these commands (simplified version, provided as an example):

```shell
cd <path/to/submodule>
git add .
git commit -m "comment"
git push
```

Whenever you clone the project, you simply need to `init` and `update` the submodule with these commands:

```shell
git submodule init
git submodule update
```

> Do not forget to delete the existing Core module before adding the submodule to other applications.
