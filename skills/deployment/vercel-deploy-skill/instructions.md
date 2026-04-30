# Vercel Deploy Skill

## Purpose
Deploy web applications to Vercel with automatic optimization and best practices.

## Prerequisites
- Vercel account
- Vercel CLI installed (`npm i -g vercel`)
- Project configured for Vercel

## Deployment Process

### 1. Pre-Deployment Checks
- Verify build configuration
- Check environment variables
- Run tests
- Lint code
- Check for security issues

### 2. Build Optimization
- Optimize images
- Minify JavaScript/CSS
- Tree-shake unused code
- Generate source maps
- Configure caching headers

### 3. Deployment
- Create preview deployment (for branches)
- Create production deployment (for main)
- Verify deployment success
- Run smoke tests

### 4. Post-Deployment
- Verify URLs are accessible
- Check performance metrics
- Monitor error rates
- Update deployment status

## Instructions

### Deploy to Preview
```bash
# Deploy current branch to preview
vercel --yes

# Output preview URL
# Run smoke tests on preview
```

### Deploy to Production
```bash
# Deploy to production
vercel --prod --yes

# Verify production deployment
# Monitor for errors
```

### Rollback
```bash
# List recent deployments
vercel ls

# Rollback to previous deployment
vercel rollback [deployment-url]
```

## Example Workflow

```
User: Deploy this Next.js app to Vercel

Codex: [Activates vercel-deploy-skill]

Pre-Deployment Checks:
✓ Build configuration valid
✓ Environment variables set
✓ Tests passing (24/24)
✓ No linting errors
✓ No security vulnerabilities

Build Optimization:
✓ Images optimized (saved 2.3 MB)
✓ JavaScript minified
✓ CSS minified
✓ Tree-shaking applied
✓ Source maps generated

Deploying to Vercel...
✓ Build completed (45s)
✓ Deployment successful

Preview URL: https://my-app-git-feature.vercel.app
Production URL: https://my-app.vercel.app

Post-Deployment Verification:
✓ URLs accessible
✓ Performance score: 95/100
✓ No errors detected

Deployment complete! ✓
```

## Configuration

### vercel.json
```json
{
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "framework": "nextjs",
  "regions": ["iad1"],
  "env": {
    "NODE_ENV": "production"
  },
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        },
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        }
      ]
    }
  ]
}
```

## Best Practices
- Always deploy to preview first
- Run tests before production deployment
- Use environment variables for secrets
- Configure proper caching headers
- Monitor deployment metrics
- Set up automatic deployments for main branch
- Use deployment protection for production

## Troubleshooting

### Build Failures
- Check build logs
- Verify dependencies
- Check Node.js version
- Verify environment variables

### Deployment Failures
- Check Vercel status
- Verify account limits
- Check deployment logs
- Verify domain configuration

### Performance Issues
- Optimize images
- Enable caching
- Use CDN
- Minimize bundle size
