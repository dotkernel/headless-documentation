# Usage

## Summary

Explains how Dotkernel API fits alongside Dotkernel Admin and Dotkernel Queue, and how to start with API alone and add the other components later.

## Details

Dotkernel API can be installed independently or together with other applications in the Dotkernel suite, based on your business requirements.
These components are designed to complement each other (out-of-box they are separate codebases):

- **Dotkernel API** exposes the content to 3rd-party frontends or backends.
- **Dotkernel Admin** (optional) manages the data (create, edit, delete).
- **Dotkernel Queue** (optional) queue management microservice.

A safe bet is to start with Dotkernel API and integrate it into your existing platform.
The API can manage the access permissions to keep your data secure:

- Admin-level users create and edit the data for your existing backend.
- Regular users read the data for your frontend.

Later on you can add:

- Dotkernel Admin for its simple table-based approach, its reports and graphs.
- Dotkernel Queue for its asynchronous task processing.

## FAQ

**Q: Should I start with Dotkernel API or Admin?**
A: Starting with Dotkernel API is a safe bet since it can manage access permissions to keep your data secure.

**Q: How does Dotkernel API separate admin and regular users?**
A: Admin-level users create and edit the data, while regular users read the data for your frontend.

**Q: What can I add to Dotkernel API later?**
A: Dotkernel Admin for its table-based management, reports and graphs, and Dotkernel Queue for asynchronous task processing.
