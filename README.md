# TeamSpeak 6 Server on GCP (Docker-Based Setup)

Welcome to your full guide to hosting the **TeamSpeak 6 Server (Beta)** on **Google Cloud Platform (GCP)** using **Docker and Docker Compose**. This setup is secure, persistent, and easy to maintain.

> 🧪 This setup is for the **TeamSpeak 6 Beta Release** — some features may be in development.

---

## 📦 Features

- TeamSpeak 6 Server (latest beta)
- 32-slot free preview license (valid for 2 months)
- Persistent storage using Docker volumes
- GCP firewall configuration
- Supports both TS6 desktop and mobile clients

---

## 📦 Requirements

- A GCP project with billing enabled
- A VM instance (Ubuntu 22.04 LTS recommended)
- Docker & Docker Compose installed

---

## 🚀 Quick Start

### 1. Create a GCP VM Instance

- Go to [GCP VM Instances](https://console.cloud.google.com/compute/instances)
- Click **"Create Instance"**
- Recommended settings:
  - **Name**: `teamspeak6-vm`
  - **Machine type**: `e2-small` or higher
  - **Boot disk**: Ubuntu 22.04 LTS
  - Enable **HTTP** & **HTTPS** (optional)
- Create and note the **external IP address**

---

### 2. Open Required Firewall Ports

Go to **VPC > Firewall rules** → **Create Firewall Rule**

| Field         | Value                        |
|--------------|------------------------------|
| Name          | `teamspeak6-ports`           |
| Direction     | Ingress                      |
| Targets       | All instances in the network |
| Source IP     | `0.0.0.0/0` (allow all)      |
| Protocols     | UDP `9987`, TCP `30033`      |

---

## 🐳 Docker Setup

### 1. SSH into the VM

```bash
gcloud compute ssh teamspeak6-vm
```

### 2. Install Docker & Docker Compose

```bash
sudo apt update && sudo apt install -y docker.io docker-compose
sudo systemctl enable docker && sudo systemctl start docker
```

---

## 🧰 Run TeamSpeak 6 Server

### 1. Create Directory

```bash
mkdir ~/teamspeak6 && cd ~/teamspeak6
```

### 2. Create `docker-compose.yaml`

```yaml
version: '3'

services:
  teamspeak:
    image: teamspeaksystems/teamspeak6-server:latest
    container_name: teamspeak-server
    restart: unless-stopped
    ports:
      - "9987:9987/udp"   # Voice port
      - "30033:30033/tcp" # File transfer
    environment:
      - TSSERVER_LICENSE_ACCEPTED=accept
    volumes:
      - teamspeak-data:/var/tsserver/

volumes:
  teamspeak-data:
```

### 3. Start Server

```bash
sudo docker-compose up -d
```

---

## 🎮 Connect to TeamSpeak 6

- Download the [TS6 Client](https://teamspeak.com/en/downloads)
- Connect using your GCP **external IP** on port **9987**
- Default 32-slot preview license is preloaded (valid for 2 months)

---

## 📄 Resources

- [Official TS6 Website](https://teamspeak.com/)
- [Docker Hub – TS6 Server](https://hub.docker.com/r/teamspeaksystems/teamspeak6-server)
- [Community Forum](https://community.teamspeak.com/)

---

![GitHub issues](https://img.shields.io/github/issues/Mindula-Dilthushan/TeamSpeak-6-Server-on-Google-Cloud-Platform?&labelColor=black&color=eb3b5a&label=Issues&logo=issues&logoColor=black&style=for-the-badge)
![GitHub Contributions](https://img.shields.io/github/contributors/Mindula-Dilthushan/TeamSpeak-6-Server-on-Google-Cloud-Platform?&labelColor=black&color=8854d0&style=for-the-badge)

### License 📝
[![GitHub license](https://img.shields.io/github/license/Mindula-Dilthushan/TeamSpeak-6-Server-on-Google-Cloud-Platform?&labelColor=black&color=3867d6&style=for-the-badge)](https://github.com/Mindula-Dilthushan/TeamSpeak-6-Server-on-Google-Cloud-Platform/blob/master/LICENSE)


<div align="center">

![repo size](https://img.shields.io/github/repo-size/Mindula-Dilthushan/TeamSpeak-6-Server-on-Google-Cloud-Platform?label=Repo%20Size&style=for-the-badge&labelColor=black&color=20bf6b)
![GitHub forks](https://img.shields.io/github/forks/Mindula-Dilthushan/TeamSpeak-6-Server-on-Google-Cloud-Platform?&labelColor=black&color=0fb9b1&style=for-the-badge)
![GitHub stars](https://img.shields.io/github/stars/Mindula-Dilthushan/TeamSpeak-6-Server-on-Google-Cloud-Platform?&labelColor=black&color=f7b731&style=for-the-badge)
![GitHub LastCommit](https://img.shields.io/github/last-commit/Mindula-Dilthushan/TeamSpeak-6-Server-on-Google-Cloud-Platform?logo=github&labelColor=black&color=d1d8e0&style=for-the-badge)

</div>

<div align="center"> 

#### [Mindula Dilthushan Manamperi](http://minduladilthushan.netlify.app/) ^_~
</div>
