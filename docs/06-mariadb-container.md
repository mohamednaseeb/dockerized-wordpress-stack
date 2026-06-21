# MariaDB Container

## Overview

MariaDB was used as the database server for the Dockerized WordPress application.

The MariaDB container stores all website data required by WordPress, including users, posts, pages, comments, and site settings.

---

## Role of the MariaDB Container

The MariaDB container is responsible for:

* Storing WordPress data
* Managing user accounts
* Storing website content
* Handling database queries
* Providing persistent storage for application data

---

## Why MariaDB Was Used

MariaDB is a popular open-source relational database management system.

It is:

* Fast
* Reliable
* MySQL-compatible
* Widely used with WordPress
* Suitable for production environments

---

## Database Information Stored

MariaDB stores:

### Users

* Administrator accounts
* WordPress user accounts

### Content

* Posts
* Pages
* Comments

### Configuration

* WordPress settings
* Plugin settings
* Theme settings

### Metadata

* Categories
* Tags
* Upload information

---

## Database Configuration

The database was configured using Docker Compose environment variables.

These variables defined:

* Database name
* Database username
* Database password
* Root password

This allowed automatic database creation during container startup.

---

## Docker Volume Integration

A Docker volume was attached to MariaDB:

db_data

This volume stores:

* Database files
* Tables
* Records
* User information

The volume ensures data remains available even if the MariaDB container is removed and recreated.

---

## Communication with WordPress

The WordPress container communicates with MariaDB through the Docker network.

Connection flow:

WordPress → MariaDB

The database service name was used instead of an IP address.

This simplifies container communication and improves portability.

---

## Security Considerations

The MariaDB container was not exposed directly to the internet.

Only containers within the Docker network could access the database.

This improves security by limiting external access.

---

## Verification

The MariaDB container was verified using:

docker compose ps

Database connectivity was verified by successfully completing the WordPress installation process.

phpMyAdmin was also used to confirm database accessibility.

---

## Result

At the end of this phase:

* MariaDB was running successfully inside a container.
* WordPress connected to MariaDB correctly.
* Database data was stored using a persistent Docker volume.
* Database access was restricted to internal Docker networking.
* WordPress content could be stored and retrieved successfully.
