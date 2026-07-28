# Usage

## Summary

Explains how Dotkernel Queue fits alongside Dotkernel API and Dotkernel Admin, and when to add it to your platform.

## Details

Dotkernel Queue can be installed independently or alongside other applications in the Dotkernel suite, based on your business requirements. Like API and Admin, it is a separate codebase designed to complement the others — see the [Architecture Overview](../architecture.md) for how the three fit together.

Add Dotkernel Queue once you have work that shouldn't run inline with a request, such as sending bulk emails, generating reports, or processing uploads. Your API or Admin application dispatches a message, and Queue processes it asynchronously in the background, independent of the request/response cycle.

Because Queue is its own microservice, it can be deployed and scaled separately from API and Admin, and it can consume messages produced by either one.

## FAQ

**Q: Can Dotkernel Queue be used on its own?**
A: Yes, it can be installed independently, though it's most useful once another application (API or Admin) is producing messages for it to process.

**Q: When should I add Dotkernel Queue to my platform?**
A: Once you have work that shouldn't run inline with a request, such as sending bulk emails, generating reports, or processing uploads.

**Q: Can Dotkernel Queue be scaled independently of API and Admin?**
A: Yes, since it's a separate microservice, it can be deployed and scaled on its own.

## See also

- [Dotkernel API: Usage](../api/usage.md)
- [Dotkernel Admin: Usage](../admin/usage.md)
- [Architecture Overview](../architecture.md)
