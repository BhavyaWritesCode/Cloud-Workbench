# ☁️ Cloud Workbench

A portable **Developer Productivity Platform** built with Docker. Spin up a full development environment with a single command — browser-based IDE, Git hosting, database, and team chat, all running locally.

---

## 🧱 Services

| Service | Description | URL |
|---|---|---|
| **VS Code Server** | Browser-based code editor | `http://localhost/code` |
| **Gitea** | Self-hosted Git repository hosting | `http://localhost:3000` |
| **PostgreSQL** | Sandbox database for development | `localhost:5432` |
| **Mattermost** | Self-hosted team chat | `http://localhost:8065` |
| **Nginx** | Reverse proxy and entry point | `http://localhost` |

---

## 🚀 Quick Start

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/cloud-workbench.git
cd cloud-workbench
```

### 2. Set up environment variables
```bash
cp .env.example .env
```
Open `.env` and replace all `CHANGE_ME` values with your own passwords.

### 3. Start the platform
```bash
docker-compose up -d
```

That's it! All 5 containers will start automatically.

---

## 🛠️ Useful Commands

```bash
# start everything
docker-compose up -d

# check status of all containers
docker-compose ps

# view logs of a specific service
docker-compose logs mattermost

# restart a single service
docker-compose restart vscode

# stop everything (data is preserved)
docker-compose down

# stop everything and delete all data
docker-compose down -v
```

---

## 📁 Project Structure

```
cloud-workbench/
├── nginx/
│   └── nginx.conf        # reverse proxy routing rules
├── .env                  # your credentials (never commit this)
├── .env.example          # credentials template for others
├── .gitignore
└── docker-compose.yml    # orchestrates all containers
```

---

## 🔗 Docker Network

All containers communicate over a shared Docker bridge network called `dev-network`. Services can reach each other by container name (e.g. Gitea connects to Postgres at `postgres:5432`).

## 💾 Persistent Storage

Data is stored in Docker volumes and survives container restarts:

| Volume | Data |
|---|---|
| `vscode-data` | Project files |
| `gitea-data` | Git repositories and settings |
| `postgres-data` | Database tables and records |
| `mattermost-data` | Messages and channels |

---

## 📋 Requirements

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- 4GB RAM minimum recommended
- Ports `80`, `3000`, `5432`, `8065`, `222` available on your machine

---
