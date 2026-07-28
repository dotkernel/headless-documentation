---
title: Usage
description: Explains how Dotkernel Queue fits alongside Dotkernel API and Dotkernel Admin, and when to add it to your platform.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/queue/usage"
category: "Development"
language: "en"
---

# Usage

## TL;DR

Dotkernel Queue can be installed independently or alongside API and Admin, as its own codebase — add it once you have work that shouldn't run inline with a request, such as sending bulk emails, generating reports, or processing uploads. Your API or Admin application dispatches a message and Queue processes it asynchronously in the background, and because it's a separate microservice, it can be deployed and scaled independently of the other two.

## FAQ

**Q: Can Dotkernel Queue be used on its own?**
A: Yes, it can be installed independently, though it's most useful once another application (API or Admin) is producing messages for it to process.

**Q: When should I add Dotkernel Queue to my platform?**
A: Once you have work that shouldn't run inline with a request, such as sending bulk emails, generating reports, or processing uploads.

**Q: Can Dotkernel Queue be scaled independently of API and Admin?**
A: Yes, since it's a separate microservice, it can be deployed and scaled on its own.
