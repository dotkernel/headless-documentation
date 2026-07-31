# Benefits of the Core Submodule

## Summary

Lists the benefits the Core submodule pattern provides as your platform grows, such as scalability and easier onboarding.

## Details

This design pattern ensures:

- Design flexibility.
- Scalability based on future requirements.
- Consistent, enterprise-level growth, while also being suited for smaller applications.
- The ability to split the work to multiple developers.
- Easier bugfixes and onboarding.

As your platform expands, each new application connects to the Dotkernel Headless Platform via the central API which services everything the other applications require.
This ensures consistency throughout your platform, while allowing any number of outside connections as requirements arise.

## FAQ

**Q: How does the Core submodule pattern help as a platform grows?**

A: It provides design flexibility and scalability suited for both enterprise and smaller applications.

**Q: Can multiple developers work on the platform using this pattern?**

A: Yes, it allows splitting the work across multiple developers.

**Q: How do new applications connect to the platform?**

A: Each new application connects via the central API, which services everything the other applications require.

## See also

- [Introduction](introduction.md)
- [Using the Core Submodule](usage.md)
