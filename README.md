# Webhook Client

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub-rocardho%2Fwebhook--client-blue)](https://hub.docker.com/r/rocardho/webhook-client)

A minimal Express.js server that logs incoming webhook requests to the console, with Docker support.

## Features
- POST `/webhook` endpoint that logs headers + body
- Health check at `/health`
- Auto-reload in development (using Nodemon)
- Dockerized for easy deployment

## 🚀 Quick Deployment (Docker Hub)

Pre-built image available on Docker Hub:

```bash
# Pull and run the latest version
docker run -p 3000:3000 -d rocardho/webhook-client:latest
```

```bash
# Or specify a version
docker run -p 3000:3000 -d rocardho/webhook-client:1.0.0
```

## Quick Start

### Without Docker
1. Install dependencies:
   ```bash
   npm install
2. Start the server:
   ```bash
    npm start       # Production
    npm run dev     # Development (auto-reload)

## With Docker
1. Build the image::
   ```bash
   docker build -t webhook-client .
2. Run the container:
   ```bash
    docker run -p 3000:3000 -d --name webhook-client webhook-client

## Usage
Send a test webhook:
```bash
curl -X POST http://localhost:3000/webhook \
  -H "Content-Type: application/json" \
  -d '{"event": "test", "data": {"key": "value"}}'
```

## View Logs
```bash
# Local
npm start

# Docker
docker logs -f webhook-client
```

## Endpoints
| Route       | Method | Description                          |
|-------------|--------|--------------------------------------|
| `/webhook`  | POST   | Receives and logs webhook data       |
| `/health`   | GET    | Returns `{"status":"healthy"}`       |