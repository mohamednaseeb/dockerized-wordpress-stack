# Docker Networking

## Overview

Docker Networking was used to allow communication between the containers in the WordPress application stack.

Since each service runs in its own container, a network is required so that containers can communicate with each other.

---

## Why Docker Networking Was Needed

The application consists of multiple containers:

* Nginx
* WordPress
* MariaDB
* phpMyAdmin

These containers must exchange information.

Examples:

* Nginx must communicate with WordPress.
* WordPress must communicate with MariaDB.
* phpMyAdmin must communicate with MariaDB.

Without Docker Networking, these containers would not be able to communicate.

---

## Network Architecture

```text
Nginx
  |
  v
WordPress
  |
  v
MariaDB
  ^
  |
phpMyAdmin
```

All containers are connected to the same Docker bridge network.

---

## Docker Bridge Network

Docker Compose automatically creates a bridge network for the application.

This network provides:

* Container-to-container communication
* Automatic service discovery
* Network isolation
* Internal DNS resolution

---

## Service Discovery

One major advantage of Docker Networking is service discovery.

Instead of using IP addresses, containers can communicate using service names.

Examples:

```text
database
wordpress
nginx
phpmyadmin
```

---

## WordPress to MariaDB Communication

The WordPress container connects to MariaDB using:

```text
database:3306
```

Where:

* database = MariaDB service name
* 3306 = MariaDB port

Docker automatically resolves the service name to the correct container.

---

## Nginx to WordPress Communication

Nginx forwards PHP requests to:

```text
wordpress:9000
```

Where:

* wordpress = WordPress service name
* 9000 = PHP-FPM port

This allows Nginx to process dynamic WordPress pages.

---

## phpMyAdmin to MariaDB Communication

phpMyAdmin communicates with MariaDB using:

```text
database
```

This allows database administration through the browser.

---

## Benefits of Docker Networking

### Simplified Communication

Containers communicate using service names instead of IP addresses.

### Improved Portability

The application can be moved to another system without changing IP configurations.

### Better Security

Internal services remain isolated from external networks.

### Easier Management

Docker automatically handles network creation and DNS resolution.

---

## Verification Commands

List Docker networks:

```bash
docker network ls
```

Inspect a network:

```bash
docker network inspect NETWORK_NAME
```

Verify running containers:

```bash
docker compose ps
```

---

## Result

At the end of this phase:

* All containers were connected through a Docker bridge network.
* Containers communicated using service names.
* WordPress successfully connected to MariaDB.
* Nginx successfully connected to WordPress.
* phpMyAdmin successfully connected to MariaDB.
* Internal application communication functioned correctly.
