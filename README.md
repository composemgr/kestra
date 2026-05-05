## 👋 Welcome to kestra 🚀

Infinitely scalable orchestration and scheduling platform

## 📋 Description

Infinitely scalable orchestration and scheduling platform

## 🚀 Services

- **app**: kestra/kestra:latest

### Infrastructure Components

- **db**: Postgres database


## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/kestra/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/kestra" ~/.local/srv/docker/kestra
cd ~/.local/srv/docker/kestra
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install kestra
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
DB_CREATE_DATABASE_NAME=kestra
```

See `docker-compose.yaml` for complete list of configurable options.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:59057

## 📂 Volumes

- `./volumes/data/tmp` - Data storage
- `./volumes/data/kestra` - Data storage
- `./volumes/data/db/postgres/kestra` - Data storage

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose logs -f app
```

## 🛠️ Management

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Update to latest images
docker compose pull && docker compose up -d

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
