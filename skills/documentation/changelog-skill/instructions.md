# Changelog Skill

## Purpose
Generate and maintain a `CHANGELOG.md` following [Keep a Changelog](https://keepachangelog.com) format, driven by conventional commits.

## Process

### 1. Collect Commits Since Last Release
```bash
# Get last tag
LAST_TAG=$(git describe --tags --abbrev=0)

# List commits since last tag
git log $LAST_TAG..HEAD --oneline --no-merges
```

### 2. Parse Conventional Commits

| Prefix | Changelog Section |
|--------|------------------|
| `feat:` | Added |
| `fix:` | Fixed |
| `perf:` | Changed |
| `refactor:` | Changed |
| `docs:` | Changed |
| `BREAKING CHANGE:` | ⚠ Breaking Changes |
| `chore:`, `ci:`, `test:` | (omit from changelog) |

### 3. Generate Entry

## CHANGELOG.md Format

```markdown
# Changelog

All notable changes to this project will be documented in this file.
Format: [Keep a Changelog](https://keepachangelog.com) | [Semantic Versioning](https://semver.org)

## [Unreleased]

## [2.1.0] - 2025-05-30

### ⚠ Breaking Changes
- `createUser()` now requires `role` parameter (previously optional)

### Added
- User role management with RBAC support (#142)
- Export data to CSV from dashboard (#138)
- Dark mode support (#129)

### Fixed
- Login redirect loop when session expires (#145)
- Mobile layout overflow on small screens (#141)
- Memory leak in WebSocket connection handler (#139)

### Changed
- Improved search performance by 3x with new indexing strategy (#140)
- Updated dependencies: React 19, TypeScript 5.5

## [2.0.0] - 2025-04-15

### ⚠ Breaking Changes
- Dropped Node.js 18 support — requires Node.js 20+
- Renamed `config.apiUrl` to `config.baseUrl`

### Added
- Multi-tenant support
- OAuth2 login (Google, GitHub)

[Unreleased]: https://github.com/org/repo/compare/v2.1.0...HEAD
[2.1.0]: https://github.com/org/repo/compare/v2.0.0...v2.1.0
[2.0.0]: https://github.com/org/repo/compare/v1.0.0...v2.0.0
```

### 4. Determine Version Bump (Semantic Versioning)
- Any `BREAKING CHANGE` → **major** bump
- Any `feat:` → **minor** bump
- Only `fix:`, `perf:`, `docs:` → **patch** bump

### 5. Update Files
```bash
# Update CHANGELOG.md
# Update package.json version
npm version minor --no-git-tag-version

# Commit and tag
git add CHANGELOG.md package.json
git commit -m "chore: release v2.1.0"
git tag v2.1.0
git push && git push --tags
```

## Best Practices
- Write changelog entries for humans, not machines — summarize the impact
- Always link to the relevant issue or PR number
- Highlight breaking changes prominently
- Keep an `[Unreleased]` section at the top, updated with every merged PR
- Never edit old release entries
