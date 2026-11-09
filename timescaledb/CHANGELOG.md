## ⚠️ Upgrading from 5.x

This is the first release in the add-on store since 5.4.2, so it also contains everything of [6.0.0](https://github.com/expaso/hassos-addon-timescaledb/releases/tag/v6.0.0). **Take a backup before updating.**

- Your databases are upgraded from PostgreSQL 17 to 18 automatically on the first start; this can take a while on large databases. Databases on PostgreSQL 15 or 16: install 5.x first.
- Only `aarch64` and `amd64` are supported, like Home Assistant itself. Stay on 5.x on `armhf`, `armv7` or `i386`.
- `postgresql_config` (which never worked) is replaced by `postgresql_settings`, a list of `name=value` entries.
- New option `postgres_password` for the password of the `postgres` user. New installations use `scram-sha-256`; existing ones keep `md5`.
- Backups are now compressed and can no longer fill the disk; restores use TimescaleDB's own restore steps (restores of older backups could silently lose TimescaleDB data).
- The add-on no longer stops PostgreSQL when pgAgent or a startup check fails.

## 🚀 Features in 6.1.0

- Add VectorChord (vchord) for Immich, behind the vectorchord option @expaso (#94)

Turn on the new `vectorchord` option to load VectorChord, then set up a database for [Immich](https://immich.app/) as described in the documentation.

## Changes in 6.0.0

- Release Drafter: breaking-change makes a major version @expaso (#89)
- Fix pg\_hba\_config writing literal "null" and orphaned rules on clear @danieldotnl (#82)

### 💥 Breaking Changes

- Replace postgresql\_config by postgresql\_settings, which works @expaso (#90)
- Version 6.0.0: PostgreSQL 18, TimescaleDB 2.31, stability fixes @expaso (#88)

### 🚀 Features

- scram-sha-256 for new installs, postgres\_password option @expaso (#92)
- Bump versions: timescaledb 2.26.0, postgis 3.6.2, timescaledb-toolkit 1.22 @nsteinmetz (#72)

### 🐛 Bug Fixes

- Rebuild backup and restore: compressed, disk-safe, TimescaleDB-correct @expaso (#91)
- Replace postgresql\_config by postgresql\_settings, which works @expaso (#90)
- Version 6.0.0: PostgreSQL 18, TimescaleDB 2.31, stability fixes @expaso (#88)
- Fix "No such file or directory" startup failure after HAOS backup restore @[copilot-swe-agent[bot]](https://github.com/apps/copilot-swe-agent) (#74)
- Fix pg\_hba\_config crash and duplicate entries on restart @[copilot-swe-agent[bot]](https://github.com/apps/copilot-swe-agent) (#77)
- Fix: chown/chmod backup file before restore to prevent postgres permission denied @[copilot-swe-agent[bot]](https://github.com/apps/copilot-swe-agent) (#75)

