![Project Stage][project-stage-shield]
![Maintenance][maintenance-shield]
[![License][license-shield]](https://github.com/expaso/hassos-addon-pgadmin4/blob/main/LICENSE)

# Home Assistant Add-on: [pgAdmin 4](https://www.pgadmin.org/)

<a href="https://www.buymeacoffee.com/expaso" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

## Introduction

pgAdmin is the most popular and feature rich Open Source administration and development platform for PostgreSQL, the most advanced Open Source database in the world.

This Add-on can be used to control any postgreSQL databases on your network, incuding those served the TimescaleDB add-on, which can also install from the same addon-repository.

## Configuation

Example add-on configuration:

```
 {
    "ssl": true,
    "certfile": "fullchain.pem",
    "keyfile": "privkey.pem",
    "system_packages": [],
    "init_commands": [],
    "leave_front_door_open": false
 }
```

### Option: `ssl`

Indicates if the add-on UI will be servd from port 80 or port 443 (using the provided certificates).

### Option: `certfile`

The filename of your SSL Certificate in the `ssl` folder.

### Option: `certfile`

The filename of your Private Key File in the `ssl` folder.

### Option: `system_packages`

Optional extra Alpine packages that will be installed during add-on startup.
**Beware**: Adding a lot of packages could lead to long startup time.

### Option: `init_commands`

Any extra commands that will be run during add-on startup.

### Option: `leave_front_door_open`

Serves the website without protection of home-assistant user authentication.

**CAUTION!!**

Setting this option is a potential security risk and should be avoided whenever possible.
If you don't know what you are doing, just leave it off.

## Support

- Got questions?
  [Open an issue here][issues]

- For a general repository issue or add-on ideas? [Open an issue here][repo-issues]

[issues]: https://github.com/expaso/hassos-addon-pgadmin4/issues
[repo-issues]: https://github.com/expaso/hassos-addons/issues



[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[release-shield]: https://img.shields.io/badge/version-v4.0.0-blue.svg
[release]: https://github.com/expaso/hassos-addon-pgadmin4/tree/v4.0.0
[license-shield]: https://img.shields.io/github/license/expaso/hassos-addon-pgAdmin4.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2024.svg