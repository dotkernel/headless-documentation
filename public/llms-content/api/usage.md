---
title: Usage
description: Explains how Dotkernel API fits alongside Dotkernel Admin and Dotkernel Queue, and how to start with API alone and add the other components later.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/api/usage"
category: "Development"
language: "en"
---

# Usage

## TL;DR

Dotkernel API can be installed on its own and integrated into an existing platform, or combined with Dotkernel Admin and Dotkernel Queue — each is a separate codebase designed to complement the others. Starting with API alone is a safe bet since it can manage access permissions (admin-level users create and edit data, regular users only read it); you can later add Admin for its table-based management, reports, and graphs, and Queue for asynchronous task processing.

## FAQ

**Q: Should I start with Dotkernel API or Admin?**
A: Starting with Dotkernel API is a safe bet since it can manage access permissions to keep your data secure.

**Q: How does Dotkernel API separate admin and regular users?**
A: Admin-level users create and edit the data, while regular users read the data for your frontend.

**Q: What can I add to Dotkernel API later?**
A: Dotkernel Admin for its table-based management, reports and graphs, and Dotkernel Queue for asynchronous task processing.
