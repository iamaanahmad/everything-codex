# README Generator Skill

## Purpose
Analyze a project and generate a comprehensive, well-structured README that helps developers onboard quickly.

## Process

### 1. Analyze Project
```bash
# Detect language/framework
cat package.json | jq '.dependencies'
ls -la

# Find existing docs
find . -name "*.md" -not -path "*/node_modules/*"

# Check scripts
cat package.json | jq '.scripts'
```

### 2. Generate README

## README Template

```markdown
# Project Name

> One-line description of what this project does.

[![CI](https://github.com/org/repo/actions/workflows/ci.yml/badge.svg)](...)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Overview

2-3 sentences explaining the problem this solves and who it's for.

## Features

- **Feature 1** — brief description
- **Feature 2** — brief description
- **Feature 3** — brief description

## Quick Start

### Prerequisites
- Node.js v20+
- PostgreSQL 16+

### Installation

```bash
git clone https://github.com/org/repo.git
cd repo
npm install
cp .env.example .env   # fill in your values
npm run db:migrate
npm run dev
```

Open http://localhost:3000

## Usage

### Basic Example

```javascript
import { MyClient } from 'my-package';

const client = new MyClient({ apiKey: process.env.API_KEY });
const result = await client.doSomething({ input: 'value' });
console.log(result);
```

### Configuration

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `API_KEY` | Yes | — | Your API key |
| `PORT` | No | `3000` | Server port |
| `DATABASE_URL` | Yes | — | PostgreSQL connection string |

## Development

```bash
npm run dev        # start dev server with hot reload
npm test           # run tests
npm run test:watch # watch mode
npm run lint       # lint code
npm run build      # production build
```

## Project Structure

```
src/
├── api/          # Route handlers
├── services/     # Business logic
├── models/       # Database models
├── utils/        # Shared utilities
└── index.ts      # Entry point
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). PRs welcome!

## License

MIT — see [LICENSE](LICENSE)
```

## Sections to Include Based on Project Type

| Project Type | Extra Sections |
|-------------|---------------|
| CLI tool | `Usage` with all flags/commands |
| Library/SDK | `API Reference`, `Examples` |
| Web app | `Screenshots`, `Demo link` |
| API service | Link to OpenAPI docs |
| Monorepo | `Packages` table with links |

## Best Practices
- Lead with what the project does, not how it works
- Include a working Quick Start that takes < 5 minutes
- Use real code examples, not pseudocode
- Keep the README scannable — use headers, bullets, tables
- Add badges for CI status, version, and license
- Update README as part of every feature PR
