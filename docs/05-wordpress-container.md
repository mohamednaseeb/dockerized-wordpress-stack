# WordPress Container

## Overview

The WordPress container runs the main web application in this project.

WordPress is responsible for generating the website pages, handling admin login, managing posts, themes, plugins, and connecting to the database.

---

## Role of the WordPress Container

The WordPress container is responsible for:

* Running the WordPress application
* Processing PHP requests using PHP-FPM
* Connecting to the MariaDB database
* Serving dynamic website content
* Managing WordPress files, themes, and plugins

---

## WordPress Image

The project used the official WordPress image with PHP-FPM support.

This image includes:

* WordPress application files
* PHP runtime
* PHP-FPM process manager
* Required PHP components

---

## Database Connection

WordPress connects to the MariaDB container using Docker networking.

The database host was configured as:

database:3306

Here:

* database is the MariaDB service name
* 3306 is the database port

This allows WordPress to communicate with MariaDB without using an external IP address.

---

## Environment Variables

Environment variables were used to configure the WordPress database connection.

These included:

* Database host
* Database name
* Database username
* Database password

This allows WordPress to automatically connect to MariaDB during setup.

---

## Persistent WordPress Data

A Docker volume was used to store WordPress files.

This helps preserve:

* WordPress core files
* Themes
* Plugins
* Uploaded media
* Configuration data

even if the WordPress container is restarted or recreated.

---

## Relationship with Nginx

Nginx receives web requests from users.

When a PHP page needs to be processed, Nginx forwards the request to the WordPress container through PHP-FPM.

The request flow is:

Browser → Nginx → WordPress → MariaDB

---

## Verification

The WordPress container was verified using:

docker compose ps

The WordPress site was accessed from the browser using:

http://SERVER_IP:8080

Successful loading of the WordPress installation page confirmed that the WordPress container was working correctly.

---

## Result

At the end of this phase:

* WordPress was running inside its own container.
* PHP-FPM processed WordPress requests.
* WordPress connected successfully to MariaDB.
* WordPress data was stored using a Docker volume.
* The WordPress site was accessible through Nginx.
