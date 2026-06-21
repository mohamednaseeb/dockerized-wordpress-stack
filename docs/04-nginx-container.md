# Nginx Container Configuration

## Overview

Nginx was used as the frontend web server for the Dockerized WordPress application.

In this project, Nginx runs inside its own Docker container and receives HTTP requests from the browser.

---

## Role of Nginx

Nginx is responsible for:

* Receiving web requests from users
* Serving the WordPress website
* Forwarding PHP requests to the WordPress container
* Acting as the entry point for the application

---

## Port Mapping

The Nginx container listens on port 80 internally.

It was mapped to port 8080 on the host machine.

Host Port 8080 → Nginx Container Port 80

This allows the website to be accessed using:

http://SERVER_IP:8080

---

## Custom Nginx Configuration

A custom Nginx configuration file was created at:

nginx/default.conf

This file was mounted into the Nginx container.

The configuration defines:

* Website root directory
* Index files
* PHP request handling
* WordPress routing
* Security rule for hidden files

---

## WordPress Document Root

The document root was configured as:

/var/www/html

This is where the WordPress files are available inside the container.

---

## PHP Request Handling

Nginx does not process PHP directly.

Instead, PHP requests are forwarded to the WordPress container using PHP-FPM.

Nginx forwards PHP requests to:

wordpress:9000

Here:

* wordpress is the Docker service name
* 9000 is the PHP-FPM port

---

## WordPress Routing

The Nginx configuration uses WordPress routing so that pages and admin URLs work correctly.

This allows URLs such as:

* /
* /wp-admin
* /wp-login.php
* /index.php

to be handled properly.

---

## Security Configuration

Access to hidden files was blocked using an Nginx rule.

This helps prevent access to sensitive files such as:

* .htaccess
* .env
* hidden configuration files

---

## Why Nginx Was Used

Nginx was used because it is:

* Lightweight
* Fast
* Common in production environments
* Widely used as a reverse proxy
* Suitable for containerized applications

---

## Verification

The Nginx container was verified using:

docker compose ps

The website was tested in the browser using:

http://SERVER_IP:8080

Successful loading of the WordPress site confirmed that Nginx was correctly forwarding requests to the WordPress container.

---

## Result

At the end of this phase:

* Nginx was running inside a container.
* Nginx exposed the WordPress site on port 8080.
* PHP requests were forwarded to the WordPress container.
* WordPress routing worked correctly.
* The Dockerized WordPress site was accessible from a browser.
