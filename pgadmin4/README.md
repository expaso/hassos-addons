# Home Assistant Add-on: [pgAdmin 4](https://www.pgadmin.org/)

## Introduction

pgAdmin is the most popular and feature rich Open Source administration and development platform for PostgreSQL, the most advanced Open Source database in the world.

This Add-on can be used to control any postgreSQL databases on your network, incuding those served by the TimescaleDB add-on.

## Installation

To install this Hass.io add-on you need to add the Expaso add-on repository
first:

You can do this by navigating to the "Add-on Store" tab in the Supervisor panel and then entering https://github.com/expaso/hassos-addons in the "Add new repository by URL" field.

Now scroll down and select the "pgAdmin4" add-on.
Press install to download the add-on and unpack it on your machine. This can take some time.

Start the add-on, check the logs of the add-on to see if everything went well.

On first start-up, a new configuration is created. This can take some time.
Please be patient. 

## TimescaleDb

This addon is a standalone implementation of the Postgresql pgAdmin application, and can be used as such.
When this add-on is used together with my ![TimescaleDb] add-on (https://github.com/expaso/hassos-addon-timescaledb), you can connect to the Timescale instance using this hostname: `77b2833f-timescaledb` 

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
__Beware__: Adding a lot of packages could lead to long startup time.

### Option: `init_commands`

Any extra commands that will be run during add-on startup.

### Option: `leave_front_door_open`

Serves the website without protection of  home-assistant user authentication.

__CAUTION!!__

Setting this option is a potential security risk and should be avoided whenever possible.
If you don't know what you are doing, just leave it off.
