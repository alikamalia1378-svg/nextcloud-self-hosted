# Nextcloud Self-Hosted Cloud Storage

A self-hosted cloud storage platform built with **Nextcloud, Docker, Docker Compose and MariaDB** on Ubuntu.

The goal of this project is to deploy a private cloud environment for file storage, synchronization and multi-device access while documenting the deployment, networking and security considerations.

## 🚀 Features

* Self-hosted cloud storage
* File upload and management
* File synchronization between devices
* Multi-device access
* Docker-based deployment
* MariaDB database backend
* Persistent data storage
* Docker network communication
* Network connectivity testing and troubleshooting
* Security-oriented configuration

## 🏗️ Architecture

```text
                    Client Devices
                 ┌────────┬────────┐
                 │        │        │
              Laptop    Phone    Desktop
                 │        │        │
                 └────────┼────────┘
                          │
                       HTTP :8080
                          │
                          ▼
                ┌──────────────────┐
                │    Nextcloud     │
                │    Container     │
                └────────┬─────────┘
                         │
                    MySQL Protocol
                         │
                         ▼
                ┌──────────────────┐
                │     MariaDB      │
                │    Container     │
                └──────────────────┘
```

## 🛠️ Technologies

| Technology     | Purpose                |
| -------------- | ---------------------- |
| Ubuntu         | Host operating system  |
| Docker         | Containerization       |
| Docker Compose | Service orchestration  |
| Nextcloud      | Cloud storage platform |
| MariaDB        | Database               |
| Git            | Version control        |
| GitHub         | Project hosting        |

## 📁 Project Structure

```text
nextcloud-self-hosted/
├── docker-compose.yml
├── README.md
├── .gitignore
└── docs/
    └── architecture.md
```

Runtime data is intentionally excluded from the repository:

```text
html/
db/
.env
```

These directories may contain application data, database files or credentials.

## ⚙️ Installation

### Requirements

* Ubuntu Linux
* Docker
* Docker Compose
* Git
* At least one available network interface

### Clone the repository

```bash
git clone https://github.com/alikamalia1378-svg/nextcloud-self-hosted.git
cd nextcloud-self-hosted
```

### Configure environment variables

Create a `.env` file:

```env
MYSQL_ROOT_PASSWORD=your_secure_root_password
MYSQL_PASSWORD=your_secure_database_password
```

Do not commit `.env` to Git.

### Start the services

```bash
docker compose up -d
```

### Check running containers

```bash
docker compose ps
```

### View logs

```bash
docker compose logs
```

## 🌐 Access

Nextcloud is exposed through port `8080`.

```text
http://SERVER_IP:8080
```

Example:

```text
http://10.241.209.165:8080
```

The server IP may be different depending on the network configuration.

## 🔌 Networking

The project uses Docker networking to allow communication between the Nextcloud and MariaDB containers.

Example Docker topology:

```text
Host
 │
 ├── Port 8080
 │      │
 │      ▼
 │   Nextcloud
 │      │
 │      ▼
 │   MariaDB
 │
 └── Docker Network
```

Network troubleshooting was performed using Linux networking tools including:

```bash
ip addr
ip route
ss
ping
curl
tcpdump
```

Docker networking was also inspected during troubleshooting.

## 🔐 Security

Security considerations for a production deployment include:

* Never commit passwords or secrets to GitHub.
* Store credentials in environment variables or a secret-management system.
* Keep runtime directories outside version control.
* Use HTTPS/TLS for production access.
* Restrict exposed ports using a firewall.
* Keep Docker images updated.
* Use strong database credentials.
* Avoid exposing the database directly to the public network.

## 🧪 Troubleshooting

During deployment, network connectivity was tested between multiple devices.

Useful commands:

### Check IP configuration

```bash
ip addr
```

### Check routing

```bash
ip route
```

### Check listening ports

```bash
ss -nltp
```

### Test HTTP connectivity

```bash
curl http://SERVER_IP:8080
```

### Monitor network traffic

```bash
sudo tcpdump -i wlp2s0 port 8080
```

### Check Docker containers

```bash
docker ps
```

### Check Docker networks

```bash
docker network ls
```

## 📌 Project Status

**Deployment:** Completed

**Containerization:** Completed

**Database:** MariaDB configured

**Multi-device testing:** Performed

**Networking troubleshooting:** Performed

**Documentation:** In progress

## 🎯 Future Improvements

* HTTPS with a valid TLS certificate
* Reverse proxy using Nginx or Caddy
* Domain-based access
* Automatic backups
* Monitoring and logging
* Resource monitoring
* Automated deployment
* Stronger authentication configuration
* Production-ready firewall configuration

## 👨‍💻 Author

**Ali Kamali**

GitHub:

https://github.com/alikamalia1378-svg

