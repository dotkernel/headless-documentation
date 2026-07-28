---
title: Introduction
description: Introduces the ConfigProvider class, what it returns, and how it's used across Dotkernel applications and packages, with a code example.
author: "admin"
date_published: "2026-07-27"
canonical_url: "https://docs.dotkernel.org/development/config-provider/introduction"
category: "Development"
language: "en"
---

# Introduction

## TL;DR

A `ConfigProvider` is a PHP class used during an application's bootstrap process that returns an array of configuration — in Dotkernel, typically dependency injection mappings, request handlers, and template file paths. Every Dotkernel application and package (API, Admin, Frontend, Light, Packages) ships with its own `ConfigProvider`, following an approach similar to Laminas/Mezzio.

## FAQ

**Q: What does a ConfigProvider return in Dotkernel?**
A: Dependency injection mappings, request handlers, and template file paths.

**Q: Which Dotkernel applications use ConfigProviders?**
A: Dotkernel API, Admin, Frontend, Light, and Packages all use ConfigProviders.

**Q: Is the Dotkernel ConfigProvider approach specific to Dotkernel?**
A: No, it follows an approach similar to Laminas/Mezzio.
