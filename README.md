# TeamSpeak 6 Server on Google Cloud Platform

This repository explains how to **self-host a TeamSpeak 6 Server on GCP** using a Virtual Machine (VM) and Docker. It includes a persistent setup with Docker Compose and instructions to make your server available to anyone globally.

> 🧪 This setup is for the **TeamSpeak 6 Beta Release** — some features may be in development.

---

## 📦 Features

- TeamSpeak 6 Server (latest beta)
- 32-slot free preview license (valid for 2 months)
- Persistent storage using Docker volumes
- GCP firewall configuration
- Supports both TS6 desktop and mobile clients

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

### 3. SSH Into Your VM

From GCP Console or CLI:

```bash
gcloud compute ssh teamspeak6-vm
```

### 4. Install Docker & Docker Compose

Update system
```bash
sudo apt update && sudo apt upgrade -y
```

Install Docker
```bash
sudo apt install -y docker.io
```

Start Docker
```bash
sudo systemctl enable docker
```

```bash
sudo systemctl start docker
```

Install Docker Compose V1
```bash
sudo apt install -y docker-compose
```

### 5. Clone This Repo and Start the Server
Clone the repo
```bash
git clone https://github.com/teamspeak/teamspeak6-server.git
```

```bash
cd teamspeak6-server
```

Start the container
```bash
sudo docker-compose up -d
```

## Useful Commands

See logs
```bash
sudo docker-compose logs -f
```

Stop the server
```bash
sudo docker-compose down
```

Restart the server
```bash
sudo docker-compose up -d
```


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
