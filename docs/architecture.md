# Architecture

## Overview

This project deploys a self-hosted cloud storage platform using Docker Compose.

## Components

### Nextcloud

Provides the web interface, file management, synchronization and user access.

### MariaDB

Stores Nextcloud application data and metadata.

## Architecture

```text
Client Devices
      |
      | HTTP
      v
Nextcloud Container
      |
      | Database Connection
      v
MariaDB Container
