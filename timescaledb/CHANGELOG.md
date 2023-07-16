# 3.0.1

## 🚀 Features

- Fixed an issue whereby the upgrade would fail when the scripts from TimescaleDb-extras are installed. @Expaso (#37)
⚠️ Please reinstall TimescaleDb-extras after the upgrade should you need them. ⚠️

## 🐛 Bug Fixes

- Fixed an issue with pgAgent not updating job status @Expaso (#38)

# 3.0.1

## 🚀 Features

- Fixed an issue whereby the upgrade would fail when the scripts from TimescaleDb-extras are installed. @Expaso (#37)
⚠️ Please reinstall TimescaleDb-extras after the upgrade should you need them. ⚠️

## 🐛 Bug Fixes

- Fixed an issue with pgAgent not updating job status @Expaso (#38)

# 3.0.0

It has been a while, but this release had many many important changes under the hood!

Maintenance:
- ⬆️ Upgraded Postgresql to 15.3 🥳
- ⬆️ Upgraded TimescaleDb to 2.11.1
- ⬆️ Upgraded Postgis to 3.3.3
- ⬆️ Upgraded Base Images to 14.0.2
- ⬆️ Upgraded all S6 container scripts to the new coding style
- ⬆️ Moved all config files from json to yaml
- 🙋🏻‍♂️ Deprecated i386 and armhf architectures

Features:
- 🚀 Paved the way for Timescaledb-Toolkit integration
- 🚀 Postgresql 14 to Postgresql 15 auto upgrade
- 🚀 Increased max-connections default to 50
- 🚀 Added dependencies for Postgis-raster to fuction
- 🚀 Implemented Codenotary CAS to enable addon-signing for a higher security rating

Fixes:
- 🐛 Fixed an issue whereby pgAgent jobs did not run due to noexec mount of /tmp. Moved the workingfolder of pgAgent to /data/tmp/pgagent

# 2.1.1

- 🐞Added missing packages llvm12. Closes #27

# 2.1.0

- ⬆️Upgraded Base Image to 12.2.6
- ⬆️Upgraded PostgreSql to 14.5
- ⬆️Upgraded Timescale to 2.8.1
- 🎉Feat: add the stats_temp_directory option and enable tmpfs @snowyu (#24)
- 🎉Adds postgresql contrib for standard functions @jhogendorn (#25)
- Implemented better checks around various installed extensions, so the upgrade is more intelligent about what extensions should be updated during startup.
- Minor bugs and fixes for resilliency.


# 2.0.1

- Fixed an issue with PostgreSql 12 to 14 conversion, whereby conversion could fail when the database was being accessed during the upgrade process.

# 2.0.0
 
!! READ CAREFULLY - Breaking changes !!

Upgraded PostgreSQL to 14.2 🎉
Upgraded TimescaleDb to 2.6.0 🥳
Upgraded Postgis to 3.2.1 👍🏻
Upgraded pgAgent to 4.2.2
Upgraded base images to 11.1.1
It took a while before this release came out. Covid came (and went!), but more importantly: Timescale 2.0 came out, just as PostgreSql 13 and 14.
I know that a lot of you guys (and girls) were waiting for support of Timescale 2+, but I had to be very careful not to break your existing setups.

The goals was to bring a seamless upgrade experience for both Timescale, Postgis, as well as Postgresql itself.
To perform these upgrades all together was not trivial, but, it's here!!

Please read the link below carefully to thoroughly understand the new breaking changes in TimescaleDb.

(see: https://docs.timescale.com/timescaledb/latest/overview/release-notes/changes-in-timescaledb-2/)

May you find any issues during install and/or upgrade, please open an issue on Github: https://github.com/Expaso/hassos-addon-timescaledb/issues

Thanks for all your support!

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
