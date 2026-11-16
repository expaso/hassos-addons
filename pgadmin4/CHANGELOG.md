## Breaking change

32-bit architectures (armv7 and i386) are no longer supported. This release requires aarch64 or amd64.

## Changes

- Upgrade pgAdmin to 9.19 and the Home Assistant base image to 21.0.11.
- Add PostgreSQL 18 client utilities and retain PostgreSQL 12-17 client utilities.
- Update the add-on startup and nginx integration for the current Home Assistant base image.

pgAdmin 9.19 supports PostgreSQL server versions 14-18. Back up your pgAdmin configuration before upgrading.