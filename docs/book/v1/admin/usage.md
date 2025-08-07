# Usage

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
