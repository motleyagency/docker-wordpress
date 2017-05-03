# Docker Wordpress boilerplate

Creates a "minimalistic" dockerized Wordpress with Alpine Linux, Nginx, PHP 7 and MariaDB.

## Setup

You might want to prefix the following container names in `docker-compose.yml` with project name before building.

- wordpress_nginx
- wordpress_php
- wordpress_mariadb

### Wordpress

Automatically downloads the Wordpress package and extracts it to `html` folder. However if you are setting up an environment for existing project you can replace the contents with your project's files.

#### Wordpress specific defaults

You might want to change these.

- WORDPRESS_DB_NAME=wpdb
- WORDPRESS_TABLE_PREFIX=wp_
- WORDPRESS_DB_HOST=db
- WORDPRESS_DB_PASSWORD=root

### MariaDB

Database is stored locally inside the `data/mariadb` folder in your project root.

You can access the database for example with Sequel Pro with following settings (default passwords).

- Host = 127.0.0.1
- Username = root
- Password = root
- Port = 3306

### SSL

If you need SSL certificates follow the next steps:

- in `nginx/conf.d/`, make a backup of `default.conf` and rename `default_SSL.conf` to `default.conf`
- open Keychain, select System from sidebar and drag'n'drop the `localhost.crt` from **certs** folder to Keychain
- Double click the `localhost.crt` in Keychain and then select **Always Trust** from the first dropdown labeled "When using this certificate:". This will affect all dropdowns, which is what we are after.

## Usage

After customizing your configuration, you can build the containers with

```
docker-compose build
```

And run the containers with
```
docker-compose up
```

The non-SSL app will run on port 8080. If you use SSL, the port will be 443.

## WordPress configuration

After completing the WordPress installation (boot container and navigate to `http://localhost:8080`), change the permalink setting in the [WP Admin interface](http://localhost:8080/wp-admin/options-permalink.php) to **Post name**. This will make the posts available at pretty URLs and also enable the default URL to the [REST API](http://localhost:8080/wp-json).

## More info

This Docker compose file is based on a work by evild and uses his images. Some changes are made, most notably this uses separate Wordpress/PHP image with currently latest Wordpress 4.7.2

https://github.com/Evild67/docker-compose-wordpress

https://hub.docker.com/r/evild/alpine-nginx/

https://hub.docker.com/r/turanturan/alpine-wordpress/

https://hub.docker.com/r/evild/alpine-php/

https://hub.docker.com/r/evild/alpine-base/
