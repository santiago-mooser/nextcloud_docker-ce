# THIS IS NOWHERE NEAR COMPLETE. DO NOT PULL.

## nextcloud_docker-ce

[![DDClient](https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/ddclient-logo.png)](https://github.com/ddclient/ddclient) [![Let's Encrypt](https://letsencrypt.org/images/letsencrypt-logo-horizontal.svg)](https://letsencrypt.org/)   [![NextCloud](https://nextcloud.com/wp-content/themes/next/assets/img/common/favicon-touch.png)](https://nextcloud.com) [![MariaDB](https://mariadb.org/wp-content/uploads/2019/02/cropped-mariadb_org_rgb_r_512-1-180x180.png)](https://mariadb.org/) 

This repo sets up a [NextCloud](https://github.com/linuxserver/docker-nextcloud) instance automatically with [DDClient](https://github.com/linuxserver/docker-ddclient) (for DDNS), [Let's Encrypt nginx](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md) (with auto-renewing certs) and [MariaDB containers](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md).

All of the containers used are from [linuxserver.io](linuxserver.io). Credits go to them.


## Setup

Before you try to quickly pull the repo and instantly deploy, you should know that there are a few files that you need to add as configuration, even if there are example configuration files.

- The DDClient configuration file ``volumes/ddclient/ddclient.conf``
- The letsencrypt nginx config file ``volumes/letsencrypt/``

## Parameters

All parameters for this setup should be put in a .env file. [An example file is provided](hhttps://github.com/santiago-espinosa/nextcloud_docker-ce/blob/v0.1/example_env.NOTenv) for your reference.

```
#DDClient variables
ddc_timezone=Asia/Hong_Kong

#MariaDB variables
mdb_name=nextcloud_db
mdb_root_password=ChaNgeMe!!4312
mdb_username=nextcloud
mdb_password=¡cHanGeMetO0!

#Letsencrypt variables
le_timezone=Asia/Hong_Kong
le_domain_name=example.com
le_subdomains=nextcloud
le_email=myemail@fake.example
```

## Resources used

**Refering to config files:**

DDClient config file: []()

Let's Encrypt config file: []()

**Refering to docker compose:**

DDClient env variables: 

MariaDB env variables: [linuxserver.io's github documentation](https://github.com/linuxserver/docker-mariadb)

For Let's Encrypt env variables: [linuxserver.io's github documentation](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md)

For Nextcloud env variables: [Nextcloud commandline installation](https://docs.nextcloud.com/server/stable/admin_manual/installation/command_line_installation.html)