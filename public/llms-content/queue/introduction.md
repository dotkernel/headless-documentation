---
title: Introduction
description: An overview of Dotkernel Queue, a Mezzio-based microservice for processing asynchronous tasks via message queues.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/queue/introduction"
category: "Development"
language: "en"
---

# Introduction

## TL;DR

Dotkernel Queue is a standalone microservice, separate from your API or Admin application, built on the Mezzio microframework and using Laminas Messenger to dispatch and handle messages. It lets you offload slow or non-critical work — such as sending emails, generating exports, or processing uploads — outside the request/response cycle, following the same PSR-Compliant Middleware Stack (PSR-7, PSR-15) as other Dotkernel applications.

## FAQ

**Q: What is Dotkernel Queue?**
A: A standalone microservice for processing asynchronous tasks, separate from your API or Admin application.

**Q: What is Dotkernel Queue built on?**
A: The Mezzio microframework, using Laminas Messenger to dispatch and handle messages.

**Q: Why would I use Dotkernel Queue?**
A: To offload slow or non-critical work, such as sending emails, generating exports, or processing uploads, so it doesn't block the request/response cycle.
