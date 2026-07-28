---
title: Strangler Fig Pattern or Incremental Migration
description: Describes the Strangler Fig (incremental) migration strategy, how it works, and its main advantages.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/migration/strangler-fig"
category: "Development"
language: "en"
---

# Strangler Fig Pattern or Incremental Migration

## TL;DR

The Strangler Fig Pattern gradually replaces parts of an old application with new components — wrapping the old app with a routing layer, building and testing features in the new architecture one at a time, rerouting traffic once each is ready, and decommissioning the old application only after everything has migrated. It's the recommended approach for complex legacy systems since it lowers risk, delivers continuous improvements, allows easy rollback, and supports better learning, as long as you can intercept and redirect requests through a routing layer.

## FAQ

**Q: What is the Strangler Fig Pattern?**
A: A migration strategy that gradually replaces parts of the old application with new components until the old one is no longer needed.

**Q: What must be in place for the Strangler Fig Pattern to work?**
A: The ability to intercept requests and redirect execution via a routing layer.

**Q: Why is this pattern recommended for complex legacy applications?**
A: It mitigates downtime and risk by handling small, manageable sections of code at a time.
