# Usage

## Summary

Explains how Dotkernel Admin fits alongside Dotkernel API and Dotkernel Queue, and how you can start with Admin alone and add the other components later.

## Details

Dotkernel Admin can be installed independently or together with other applications in the Dotkernel suite, based on your business requirements.
These components are designed to complement each other (out-of-box they are separate codebases):

- **Dotkernel API** exposes the content to 3rd-party frontends or backends.
- **Dotkernel Admin** (optional) manages the data (create, edit, delete).
- **Dotkernel Queue** (optional) queue management microservice.

You can start with Dotkernel Admin and integrate it into your existing platform.
The Admin has built-in reports and graphs that can be configured and customized based on your needs.

Later on you can add:

- Dotkernel API to handle all data manipulation.
- Dotkernel Queue for its asynchronous task processing.

## FAQ

**Q: Can Dotkernel Admin be used on its own?**
A: Yes, it can be installed independently and integrated into your existing platform.

**Q: Are Dotkernel Admin, API, and Queue part of the same codebase?**
A: No, out of the box they are separate codebases designed to complement each other.

**Q: What do Dotkernel API and Dotkernel Queue add to Admin?**
A: The API handles data manipulation for the platform, and Queue handles asynchronous task processing.
