# Samizdat-Plugin-Database

MySQL/MariaDB database hosting management for Samizdat. An **offerable** Samizdat module (hostable for customers). Extracted
from the Samizdat monorepo with history; installs as a standalone CPAN/pkg
distribution.

## Layout

    lib/Samizdat/Plugin/Database.pm        routes + the `database` helper
    lib/Samizdat/Controller/Database.pm    request handlers
    lib/Samizdat/Model/Database.pm         business logic / data access
    lib/Samizdat/resources/templates/database/   views (install to site_perl)
    lib/Samizdat/resources/locale/database/      per-module translations

Resources install under `site_perl/Samizdat/resources/...`, where the core
resolver (`$app->resource(...)`) finds them.

## Dependencies

- **Samizdat** (core) — provides `Samizdat::Model::Cache`, `pg`/`mysql`, and the
  resource resolver. Not yet on CPAN; install the core dist or put it on `PERL5LIB`.
- Mojolicious.

## Install

    perl Makefile.PL
    make && make test          # core (Samizdat) must be on PERL5LIB
    make install               # or: make install INSTALL_BASE=/path/to/prefix

Enable it in `samizdat.yml` via `extraplugins: [Database]`.
