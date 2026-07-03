# Docker Deploy Skill

## Purpose
Containerize applications with optimized multi-stage Dockerfiles and deploy with Docker Compose or to a registry.

## Dockerfile Templates

### Node.js (Multi-stage)
```dockerfile
# Build stage
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

# Runtime stage
FROM node:20-alpine AS runner
WORKDIR /app
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
COPY --from=builder /app/node_modules ./node_modules
COPY . .
USER appuser
EXPOSE 3000
CMD ["node", "src/index.js"]
```

### Python (Multi-stage)
```dockerfile
FROM python:3.12-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir --user -r requirements.txt

FROM python:3.12-slim AS runner
WORKDIR /app
COPY --from=builder /root/.local /root/.local
COPY . .
ENV PATH=/root/.local/bin:$PATH
EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

## Docker Compose

```yaml
# docker-compose.yml
services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - DATABASE_URL=${DATABASE_URL}
    depends_on:
      db:
        condition: service_healthy
    restart: unless-stopped

  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_DB: myapp
      POSTGRES_USER: ${DB_USER}
      POSTGRES_PASSWORD: ${DB_PASSWORD}
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${DB_USER}"]
      interval: 10s
      timeout: 5s
      retries: 5

volumes:
  postgres_data:
```

## Build & Deploy Commands

```bash
# Build image
docker build -t my-app:latest .

# Run locally
docker compose up -d

# View logs
docker compose logs -f app

# Push to registry
docker tag my-app:latest registry.example.com/my-app:latest
docker push registry.example.com/my-app:latest

# Deploy update (zero-downtime)
docker compose pull && docker compose up -d --no-deps app
```

## .dockerignore
```
node_modules
.git
.env
*.log
dist
coverage
```

## Best Practices
- Always use multi-stage builds to minimize image size
- Run as non-root user in production
- Never copy `.env` files into the image — use runtime env vars
- Pin base image versions (e.g., `node:20-alpine`, not `node:latest`)
- Use health checks in Compose for dependency ordering
- Scan images: `docker scout cves my-app:latest`
