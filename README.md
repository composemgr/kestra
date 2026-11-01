## 👋 Welcome to kestra 🚀

Infinitely scalable orchestration and scheduling platform

## 📋 Description

Kestra is an open-source data orchestration and scheduling platform. It runs
workflows declaratively, stores them in Postgres, and exposes a web UI and REST
API for building, monitoring and running them.

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
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr

```bash
composemgr install kestra
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
APP_ADMIN_USER=admin
APP_ADMIN_PASS=replace-with-a-random-password
DB_USER_NAME=kestra
DB_USER_PASS=replace-with-a-random-password
DB_CREATE_DATABASE_NAME=kestra
```

See `docker-compose.yaml` for complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64222` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

The proxy variants publish no host ports. The app is reachable only through the
proxy network, and the Postgres service stays internal to the project network in
every variant.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:64222

## 📂 Volumes

- `./volumes/data/tmp` - Kestra working and temporary task directory
- `./volumes/data/kestra` - Workflow storage
- `./var/run/docker.sock` - Docker socket, mounted read-write so Docker tasks work
- `./volumes/db/postgres/kestra` - Postgres database data

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

The Docker socket mount gives the container control of the Docker daemon. Only
expose the stack to trusted networks, and prefer a dedicated socket proxy if you
do not need Docker tasks.

## 🔍 Logging

```shell
docker compose --env-file .env logs -f app
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
