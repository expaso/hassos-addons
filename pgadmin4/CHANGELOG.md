## 2.0.0

- Upgraded pgAdmin to 6.5
- Upgraded base images to be in-line with the lastest home-assistant add-ons
- Dropped support for Postgresql 9
- Added support for Postgresql 13 and 14
- Patched a reg-ex in sourcecode that prevented hostnames staring with digits to be used. This fixes the problem whereby a hostname like 77b2833f-timescaledb validated as an invalid hostname.

## 1.2.1

- Updated pgAdmin to 5.3
See also: https://www.pgadmin.org/docs/pgadmin4/development/release_notes_5_3.html
- Updated base images

## 1.2.0

- Updated pgAdmin to 5.0
See also: https://www.pgadmin.org/docs/pgadmin4/development/release_notes_5_0.html
- Updated base images (Thanks @sinclairpaul for getting my CI working again with this version leap!)

## 1.1.0

- Updated pgAdmin to 4.30
See also: https://www.pgadmin.org/docs/pgadmin4/development/release_notes_4_30.html
- Upgraded base image from 7.0.1 to 9.1.2

## 1.0.6

- Updated pgAdmin to 4.27
See also: https://www.pgadmin.org/docs/pgadmin4/development/release_notes_4_27.html

## 1.0.5

- Updated pgAdmin to 4.25
See also: https://www.pgadmin.org/docs/pgadmin4/development/release_notes_4_25.html

## 1.0.4

- Updated pgAdmin to 4.23
See also: https://www.pgadmin.org/docs/pgadmin4/development/release_notes_4_23.html

## 1.0.3

- Updated pgAdmin to 4.22
See also: https://www.pgadmin.org/docs/pgadmin4/development/release_notes_4_22.html

## 1.0.2

- Fixed ingress (Sidebar UI) when serving HA from a non-standard http-port
  for architectures aarch64 and armv7.

## 1.0.1

- Fixed ingress (Sidebar UI) when serving HA from a non-standard http-port.

## 1.0.0

- Initial release.
