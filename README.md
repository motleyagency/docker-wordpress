# Docker Wordpress boilerplate

Creates a "minimalistic" dockerized Wordpress with Alpine Linux, Nginx, PHP 7 and MariaDB.

## Usage
```docker-compose up -d```

You might want to prefix container names with project name
- wordpress_nginx
- wordpress_php
- wordpress_mariadb

## Wordpress

Automatically downloads the Wordpress package and extracts it to **html** folder. However if you are setting up an environment for existing project you can replace the contents with your projects' files.

### Wordpress specific defaults

You might want to change these.

- WORDPRESS_DB_NAME=wpdb
- WORDPRESS_TABLE_PREFIX=wp_
- WORDPRESS_DB_HOST=db
- WORDPRESS_DB_PASSWORD=root

## MariaDB

Database is stored locally inside the data/mariadb folder in your project root.

You can access the database for example with Sequel Pro with following settings. Passwords only work if you haven't changed the defaults.

- Host = 127.0.0.1
- Username = root
- Password = root
- Port = 3306

## More info

This Docker compose file is based on a work by evild and uses his images. Some changes are made, most notably this uses separate Wordpress/PHP image with currently latest Wordpress 4.7.2

https://github.com/Evild67/docker-compose-wordpress