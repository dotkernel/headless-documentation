---
title: Getting Started
description: Explains the prerequisites and general installation flow for setting up a Dotkernel API, Admin, or Queue application, based on their official setup instructions.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/getting-started"
category: "Development"
language: "en"
---

# Getting Started

## TL;DR

Before installing any Dotkernel application, make sure you have PHP (8.3–8.5 for API and Admin, 8.4–8.5 for Queue), Composer, a MariaDB/MySQL database for Doctrine ORM, and Git if you'll use a Core submodule. API and Admin install the same way — clone, `composer install`, decline extra ConfigProvider injection, duplicate the local config files, run migrations/fixtures, and change the default credentials before production — while Queue is installed separately per its own documentation.

## FAQ

**Q: What PHP version do I need?**
A: PHP 8.3, 8.4, or 8.5 for Dotkernel API and Admin; PHP 8.4 or 8.5 for Dotkernel Queue.

**Q: What database does Dotkernel use?**
A: API and Admin use Doctrine ORM, typically against a MariaDB or MySQL database.

**Q: Why am I prompted about ConfigProviders during installation?**
A: Composer may ask whether to inject additional ConfigProviders — decline, since the application's required ConfigProviders are already included.

**Q: Do I need to configure anything before running the application for the first time?**
A: Yes — duplicate the distributed local configuration files, fill in your database connection details, run migrations (and fixtures, if provided), and change any default credentials before production use.
