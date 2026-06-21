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
