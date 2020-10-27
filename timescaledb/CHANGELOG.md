# 1.1.6

- Added armhf architechture
- Added max_connection configuration-option to set the maximum number of connection PostgreSql will accept.

# 1.1.5

- Added armv7 support: Closes #7 Add armv7 compatibility. Thanks to @berga (#8)

# 1.1.4

- Upgraded Postgres to 12.4 (see: https://www.postgresql.org/docs/12/release-12-4.html)
- Upgraded TimescaleDb to 1.7.4 (see: https://github.com/timescale/timescaledb/releases/tag/1.7.4)
- Added possibility to use system_packages:[str] and init_commands:[str] in your config, to further customize the container during startup.

# 1.1.3

- Upgraded TimeScaleDb to 1.7.2 (see: https://github.com/timescale/timescaledb/releases/tag/1.7.2).
- Fix problem whereby permissions on data-directory are wrong after snapshot restore.

# 1.1.2

- Prevent add-on exit when pgAgent-extension cannot be installed correctly.

# 1.1.1

- Support for more versions of TimecaleDb. This is needed when upgrading existing installations.

# 1.1.0

- Upgraded TimeScaleDb to 1.7.1 due to critical issues in 1.7.0 (see: https://github.com/timescale/timescaledb/releases/tag/1.7.1)
- Added pgAdmin extension

# 1.0.3

- Fixed error during CREATE EXTENSION IF NOT EXISTS postgis CASCADE

# 1.0.2

- Fixed error during add-on startup on Rpi3 and Rpi4

# 1.0.1

- Temporary version without TimeScaleDB Tuning

# 1.0.0

- Initial release
