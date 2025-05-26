# Sushi Smash Codebase

This repository holds the code specification for the **Sushi Smash** game built on Topia's experience engine.

Topia's experience engine loads this JSON specification and translates it into runnable TypeScript during deployment. The engine runs entirely on Topia's multiplayer infrastructure and does not require a custom backend. Gameplay runs in canvas with built‑in WebRTC networking, collision, and physics features.

The single file `Sushi Smash_.json` defines:

- Game metadata such as name, size, category, and timestamps
- Event definitions and variables for in‑game actions
- Sprite assets and positions
- Embedded script logic that updates player scores and game state

For example, when a player's score changes, the following script snippet updates the on‑screen score display:

```javascript
score = _a.score;
spriteManager.updateSprite({ _rs: _rs, _rsId: _rsId, as: false }, `${playerId}_score`, {
    text: `Score: ${score}`,
});
```

This repository contains no other files.
