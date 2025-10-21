![Project Stage][project-stage-shield]
![Maintenance][maintenance-shield]
[![License][license-shield]](https://github.com/expaso/hassos-addon-timescaledb/blob/main/LICENSE)

<a href="https://www.buymeacoffee.com/expaso" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

# Home Assistant Add-on: [PostgreSQL](https://www.postgresql.org/) [TimescaleDB](https://www.timescale.com/)

## [PostgreSql 17.6](https://www.postgresql.org/) & [Postgis 3.6.0](https://postgis.net/) & [TimescaleDB 2.22.1](https://www.timescale.com/) & [TimescaleDB Toolkit 1.21.0](https://github.com/timescale/timescaledb-toolkit) & [pgAgent 4.2.3](https://www.pgadmin.org/docs/pgadmin4/development/pgagent.html)

#### Configuation

Example add-on configuration:

```
 {
    "databases": ["homeassistant"],
    "timescale_enabled": ["homeassistant"],
    "timescaledb": {
      "telemetry": "basic",
      "maxmemory": "512MB",
      "maxcpus": "4"
      },
      "max_connections": 20,
      "system_packages": [],
      "init_commands": []
 }
```

#### Option: `databases`

Sets a list of database-names that will be created for you, once you start the add-on.
You can also create databases on your own ofcourse, using a psql client of your choice.

#### Option: `timescale_enabled`

Sets a list of database-names where the timescale-extentions will be enabled for.
Databases not in this list will act like normal Postgre databases.

#### Option: `timescaledb.telemetry`

Switches the telemetry of TimescaleDb on or off.
Valid options are: 'basic' or 'off'.
See: https://docs.timescale.com/latest/using-timescaledb/telemetry

#### Option: `timescaledb.maxmemory`

Sets the maximum amount of memory that PostgreSQL will claim.
It's important to leave breathing room for other processes on your machine (or raspberry pi), so set these level not too high (say max 50% of your total ram).

Example: `maxmemory="1024MB"`
Or leave empty for accepting auto-tune.

#### Option: `timescaledb.maxcpu`

Sets the maximum number of cores that PostgreSQL will use.
It's important to leave breathing room for other processes on your machine (or raspberry pi), so set these level not too high (say max 75% of your total number of cores).

Example: `maxcpu="2"`
Or leave empty for accepting auto-tune.

See also:
https://docs.timescale.com/latest/getting-started/configuring
for further tuning. Your Postgres.config file is located in the addon's data directory.

#### Option: `max_connections`

Sets the maximum number of connections that PostgreSql will accept.
Setting this higher could lead to more memory usage.

Example: `max_connections=30`

#### Option: `system_packages`

Advanced users only!
A list of extra alpine packages to iunstall during addon-startup.

Example: ['nano']

#### Option: `init_commands`

Advanced users only!
A list of extra commands to run during startup.

To alter something in the postgresql.conf file for example:

Example: ['sed -i -e "/max_connections =/ s/= .*/= 50/" /data/postgres/postgresql.conf']

#### Option: `retry_upgrade`

Advanced users only!
When set, the upgrade from Postgres 14 to 15 could be retryed if it failed mid-flight.
Basically this will try to find the old database-files from Postgres 12, and restore them before trying to upgrade to Postgres 14 again.

!! Please don't set this if you don't know what you are doing or before taking a backup. !!

#### Option: `postgresql_config`

Allows you to customize PostgreSQL server parameters. These settings are applied to `postgresql.conf` and can override default settings.

Example:
```yaml
postgresql_config:
  log_statement: "all"
  work_mem: "16MB"
  maintenance_work_mem: "256MB"
```

See [PostgreSQL documentation](https://www.postgresql.org/docs/current/runtime-config.html) for available parameters.

**Note:** Some critical parameters cannot be modified (e.g., `shared_preload_libraries`, `port`, `data_directory`) as they are managed by the addon.

#### Option: `pg_hba_config`

Allows you to add custom authentication rules to `pg_hba.conf`. Rules are appended to default rules.

Example:
```yaml
pg_hba_config:
  - type: "host"
    database: "homeassistant"
    user: "all"
    address: "192.168.1.0/24"
    method: "md5"
```

See [PostgreSQL documentation](https://www.postgresql.org/docs/current/auth-pg-hba-conf.html) for authentication methods.

**Warning:** Incorrect configuration can lock you out of the database.

### Running the container standalone.

In this case, you need to have a working Docker installation on your machine.
pull one of the images for the desired architecture from docker hub:

```
docker pull ghcr.io/expaso/timescaledb/amd64:stable
docker pull ghcr.io/expaso/timescaledb/aarch64:stable
docker pull ghcr.io/expaso/timescaledb/armv7:stable
docker pull ghcr.io/expaso/timescaledb/armhf:stable
docker pull ghcr.io/expaso/timescaledb/i386:stable
```

You can replace *stable* with the version number you want to use.

Simply start it like this:

```
docker run \
  --rm \
  --name timescaledb \
  --v ${PWD}/timescaledb_addon_data:/data \
  -p 5432:5432 \
  ghcr.io/expaso/timescaledb/amd64:stable
```

This will use ~/timescaledb_addon_data as the data directory for the container, and map the port 5432 to the host.

If you want to start the container as a daemon, simply remove the `--rm` option and add the `-d` option like so:

```
docker run \
  -d \
  --name timescaledb \
  --v ${PWD}/timescaledb_addon_data:/data \
  -p 5432:5432 \
  ghcr.io/expaso/timescaledb/amd64:stable
```

## Usage

You are now ready to start using Postgres with TimescaleDb extenstions enabled!

Seeking a nice web-based client? **Try the pgAdmin4 addon.**

Please do not forget to also map the TCP/IP port in the network-section of the addon to the desired port number.
The default is port `5432`

**Securiy Notice!**

The default username is `postgres` with password `homeassistant`.
Make sure you change this immediately after activating the add-on:

```
ALTER USER postgres WITH PASSWORD 'strongpassword';
```

⚠️ It's considered best practice to create a separate user for each database you create, and transfer ownership of the database to that user.
In this configuration, The `postgres` user should only be used for administrative tasks.

Use the following commands to create a user `homeassistant` with password `mypassword` and transfer ownership of the database `mydatabase` to that user, or use _pgAdmin_ for this task if you prefer a GUI.

```
CREATE USER homeassistant WITH PASSWORD 'mypassword';
ALTER DATABASE mydatabase OWNER TO homeassistant;
```


A default `pg_hba.conf` is created in the data directory with the following content, which allows local peer users and network users with passwords.:

```
# TYPE  DATABASE        USER            ADDRESS                 METHOD
host    all             all             0.0.0.0/0               md5"
local   all             all             0.0.0.0/0               md5"
local   all             all             0.0.0.0/0               peer"
```

Please review this configuration carefully by examine the docs:
https://www.postgresql.org/docs/devel/auth-pg-hba-conf.html

## Backup and Restore

This addon implements a robust backup and restore mechanism designed to protect your database from data loss.

### How Backups Work

When Home Assistant's backup system runs, it automatically:

1. **Pre-Backup**: Executes `pg_dumpall` to create a complete SQL dump of all databases (`backup_db.sql`)
2. **Backup**: Backs up the SQL dump file along with other addon data (but excludes the PostgreSQL data directory)
3. **Post-Backup**: Removes the temporary SQL dump file to save space

This approach has several advantages:

- **Consistency**: SQL dumps are transaction-consistent snapshots
- **Safety**: No risk of backing up corrupted or in-transition database files
- **Portability**: SQL dumps can be restored across different PostgreSQL versions
- **Small Size**: Excludes the large PostgreSQL data directory from backup

### How Restore Works

When you restore a Home Assistant backup:

1. The addon starts up with the restored `backup_db.sql` file
2. If the PostgreSQL data directory is missing or corrupted, the addon:
   - Initializes a fresh PostgreSQL database
   - Automatically restores all data from the SQL dump
   - Removes the SQL dump after successful restoration

This automatic recovery process ensures your data is safely restored even if:

- The database files were corrupted
- You're restoring to a different system
- A PostgreSQL upgrade failed

### Manual Backup

You can also create manual backups using the PostgreSQL command-line tools:

**Create a backup:**

```bash
docker exec addon_timescaledb_timescaledb su - postgres -c "pg_dumpall -U postgres --clean --if-exists -f /data/manual_backup_$(date +%Y%m%d).sql"
```

**Restore from a manual backup:**

```bash
docker exec addon_timescaledb_timescaledb su - postgres -c "psql -U postgres -f /data/manual_backup_YYYYMMDD.sql -d postgres"
```

### Important Notes

- The SQL dump is only present during the backup process and is automatically cleaned up
- If you need to keep a copy of the backup SQL file, copy it before the backup completes
- The PostgreSQL data directory (`/data/postgres/*`) is excluded from backups to reduce backup size and improve reliability
- Restore is automatic - no manual intervention required when restoring from a Home Assistant backup

### Troubleshooting

**If restore fails:**

1. Check the addon logs for detailed error messages
2. The backup SQL file will be preserved at `/data/backup_db.sql` for manual recovery
3. You can attempt manual restoration using:

   ```bash
   docker exec -it addon_timescaledb_timescaledb su - postgres -c "psql -U postgres -f /data/backup_db.sql -d postgres"
   ```

**If backup fails:**

- Check that PostgreSQL is running during the backup
- Ensure there's sufficient disk space for the SQL dump
- Review the addon logs for specific error messages

### Now what..

Well.. Dive in!

You can read additional documentation on how you van work with your data and Grafana here:

https://github.com/expaso/hassos-addons/issues/1

## Support

- Got questions?
  [Open an issue here][issues]

- For a general repository issue or add-on ideas? [Open an issue here][repo-issues]

[issues]: https://github.com/expaso/hassos-addon-timescaledb/issues
[repo-issues]: https://github.com/expaso/hassos-addons/issues



[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[release-shield]: https://img.shields.io/badge/version-v5.4.1-blue.svg
[release]: https://github.com/expaso/hassos-addon-timescaledb/tree/v5.4.1
[license-shield]: https://img.shields.io/github/license/expaso/hassos-addon-TimescaleDB.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2025.svg