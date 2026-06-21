# Docker Volumes

## Overview

Docker Volumes were used to provide persistent storage for the WordPress application.

Containers are designed to be temporary. If a container is deleted and recreated, any data stored inside the container can be lost.

Docker Volumes solve this problem by storing data outside the container.

---

## Why Docker Volumes Were Needed

This project contains important data such as:

* WordPress posts
* WordPress pages
* User accounts
* Uploaded images
* Themes
* Plugins
* Database records

Without persistent storage, this data would be lost if containers were recreated.

---

## Volumes Used in the Project

Two Docker Volumes were created:

### db_data

Stores MariaDB database files.

Contents include:

* Database tables
* User accounts
* WordPress content
* Site configuration

---

### wordpress_data

Stores WordPress application files.

Contents include:

* Themes
* Plugins
* Media uploads
* WordPress configuration files

---

## Volume Architecture

```text
WordPress Container
        |
        v
wordpress_data Volume

MariaDB Container
        |
        v
db_data Volume
```

---

## How Volumes Work

When a container writes data:

```text
WordPress
     |
     v
wordpress_data
```

or

```text
MariaDB
     |
     v
db_data
```

the data is stored in the Docker Volume instead of inside the container.

This means the data remains available even if the container is removed.

---

## Example Scenario

A user uploads an image to WordPress.

Without a volume:

```text
Delete Container
      |
      v
Image Lost
```

With a volume:

```text
Delete Container
      |
      v
Image Remains in Volume
```

The new container can access the same data.

---

## Benefits of Docker Volumes

### Persistent Storage

Data remains available after container recreation.

### Backup and Recovery

Volumes can be backed up independently of containers.

### Separation of Data and Application

Application containers can be replaced without affecting stored data.

### Easier Upgrades

Containers can be upgraded while preserving existing data.

---

## Verification Commands

List available volumes:

```bash
docker volume ls
```

Inspect a volume:

```bash
docker volume inspect VOLUME_NAME
```

Verify application functionality:

```bash
docker compose ps
```

---

## Importance in Production Environments

Persistent storage is essential in production environments because:

* Databases must retain data
* Website uploads must be preserved
* Application upgrades should not cause data loss

Docker Volumes provide a reliable solution for these requirements.

---

## Result

At the end of this phase:

* MariaDB data was stored in a persistent Docker Volume.
* WordPress files were stored in a persistent Docker Volume.
* Application data remained available after container restarts.
* Data persistence was successfully implemented.
* The Dockerized application became more reliable and production-ready.
