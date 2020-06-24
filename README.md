# THIS IS NOWHERE NEAR COMPLETE. DO NOT PULL.

## nextcloud_docker-ce

[Nextcloud](https://nextcloud.com/wp-content/themes/next/assets/img/common/favicon.png?x53054)

This repo sets up a [NextCloud](https://github.com/linuxserver/docker-nextcloud) instance automatically with [DDClient](https://github.com/linuxserver/docker-ddclient) (for DDNS), [Let's Encrypt nginx](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md) (with auto-renewing certs) and [MariaDB containers](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md).

All of the containers used are from [linuxserver.io](linuxserver.io). Credits go to them.


## Parameters

All parameters for this setup should be put in a .env file. [An example file is provided](https://github.com/santiago-espinosa/INSERTLINKHERE) for your reference.


## Resources used

**Refering to config files:**
DDClient config file: []()
Let's Encrypt config file: []()

**Refering to docker compose:**
DDClient env variables: 
MariaDB env variables: [linuxserver.io's github documentation](https://github.com/linuxserver/docker-mariadb)
For Let's Encrypt env variables: [linuxserver.io's github documentation](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md)
For Nextcloud env variables: [Nextcloud commandline installation](https://docs.nextcloud.com/server/stable/admin_manual/installation/command_line_installation.html)