# Netlify Deploy Skill

## Purpose
Deploy web applications to Netlify with support for serverless functions, forms, and edge deployments.

## Prerequisites
- Netlify account
- Netlify CLI: `npm install -g netlify-cli`
- Authenticated: `netlify login`

## Deployment Process

### 1. Pre-Deployment
```bash
npm test          # run tests
npm run build     # verify build succeeds
netlify status    # confirm auth and site link
```

### 2. Deploy to Preview (Draft)
```bash
netlify deploy --dir=dist
# Returns a unique draft URL for review
```

### 3. Deploy to Production
```bash
netlify deploy --dir=dist --prod
```

### 4. Rollback
```bash
netlify deploy:list          # list deployments
netlify rollback             # rollback to previous
```

## netlify.toml Configuration

```toml
[build]
  command = "npm run build"
  publish = "dist"

[build.environment]
  NODE_VERSION = "20"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"

[functions]
  directory = "netlify/functions"
```

## Netlify Functions (Serverless)

```javascript
// netlify/functions/hello.js
exports.handler = async (event, context) => {
  return {
    statusCode: 200,
    body: JSON.stringify({ message: "Hello from Netlify Functions" })
  };
};
```

## Environment Variables
```bash
# Set via CLI
netlify env:set API_KEY "your-value"

# Or via netlify.toml (non-secret only)
[build.environment]
  NEXT_PUBLIC_API_URL = "https://api.example.com"
```

## Best Practices
- Always deploy to draft first, verify, then promote to production
- Use branch deploys for feature branches
- Store secrets via `netlify env:set`, never in code
- Enable deploy notifications in Netlify dashboard
- Use `_redirects` or `netlify.toml` for SPA routing
