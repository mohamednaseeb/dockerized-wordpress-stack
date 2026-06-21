# Architecture

## Overview

This project uses a multi-container architecture where each service runs in its own Docker container.

Instead of installing Nginx, WordPress, MariaDB, and phpMyAdmin directly on the host operating system, Docker Compose manages each service as an isolated container.

---

## Architecture Diagram

```text
Client Browser
      |
      | HTTP :8080
      v
Nginx Container
      |
      | FastCGI :9000
      v
WordPress Container
      |
      | MySQL :3306
      v
MariaDB Container


Client Browser
      |
      | HTTP :8081
      v
phpMyAdmin Container
      |
      | MySQL :3306
      v
MariaDB Container


## Container Responsibilities

| Container | Purpose |
|------------|-----------|
| Nginx | Reverse proxy and web server |
| WordPress | Application container running PHP-FPM |
| MariaDB | Database server |
| phpMyAdmin | Database management interface |

## Network Flow

WordPress Request:

Browser → Nginx → WordPress → MariaDB

phpMyAdmin Request:

Browser → phpMyAdmin → MariaDB

## Port Mapping

| Port | Service |
|--------|----------|
| 8080 | WordPress via Nginx |
| 8081 | phpMyAdmin |
| 3306 | MariaDB |
| 9000 | PHP-FPM |

## Benefits of Containerization

- Service isolation
- Easy deployment
- Consistent environments
- Scalability
- Simplified troubleshooting
- Persistent storage using Docker Volumes
