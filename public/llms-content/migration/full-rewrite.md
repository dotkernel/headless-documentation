---
title: Full Rewrite or Big Bang Rewrite
description: Describes the Full Rewrite migration strategy, how it works, and its main advantages and disadvantages.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/migration/full-rewrite"
category: "Development"
language: "en"
---

# Full Rewrite or Big Bang Rewrite

## TL;DR

A full rewrite means completely rebuilding the system from scratch in the new architecture while the old application stays live, then cutting over to the new version once it's complete and tested. It offers a blank slate, optimal architecture, and better maintainability and security, but it's high risk (no partial rollback), takes a long time with no interim user value, is often as expensive as the original product, and risks feature drift if the old application keeps changing in the meantime.

## FAQ

**Q: What is a Full Rewrite migration strategy?**
A: Completely rebuilding the system from scratch in the new architecture or technology.

**Q: What is the biggest risk of a full rewrite?**
A: High risk — the release must work on the first try, with no partial rollback.

**Q: Why might a full rewrite be expensive?**
A: Building a second product in parallel can prove just as costly as the original product.
