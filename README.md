# Dockerized Multi-Tier WordPress Stack

## Project Overview

A multi-container WordPress deployment using Docker Compose.

## Architecture

Client Browser
|
v
Nginx
|
v
WordPress
|
v
MariaDB

phpMyAdmin
|
v
MariaDB

## Technologies Used

- Docker
- Docker Compose
- Nginx
- WordPress
- MariaDB
- phpMyAdmin
- Linux

## Features

- Multi-container architecture
- Persistent storage using Docker Volumes
- Internal service communication using Docker Networks
- WordPress CMS deployment
- Database management through phpMyAdmin

## Containers

| Container | Purpose |
|------------|------------|
| Nginx | Reverse proxy and web server |
| WordPress | Application container |
| MariaDB | Database server |
| phpMyAdmin | Database administration |

## Docker Concepts Demonstrated

- Containerization
- Docker Compose
- Docker Networking
- Docker Volumes
- Service Discovery
- Persistent Storage

## Project Verification

- All containers running
- WordPress installation completed
- MariaDB connected successfully
- phpMyAdmin accessible
- Docker network verified
- Docker volumes verified
