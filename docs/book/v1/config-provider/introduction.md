# Introduction

## Summary

Introduces the `ConfigProvider` class, what it returns, and how it's used across Dotkernel applications and packages, with a code example.

## Details

In PHP, the `ConfigProvider` is a class that is part of an application's bootstrap process.
It returns an array of configuration, settings, or anything else your application needs.
In Dotkernel, each application module and package contains a `ConfigProvider` that normally returns:

- Dependency injection mappings.
- Request Handlers.
- Template file paths.

Here is an example in Dotkernel, which is an approach similar to Laminas/Mezzio:

```php
class ConfigProvider
{
    public function __invoke(): array
    {
        return [
            'dependencies' => $this->getDependencies(),
            'templates'    => $this->getTemplates(),
        ];
    }

    public function getDependencies(): array
    {
        return [
            'factories'  => [
                Handler\HomepageHandler::class => Handler\HomepageHandlerFactory::class,
                Handler\SearchHandler::class   => Handler\SearchHandlerFactory::class,
            ],
            'invokables' => [
                Console\GenerateSearchData::class => Console\GenerateSearchData::class,
           ],
        ];
    }

    public function getTemplates(): array
    {
        return [
            'app'   => [__DIR__ . '/../templates/app'],
            'error' => [__DIR__ . '/../templates/error'],
        ];
    }
}
```

All Dotkernel applications and packages use ConfigProviders:

- [Dotkernel API](https://docs.dotkernel.org/api-documentation/)
- [Dotkernel Admin](https://docs.dotkernel.org/admin-documentation/)
- [Dotkernel Frontend](https://docs.dotkernel.org/frontend-documentation/)
- [Dotkernel Light](https://docs.dotkernel.org/light-documentation/)
- [Dotkernel Packages](https://docs.dotkernel.org/packages/)

## FAQ

**Q: What does a ConfigProvider return in Dotkernel?**

A: Dependency injection mappings, request handlers, and template file paths.

**Q: Which Dotkernel applications use ConfigProviders?**

A: Dotkernel API, Admin, Frontend, Light, and Packages all use ConfigProviders.

**Q: Is the Dotkernel ConfigProvider approach specific to Dotkernel?**

A: No, it follows an approach similar to Laminas/Mezzio.

## See also

- [How the ConfigProvider works](functionality.md)
- [Benefits](benefits.md)
- [Glossary](../glossary.md)
