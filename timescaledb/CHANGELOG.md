# 4.0.1

Finally its here! What you all have been waiting for: The TimescaleDB Toolkit Release! 🥳

⚠️ This release is packed with new stuff and improvements, but also some caveats! Please read these release notes carefully before installing! ⚠️

It has been a long time coming, but I am finally able to release the TimescaleDB Toolkit for all supported architectures. This release includes the latest version of TimescaleDB, PostgreSQL and Postgis.

## 🚀 Features

- Finally! 🎉 TimescaleDB_Toolkit 1.18.0 (only for amd64/aarch64/arm64 systems, but that would cover most of you). See: https://github.com/timescale/timescaledb-toolkit?tab=readme-ov-file
- Support for all architechtures (amd64, aarch64, armv7, armhf, i386).
- Support for running this addon as a standalone docker container outside of Home Assistant! Please consult the readme for more information. This makes is possible to run this addon on any system that supports docker, and way easier to migrate from a raspberry pi to a more powerful system.
- Mapped the `/media` folder into the addon, so that __could__ be used to store database or backups, just like the __share__ foilder.

## ⬆️ Maintenance
- PostgreSQL: 16.2 --> https://www.postgresql.org/docs/release/16.2/
- TimescaleDB: 2.14.2 --> https://docs.timescale.com/about/latest/release-notes/#timescaledb-2142-on-2024-02-20
- Postgis: 3.4.2 --> https://postgis.net/docs/release_notes.html
- Base Image: 15.0.7

## Notes before upgrading

As you are already accustomed to, this release will auto-upgrade your current PostgreSQL 15 installation to PostgreSQL 16.2. This is a major upgrade and you should be aware of the following:

- **PostgreSQL 16.2** is a major version upgrade. This means that you will not be able to downgrade to PostgreSQL 15 without a backup.
- **TimescaleDb Extras** Please reinstall TimescaleDb-extras after the upgrade, should you have it installed: https://github.com/timescale/timescaledb-extras 
- **TimescaleDb** From Timescale 2.7 onwards, TimescaleDb has a new form of continuous aggregates. If you have continuous aggregates in your database, you should read the following documentation: https://docs.timescale.com/use-timescale/latest/continuous-aggregates/migrate/

### TLDR;

Use the following query to see if you have continuous aggregates in your database:

```sql 
select * from timescaledb_information.continuous_aggregates
```

Look at the last column 'Finalized'. If it says **False**, you could migrate the continuous aggregates after upgrading the addon using:

```sql 
CALL cagg_migrate('<name of aggregate>', true, true); 
```

The query output will hint you that you need to refresh the aggregate using the query specified in the message.

## Overthinking

This release was a real pain in the %#@ to get out.
To compile all this stuff in for different architechtures proved to be full of pitfalls and weirdness.

I have had many compiler crashes, demolished WSL2, triggered bugs in qemu, docker, Alpine, even in docker-hub which I had to wait for.
I even had to rewrite all buildscripts to precompile a lot of stuff upfront, otherwise the github build-agents would just give up on me!

But I am happy it finally worked out. I hope you all enjoy this release as much as I did making it (most of the time ;)
Thank you for all your support and your patience. I hope you all have a great time with this release!

I would love to hear your feedback, so please let me know what you think on Github (https://github.com/expaso/hassos-addon-timescaledb), Discord (https://discord.gg/ceAynsJd), The HA Community (https://community.home-assistant.io/t/home-assistant-add-on-postgresql-timescaledb/) or just buy me a coffee:

<a href="https://www.buymeacoffee.com/expaso" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

Thank you all!


# 3.0.2

## 🚀 Features

- Fixed issue whereby pgAgent jobs were hanging in status Running @Expaso (#39)

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

May you find any issues during install and/or upgrade, please open an issue on Github: https://github.com/expaso/hassos-addon-timescaledb/issues

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
