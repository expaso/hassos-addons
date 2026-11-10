## 🐛 Bug Fixes

- Fix standalone mode: empty options instead of failing on log\_level @expaso (#96)

Only affects the container outside Home Assistant (plain Docker / Compose): 6.1.0 stopped right away with `Unknown log_level`. In Home Assistant nothing changes.

Coming from 5.x? See the upgrade notes of [6.1.0](https://github.com/expaso/hassos-addon-timescaledb/releases/tag/v6.1.0): the first start upgrades your databases to PostgreSQL 18, so take a backup first.
