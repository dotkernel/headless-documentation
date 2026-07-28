# Getting Started

## Summary

Explains the prerequisites and general installation flow for setting up a Dotkernel API, Admin, or Queue application, based on their official setup instructions.

## Details

Before installing any Dotkernel application, make sure you have:

- **PHP** – Dotkernel API and Admin require PHP 8.3, 8.4, or 8.5.
  Dotkernel Queue requires PHP 8.4 or 8.5.
- **Composer** – used to install and manage dependencies for every Dotkernel application.
- **A relational database** – API and Admin use Doctrine ORM, typically against a MariaDB or MySQL database (the `utf8mb4_general_ci` collation is recommended).
- **Git** – required if you plan to share code across applications via a [Core submodule](core/creation.md).

### Installing Dotkernel API or Admin

Both applications follow the same general installation pattern:

1. Clone the application's repository into an empty project directory and install its dependencies with Composer.
2. During installation, Composer may prompt you about registering additional ConfigProviders.
   Choose not to inject them — the application already includes the [ConfigProviders](config-provider/introduction.md) it needs.
3. Duplicate the distributed configuration files (for example the local and CORS configuration) into their local, non-versioned counterparts, and fill in your database connection parameters.
4. Run the database migrations, and the fixtures if provided, to seed initial data.
5. Enable development mode while you're building the application.

> Dotkernel Admin ships with a default admin account for first login.
> Change its credentials before deploying to production.

### Installing Dotkernel Queue

Dotkernel Queue is set up separately from API and Admin, since it centers on asynchronous message processing rather than a database-backed admin interface.
Refer to the official Dotkernel Queue documentation for its installation and message transport configuration steps.

## FAQ

**Q: What PHP version do I need?**
A: PHP 8.3, 8.4, or 8.5 for Dotkernel API and Admin; PHP 8.4 or 8.5 for Dotkernel Queue.

**Q: What database does Dotkernel use?**
A: API and Admin use Doctrine ORM, typically against a MariaDB or MySQL database.

**Q: Why am I prompted about ConfigProviders during installation?**
A: Composer may ask whether to inject additional ConfigProviders — decline, since the application's required ConfigProviders are already included.

**Q: Do I need to configure anything before running the application for the first time?**
A: Yes — duplicate the distributed local configuration files, fill in your database connection details, run migrations (and fixtures, if provided), and change any default credentials before production use.
