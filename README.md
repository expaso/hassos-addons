# Expaso Home Assistant Add-ons

![Project Stage][project-stage-shield]
![Maintenance][maintenance-shield]
[![License][license-shield]](LICENSE)

<a href="https://www.buymeacoffee.com/expaso" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>
## About

Welcome to my repository of Home-Assistant Addons!

## Installation

[![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fexpaso%2Fhassos-addons)

Or in the Home-Assistant add-on store, a possibility to add a repository is provided.
Use the following URL to add this repository:

```txt
https://github.com/expaso/hassos-addons
```

## Add-ons provided by this repository

### &#10003; [TimescaleDB][addon-timescaledb]

![Latest Version][timescaledb-version-shield]
![Supports armhf Architecture][timescaledb-armhf-shield]
![Supports armv7 Architecture][timescaledb-armv7-shield]
![Supports aarch64 Architecture][timescaledb-aarch64-shield]
![Supports amd64 Architecture][timescaledb-amd64-shield]
![Supports i386 Architecture][timescaledb-i386-shield]

An open-source database built on PostgreSQL for analyzing time-series data with the power and convenience of SQL

[:books: TimescaleDB add-on documentation][addon-doc-timescaledb]

### &#10003; [pgAdmin4][addon-pgadmin4]

![Latest Version][pgadmin4-version-shield]
![Supports armhf Architecture][pgadmin4-armhf-shield]
![Supports armv7 Architecture][pgadmin4-armv7-shield]
![Supports aarch64 Architecture][pgadmin4-aarch64-shield]
![Supports amd64 Architecture][pgadmin4-amd64-shield]
![Supports i386 Architecture][pgadmin4-i386-shield]

A PostgreSQL Management and Query tool

[:books: pgAdmin4 add-on documentation][addon-doc-pgadmin4]

## Releases

Releases are based on [Semantic Versioning][semver], and use the format
of ``MAJOR.MINOR.PATCH``. In a nutshell, the version will be incremented
based on the following:

- ``MAJOR``: Incompatible or major changes.
- ``MINOR``: Backwards-compatible new features and enhancements.
- ``PATCH``: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

Open an issue here on GitHub. Note, we use a separate
GitHub repository for each add-on. Please ensure you are creating the issue
on the correct GitHub repository matching the add-on.

- [Open an issue for the add-on: TimescaleDB][timescaledb-issue]
- [Open an issue for the add-on: pgAdmin4][pgadmin4-issue]

For a general repository issue or add-on ideas [open an issue here][issue]

[addon-timescaledb]: https://github.com/expaso/hassos-addon-timescaledb/tree/v4.2.0
[addon-doc-timescaledb]: https://github.com/expaso/hassos-addon-timescaledb/blob/v4.2.0/README.md
[timescaledb-issue]: https://github.com/expaso/hassos-addon-timescaledb/issues
[timescaledb-version-shield]: https://img.shields.io/badge/version-v4.2.0-blue.svg
[timescaledb-aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[timescaledb-amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[timescaledb-armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[timescaledb-armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[timescaledb-i386-shield]: https://img.shields.io/badge/i386-yes-green.svg
[addon-pgadmin4]: https://github.com/expaso/hassos-addon-pgadmin4/tree/v3.2.0
[addon-doc-pgadmin4]: https://github.com/expaso/hassos-addon-pgadmin4/blob/v3.2.0/README.md
[pgadmin4-issue]: https://github.com/expaso/hassos-addon-pgadmin4/issues
[pgadmin4-version-shield]: https://img.shields.io/badge/version-v3.2.0-blue.svg
[pgadmin4-aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[pgadmin4-amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[pgadmin4-armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[pgadmin4-armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[pgadmin4-i386-shield]: https://img.shields.io/badge/i386-yes-green.svg
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production-green.svg
[gitlabci-shield]: https://gitlab.com/expaso/hassos-addons/badges/master/pipeline.svg
[license-shield]: https://img.shields.io/github/license/expaso/hassos-addons.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2024.svg