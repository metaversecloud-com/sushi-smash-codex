# Sushi Smash Modding Tutorial

This guide explains how to remix **Sushi Smash** by editing the game scripts and JSON specification. It references examples from `WALKTHROUGH.md` and `FUNCTION_REFERENCE.md`.

## 1. Getting Started

All gameplay logic lives in `Sushi Smash_.json`. Open this file in a text editor to add or modify scripts. The [`README.md`](README.md) and [`WALKTHROUGH.md`](WALKTHROUGH.md) documents provide background on how the existing code works.

The engine exposes many helper functions for controlling sprites, tracking players, and reacting to events. See [`FUNCTION_REFERENCE.md`](FUNCTION_REFERENCE.md) for the complete API list.

## 2. Adding New Item Types

Items are spawned through `addItem()` which checks the game timer before creating a sprite:

```javascript
// from WALKTHROUGH.md
// gameManager.prototype.addItem
var gameTimer = stateManager.getVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'gameTimer');
if (!pseudoProxy.isGameInProress || gameTimer === 0)
    return;
```

To create a new item type, define a new sprite asset in the JSON and call `addItem()` with the desired coordinates:

```javascript
// example modification
scriptManager.emit({ _rs: _rs, _rsId: _rsId, as: false }, 'addItem', {
    itemType: 'goldenSushi',
    x: 50,
    y: 20,
});
```

Use `attachComponent()` if the item needs custom behavior when clicked.

## 3. Updating the Scoreboard

Scores are shown using text sprites. The helper `updateScore()` updates the text after each item click:

```javascript
// from WALKTHROUGH.md
utils_text.prototype.updateScore = function (_a) {
    var playerId = _a.playerId, score = _a.score;
    spriteManager.updateSprite({ _rs: _rs, _rsId: _rsId, as: false }, `${playerId}_score`, {
        text: `Score: ${score}`,
    });
};
```

You can customize the formatting or add extra information:

```javascript
// example modification
spriteManager.updateSprite({ _rs: _rs, _rsId: _rsId, as: false }, `${playerId}_score`, {
    text: `🍣 Points: ${score}`,
    color: 'yellow',
});
```

## 4. Changing Game Flow

The match begins with `startGame()` which resets state and moves players into position. You can adjust the initial timer or teleport locations here:

```javascript
// from FUNCTION_REFERENCE.md
gameManager.prototype.startGame = function () {
    pseudoProxy.resetGame({ _rs: _rs, _rsId: _rsId, as: false });
    // additional setup...
};
```

For example, to start players closer together:

```javascript
playerManager.teleportPlayers(playerIds, {
  distributionType: 'area',
  positionX: 100,
  positionY: 20,
  height: 30,
});
```

## 5. Custom Win Conditions

`endGame()` calculates who won and triggers particle effects. Modify this function to change how a winner is chosen or to add bonus effects:

```javascript
// snippet from FUNCTION_REFERENCE.md
if (winnerId) {
    text = `${playerManager.getPlayerDetails({ _rs: _rs, _rsId: _rsId, as: false }, winnerId).nameplate} wins!`;
    integrationsManager.triggerParticleEffect({ _rs: _rs, _rsId: _rsId, as: false }, {
        interactivePublicKey: pseudoProxy.interactivePublicKey,
        duration: 4,
        playerId: winnerId,
        followPlayerId: winnerId,
    });
}
```

To add a sudden‑death overtime, insert logic that checks if scores are tied and set a new timer instead of immediately ending the match.

## 6. Saving Persistent Data

Use `updateDataObject()` to store results that persist between games:

```javascript
// from FUNCTION_REFERENCE.md
integrationsManager.updateDataObject({ _rs: _rs, _rsId: _rsId, as: false }, {
    interactivePublicKey: pseudoProxy.interactivePublicKey,
    scope: 'WORLD',
    payload: dataObject,
});
```

Store high scores or custom settings here to load them the next time the map runs.

---

With these examples you can tweak Sushi Smash to create new rules, items, and visuals. Explore the scripts in `Sushi Smash_.json` alongside the API reference to keep experimenting!
