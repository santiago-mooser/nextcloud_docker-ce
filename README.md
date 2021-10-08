# THIS IS NOWHERE NEAR COMPLETE. DO NOT PULL.

## nextcloud_docker-ce

[![DDClient](https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/ddclient-logo.png)](https://github.com/ddclient/ddclient) [![Let's Encrypt](https://letsencrypt.org/images/letsencrypt-logo-horizontal.svg)](https://letsencrypt.org/)   [![NextCloud](https://nextcloud.com/wp-content/themes/next/assets/img/common/favicon-touch.png)](https://nextcloud.com) [![MariaDB](https://mariadb.org/wp-content/uploads/2019/02/cropped-mariadb_org_rgb_r_512-1-180x180.png)](https://mariadb.org/) 

This repo sets up a [NextCloud](https://github.com/linuxserver/docker-nextcloud) instance automatically with [DDClient](https://github.com/linuxserver/docker-ddclient) (for DDNS), [Let's Encrypt nginx](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md) (with auto-renewing certs) and [MariaDB containers](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md) on RHEL/CentOS or Debian/Ubuntu servers.

## Setup

Before you try to quickly pull the repo and instantly deploy, you should know that there are a few files that you need to add as configuration, even if there are example configuration files.

- The DDClient configuration file ``volumes/ddclient/ddclient.conf``
- The letsencrypt nginx config file ``volumes/letsencrypt/``

# Notice

This repo is designed to be used with the help of [the nextcloud_ansible repo](https://github.com/santiago-espinosa/nextcloud_ansible.git), which will pull this repo and setup some defaults. 

The [the nextcloud_ansible repo](https://github.com/santiago-espinosa/nextcloud_ansible.git) will **automatically populate**:
- Nginx's **nextcloud.subdomain.conf** file for nextcloud with a modern setup from [Mozilla's SSL configuration generator](https://ssl-config.mozilla.org/#server=nginx&version=1.17.7&config=modern&openssl=1.1.1d&guideline=5.4).
- The **.env** file needed for the correct setup of the docker-ce containers.
- The **ddclient.conf** file based on ***your*** defaults.

It will also:
- Setup the MariaDB container for it to work with nextcloud (some short commands need to be run).
- Connect the Nextcloud container to the MariaDB container.
- Add your site to the Nextcloud container's authorized sites (so that the nginx container can connect to the service).
- Connect the nginx container to the nextcloud container.

[SpaceInvader One's Nextcloud on unraid](https://www.youtube.com/watch?v=fUPmVZ9CgtM) has a similar setup, but this is done automagically with the help of [Ansible](https://www.ansible.com/).


# Requirenments

All parameters for this setup should be put in a .env file. [An example file is provided](hhttps://github.com/santiago-espinosa/nextcloud_docker-ce/blob/v0.1/example_env.NOTenv) for your reference. **However, this can automatically be done by [the nextcloud_ansible repo](https://github.com/santiago-espinosa/nextcloud_ansible.git)**.

### Variables
```
#DDClient variables
ddc_timezone=Asia/Hong_Kong

#MariaDB variables
mdb_name=nextcloud_db
mdb_root_password=ChaNgeMe!!4312
mdb_username=nextcloud
mdb_password=¡cHanGeMetO0!
mdb_timezone=Asia/Hong_Kong

#Letsencrypt variables
le_timezone=Asia/Hong_Kong
le_domain_name=example.com
le_subdomains=nextcloud
le_email=myemail@fake.example
```

## Debugging

### Making sure the database is working properly

run:

```docker logs $(docker ps | grep mariadb | awk '{print $1}') | grep 'Setup'``` 

(This can only be run on bash, not sh, due to the bash-ism of the command) and make sure the output in the last line contains:

```Database Setup Completed```

### Making sure nginx is working properly

run

```docker logs $(docker ps | grep nextcloud | awk '{print $1}')```

and check for any error messages.


## Config files resources:

DDClient config file documentation:
- [Guide on setting up DDClient](https://help.dyn.com/ddclient/)
- [NameCheap's DDClient setup](https://www.namecheap.com/support/knowledgebase/article.aspx/583/11/how-do-i-configure-ddclient)

Let's Encrypt's nginx's config file for nextcloud: 
- [Official nextcloud documentation](https://docs.nextcloud.com/server/16/admin_manual/installation/nginx.html)
- [example nextcloud.conf](https://gist.github.com/xxblx/2e213aba16c66a9ea591e04d057d61c3) (credits to [xxblx](https://gist.github.com/xxblx))
- [SpaceInvader One's unraid instance of the same setup](https://www.youtube.com/watch?v=fUPmVZ9CgtM)

## Container variable resourses:

DDClient env variables: [linuxserver.io's github documentation for DDClient container](https://github.com/linuxserver/docker-ddclient)

MariaDB env variables: [linuxserver.io's github documentation for MariaDB comtainer](https://github.com/linuxserver/docker-mariadb)

For Let's Encrypt env variables: [linuxserver.io's github documentation for Let's Encrypt's nginx container](https://github.com/linuxserver/docker-letsencrypt/blob/master/README.md)

For Nextcloud env variables: [Nextcloud commandline installation](https://docs.nextcloud.com/server/stable/admin_manual/installation/command_line_installation.html)

# Credits

All of the containers used are from [linuxserver.io](https://fleet.linuxserver.io). Credits go to them, [Let's Encrypt](https://letsencrypt.org/), [nginx](https://www.nginx.com/), [Nextcloud](https://nextcloud.com/), [DDClient](https://github.com/ddclient/ddclient) and the [MariaDB Organisation](https://mariadb.org/).

# Dependencies

None.

# License

GNU GPL v3.0

# Author

This repository was created by [Santiago Espinosa](https://keybase.io/santiagoespinosa) in 2020
