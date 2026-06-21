# Docker Compose Configuration

## Overview

Docker Compose was used to define and manage the complete multi-container WordPress application.

Instead of running each container manually, Docker Compose allows all services, networks, volumes, environment variables, and port mappings to be managed from a single YAML file.

The main configuration file used in this project is:

docker-compose.yml

---

## Why Docker Compose Was Used

Docker Compose was used to manage:

* Nginx container
* WordPress container
* MariaDB container
* phpMyAdmin container
* Docker network
* Docker volumes
* Port mappings
* Environment variables

---

## Services Defined

| Service    | Purpose                       |
| ---------- | ----------------------------- |
| Nginx      | Web server and reverse proxy  |
| WordPress  | WordPress application         |
| MariaDB    | Database server               |
| phpMyAdmin | Database management interface |

---

## MariaDB Service

The MariaDB container stores all WordPress data, including:

* Users
* Posts
* Pages
* Comments
* Site settings

Environment variables were used to configure the database credentials and database name.

A Docker volume was attached to MariaDB so that database data remains available even if the container is recreated.

---

## WordPress Service

The WordPress container runs the WordPress application using PHP-FPM.

It connects to MariaDB through the internal Docker network using the database service name.

This allows WordPress to communicate directly with MariaDB without requiring an external IP address.

---

## Nginx Service

The Nginx container acts as the frontend web server.

It receives HTTP requests from users and forwards PHP requests to the WordPress container.

Port mapping was configured so that:

Host Port 8080 → Nginx Container Port 80

This allows users to access the WordPress website through a browser.

A custom Nginx configuration file was mounted into the container to control request routing and PHP processing.

---

## phpMyAdmin Service

phpMyAdmin provides a browser-based interface for database administration.

It allows:

* Viewing databases
* Managing tables
* Running SQL queries
* Managing WordPress data

Port mapping was configured so that:

Host Port 8081 → phpMyAdmin Container Port 80

---

## Docker Volumes

Two persistent volumes were used:

### db_data

Stores MariaDB database files.

### wordpress_data

Stores WordPress application files.

Docker volumes prevent data loss when containers are restarted or recreated.

---

## Docker Network

All containers communicate through a Docker bridge network.

The network allows containers to communicate using service names such as:

* database
* wordpress
* nginx
* phpmyadmin

This removes the need to use static IP addresses.

---

## Deployment Command

The complete application stack was deployed using:

docker compose up -d

The `-d` option runs containers in detached mode.

---

## Verification Commands

Check running containers:

docker compose ps

View container logs:

docker compose logs

List running containers:

docker ps

---

## Result

At the end of this phase:

* Docker Compose successfully created all containers.
* WordPress connected to MariaDB.
* Nginx served the WordPress application.
* phpMyAdmin was accessible through the browser.
* Docker volumes provided persistent storage.
* Docker networking enabled communication between containers.
