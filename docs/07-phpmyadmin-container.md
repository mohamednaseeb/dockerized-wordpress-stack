# phpMyAdmin Container

## Overview

phpMyAdmin was deployed as a separate Docker container to provide a web-based interface for managing the MariaDB database.

Instead of using command-line database tools, phpMyAdmin allows database administration through a browser.

---

## Role of the phpMyAdmin Container

The phpMyAdmin container is responsible for:

* Managing MariaDB databases
* Viewing database tables
* Running SQL queries
* Managing users and permissions
* Monitoring WordPress database content

---

## Why phpMyAdmin Was Used

phpMyAdmin simplifies database administration by providing a graphical user interface.

Benefits include:

* Easy database management
* Browser-based access
* Table browsing
* SQL query execution
* User-friendly interface

---

## Database Connectivity

The phpMyAdmin container connects directly to the MariaDB container using Docker networking.

Connection flow:

phpMyAdmin → MariaDB

The MariaDB service name was used as the database host.

This allows phpMyAdmin to communicate with the database without requiring an external IP address.

---

## Port Mapping

The phpMyAdmin container was exposed on port 8081.

Port mapping:

Host Port 8081 → Container Port 80

Access URL:

http://SERVER_IP:8081

---

## Functions Performed

Using phpMyAdmin, administrators can:

### View Databases

* List available databases
* Inspect WordPress tables

### Execute SQL Queries

Example:

```sql
SHOW DATABASES;
```

### Manage Tables

* Create tables
* Modify tables
* Delete tables

### User Administration

* Manage database users
* Review permissions

---

## WordPress Database Visibility

Through phpMyAdmin, the following WordPress tables can be viewed:

* wp_users
* wp_posts
* wp_comments
* wp_options
* wp_terms

These tables store WordPress content and configuration.

---

## Security Considerations

phpMyAdmin was deployed for administration purposes only.

Database access requires valid MariaDB credentials.

The container communicates with MariaDB through the internal Docker network.

---

## Verification

The phpMyAdmin container was verified using:

docker compose ps

Browser access was verified using:

http://SERVER_IP:8081

Successful login confirmed proper communication with the MariaDB container.

---

## Result

At the end of this phase:

* phpMyAdmin was running successfully in its own container.
* Database administration was available through a browser.
* MariaDB connectivity was verified.
* WordPress database tables were accessible.
* Database management tasks could be performed without using command-line tools.
