# Game Development Example

A browser-based 2D game built with TypeScript and HTML5 Canvas — demonstrating everything-codex patterns for game development.

## Stack
- **Language**: TypeScript
- **Renderer**: HTML5 Canvas API
- **Physics**: Custom (no external engine)
- **Build**: Vite
- **Testing**: Vitest (game logic only — no DOM tests)

## Quick Start

```bash
npm install
npm run dev
```

Open `http://localhost:5173` to play.

## Project Structure

```
src/
├── engine/          # Core game engine
│   ├── Game.ts      # Main game loop (requestAnimationFrame)
│   ├── Scene.ts     # Scene management
│   ├── Entity.ts    # Base entity class
│   └── Renderer.ts  # Canvas rendering
├── entities/        # Game objects
│   ├── Player.ts
│   ├── Enemy.ts
│   └── Projectile.ts
├── systems/         # ECS-style systems
│   ├── PhysicsSystem.ts
│   ├── CollisionSystem.ts
│   └── InputSystem.ts
├── scenes/          # Game scenes
│   ├── MenuScene.ts
│   ├── GameScene.ts
│   └── GameOverScene.ts
├── assets/          # Sprites, sounds (loaded at runtime)
└── main.ts          # Entry point
```

## Game Loop

```typescript
// Engine/Game.ts pattern
class Game {
  private lastTime = 0;

  start() {
    requestAnimationFrame(this.loop.bind(this));
  }

  private loop(timestamp: number) {
    const delta = (timestamp - this.lastTime) / 1000; // seconds
    this.lastTime = timestamp;

    this.update(delta);
    this.render();

    requestAnimationFrame(this.loop.bind(this));
  }
}
```

## Codex Skills Used

- `tdd-workflow-skill` — game logic (physics, collision) built test-first
- `debugging-skill` — frame-rate and collision debugging
- `refactoring-skill` — ECS refactor from monolithic game object
- `image-generation-skill` — sprite assets generated with AI

## Scripts

```bash
npm run dev      # dev server with HMR
npm test         # run game logic tests
npm run build    # production build to dist/
npm run preview  # preview production build
```

## Multi-Agent Workflow Used

This example was built using the `feature-development` workflow:
- **Backend Agent** → game engine and systems
- **Frontend Agent** → scenes and UI
- **Testing Agent** → physics and collision tests
- **Documentation Agent** → this README and inline docs
