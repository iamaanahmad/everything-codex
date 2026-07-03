# Game Development Example — Codex Memory

## Project
Browser 2D game with TypeScript + HTML5 Canvas. ECS architecture.

## Key Commands
```bash
npm run dev      # Vite dev server (port 5173)
npm test         # vitest (game logic only)
npm run build    # production build
```

## Architecture
- Entity-Component-System (ECS) pattern
- `Entity` base class in `src/engine/Entity.ts`
- Systems process entities each frame: Physics → Collision → Render
- Scenes manage entity lifecycle: `MenuScene`, `GameScene`, `GameOverScene`

## Game Loop
- Fixed at 60fps target via `requestAnimationFrame`
- `delta` time in seconds passed to all `update(delta)` calls
- Never use `setTimeout` for game timing — always use delta time

## Testing
- Test game logic (physics calculations, collision detection) with Vitest
- Do NOT test rendering or Canvas API — mock it
- Test files: `src/systems/*.test.ts`

## Assets
- Sprites in `src/assets/sprites/` (PNG, max 512x512)
- Sounds in `src/assets/sounds/` (MP3)
- Load via `AssetLoader` in `src/engine/AssetLoader.ts`
