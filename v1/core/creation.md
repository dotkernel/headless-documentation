# Creating a Core Submodule

## Summary

A step-by-step guide to turning the Core module into a Git submodule, including adding, committing, and initializing/updating it.

## Prerequisites

Before you begin, make sure you have:

- Git installed locally.
- An existing Core module in your application to convert (see the note below).
- Push access to a new, empty Git repository that will hold the extracted Core code.

## Instructions

The full steps for creating a submodule are described in [Git Tools – Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

> There is already a Core module in some of the Dotkernel applications, but it works like any other module (App, Page, or User).
> The Core modules are designed to be a starting point for the module’s transformation into a Git submodule.

First create a new Git repository that will contain the Core code.

> If the existing Core folder already has commit history you want to keep, extract it with a history-preserving tool such as `git subtree split` before pushing to the new repository.
> Simply creating an empty repository and adding it as a submodule does not carry over the folder's original history.

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

From now on, any changes to the Core submodule must be committed from within the Core folder, like for any other Git repository, using these commands (simplified version, provided as an example):

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

## FAQ

**Q: Where can I find the full steps for creating a Git submodule?**

A: In the official Git documentation, [Git Tools – Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

**Q: What command creates a submodule in an application?**

A: `git submodule add <url>`, using the URL of the new Core repository.

**Q: How do I get the submodule after cloning the project?**

A: Run `git submodule init` followed by `git submodule update`.

**Q: Should I keep the existing Core module after adding the submodule?**

A: No, delete the existing Core module before adding the submodule to other applications.

**Q: Will I lose the Core folder's Git history when I create the submodule?**

A: Yes, unless you extract it first with a history-preserving tool such as `git subtree split` — simply creating an empty repository and adding it as a submodule does not carry over the folder's original history.

## See also

- [Introduction](introduction.md)
- [Using the Core Submodule](usage.md)
