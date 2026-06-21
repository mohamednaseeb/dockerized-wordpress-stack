# Project Overview

## Project Name

Dockerized Multi-Tier WordPress Application

---

## Objective

The objective of this project was to deploy a production-style WordPress application using Docker and Docker Compose.

Instead of installing services directly on the operating system, each component was deployed inside its own container to demonstrate modern application deployment practices.

---

## Technologies Used

* Ubuntu Linux
* Docker
* Docker Compose
* Nginx
* WordPress
* MariaDB
* phpMyAdmin
* Git
* GitHub

---

## Project Components

The application consists of four containers:

### Nginx

Acts as the frontend web server and reverse proxy.

### WordPress

Processes application requests using PHP-FPM.

### MariaDB

Stores WordPress data including users, posts, pages, comments, and settings.

### phpMyAdmin

Provides a web-based interface for database administration.

---

## Architecture

Client Browser

↓

Nginx Container

↓

WordPress Container

↓

MariaDB Container

phpMyAdmin

↓

MariaDB Container

---

## Docker Concepts Demonstrated

* Containerization
* Docker Compose
* Multi-container Applications
* Docker Networking
* Docker Volumes
* Service Discovery
* Persistent Storage

---

## Skills Demonstrated

### Linux Administration

* Docker installation
* Service management
* Command-line operations

### Containerization

* Docker containers
* Docker images
* Docker Compose

### Networking

* Docker bridge networks
* Container communication

### Storage

* Docker volumes
* Persistent data management

### Application Deployment

* WordPress deployment
* Database integration
* Nginx configuration

---

## Outcome

The project successfully deployed a fully functional multi-tier WordPress application using Docker Compose, demonstrating modern containerized infrastructure management practices.
