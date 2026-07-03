# Cloudflare Deploy Skill

## Purpose
Deploy static sites to Cloudflare Pages and serverless logic to Cloudflare Workers using Wrangler CLI.

## Prerequisites
- Cloudflare account
- Wrangler CLI: `npm install -g wrangler`
- Authenticated: `wrangler login`

## Cloudflare Pages Deployment

### Deploy
```bash
# Build first
npm run build

# Deploy to Pages
wrangler pages deploy dist --project-name=my-app

# Preview URL returned automatically
```

### wrangler.toml (Pages)
```toml
name = "my-app"
pages_build_output_dir = "dist"
compatibility_date = "2024-01-01"

[vars]
ENVIRONMENT = "production"
```

## Cloudflare Workers Deployment

### Worker Script
```javascript
// src/worker.js
export default {
  async fetch(request, env, ctx) {
    const url = new URL(request.url);

    if (url.pathname === "/api/hello") {
      return new Response(JSON.stringify({ message: "Hello from the edge!" }), {
        headers: { "Content-Type": "application/json" }
      });
    }

    return new Response("Not Found", { status: 404 });
  }
};
```

### Deploy Worker
```bash
wrangler deploy
```

### wrangler.toml (Worker)
```toml
name = "my-worker"
main = "src/worker.js"
compatibility_date = "2024-01-01"

[vars]
API_URL = "https://api.example.com"

[[kv_namespaces]]
binding = "MY_KV"
id = "your-kv-namespace-id"
```

## Environment Variables (Secrets)
```bash
# Set secrets (encrypted, not in wrangler.toml)
wrangler secret put API_KEY

# List secrets
wrangler secret list
```

## Rollback
```bash
# List deployments
wrangler deployments list

# Rollback to previous
wrangler rollback
```

## Best Practices
- Use Workers KV or D1 for edge-persistent data
- Keep Worker bundles under 1MB (free tier limit)
- Use `wrangler dev` for local testing before deploy
- Store secrets with `wrangler secret put`, never in code
- Use Cloudflare Analytics to monitor edge performance
