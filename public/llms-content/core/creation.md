---
title: Creating a Core Submodule
description: A step-by-step guide to turning the Core module into a Git submodule, including adding, committing, and initializing/updating it.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/core/creation"
category: "Development"
language: "en"
---

# Creating a Core Submodule

## TL;DR

Before converting the existing Core module into a Git submodule, make sure you have Git installed, an existing Core module to convert, and push access to a new, empty repository — if that folder already has commit history worth keeping, extract it first with a tool like `git subtree split`, since a plain `git submodule add` on a fresh repository won't carry it over. Otherwise, create a new Git repository for the Core code, then run `git submodule add <url>` from the root of the main repository to generate the `.gitmodules` file mapping it to a local directory (e.g. `src/Core`). After that, commit changes to Core from within its own folder like any other Git repository, and use `git submodule init` and `git submodule update` after cloning the project — remembering to delete the existing Core module before adding the submodule elsewhere.

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
