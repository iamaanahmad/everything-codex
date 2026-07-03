# Codex Project Rules

These rules are automatically applied to every Codex CLI session in this project.

## Code Style
- Follow existing code conventions in the file you're editing
- Use TypeScript strict mode — no implicit `any`
- Prefer `const` over `let`; never use `var`
- Use named exports, not default exports (except for pages/routes)
- Keep functions under 30 lines; extract if longer

## Git
- Commit messages must follow Conventional Commits: `type(scope): description`
- Valid types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`, `perf`
- Never force-push to `main` or `develop`
- Branch naming: `feature/`, `bugfix/`, `hotfix/`, `refactor/`, `docs/`

## Testing
- Write tests for all new functions and bug fixes
- Minimum 80% coverage for new code
- Test file naming: `*.test.ts` co-located with source, or in `__tests__/`
- Use `describe` blocks to group related tests

## Security
- Never hardcode secrets, API keys, or credentials
- Always use environment variables for sensitive config
- Validate and sanitize all user inputs
- Use parameterized queries — never string-concatenate SQL

## Dependencies
- Check `npm audit` before adding new packages
- Prefer well-maintained packages (> 1M weekly downloads, updated in last 6 months)
- Avoid packages that pull in large transitive dependency trees unnecessarily

## What Codex Should Always Do
- Run `npm test` after making code changes
- Run `npm run lint` and fix any errors introduced
- Check that TypeScript compiles without errors: `npx tsc --noEmit`
- Ask before making changes outside the current task scope
