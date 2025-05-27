# Sushi Smash Codebase

## Objective

Smash sushi, dodge junk food, and compete for the highest score before time runs out.

## Gameplay Overview

Items randomly spawn around the board while a shared timer counts down. Players click the sushi sprites to earn points and avoid the junk food that subtracts from their score. When the timer reaches zero, the game tallies the totals and announces the winner.

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

## Game Engine Function Usage

The functions below are specific to Topia's game engine. Each entry explains how to invoke the function and what role it plays during gameplay.

- **addItem(itemType, x, y)** – Spawns a new item into the board at the given coordinates and returns its identifier.
- **addPlayerText(playerId, message, color?)** – Displays floating text above the specified player. The text fades after a short duration.
- **addSprite(id, asset, options)** – Inserts a sprite into the current stage using the provided asset and optional position or settings.
- **attachComponent(entityId, component)** – Attaches a behavior component to an entity so the engine can process it each frame.
- **attachSystem(systemFn)** – Registers a system function with the game manager so it runs during the update loop.
- **boardManager** – Manager object used for board-level state changes such as adding or removing tiles.
- **buttonManager** – Utility that creates and tracks interactive buttons for the user interface.
- **emit(eventName, data)** – Fires a custom event so other scripts or systems can react to `eventName`.
- **endGame()** – Stops the current match and tallies final scores.
- **gameManager** – Provides access to the core game controller and global settings.
- **getComponent(entityId, componentName)** – Retrieves a component instance from the specified entity.
- **getDataObject(key)** – Returns a stored data object associated with the given key.
- **getMyPlayerId()** – Returns the identifier for the current player.
- **getPlayerDetails(playerId)** – Looks up metadata, such as name or score, for a player.
- **getPlayerIds()** – Returns an array containing all active player identifiers.
- **getPosition(entityId)** – Returns the current x and y coordinates of the entity.
- **getRandomUUID()** – Generates a random unique identifier string.
- **getSystem(name)** – Fetches a registered system instance by name.
- **getVariable(name)** – Reads a game variable that was previously stored with `setVariable`.
- **itemClicked(itemId)** – Handler that executes when a player clicks an item.
- **itemManager** – Helper object that maintains item state and performs spawn/removal logic.
- **main()** – Entry point for scripts executed by the game engine.
- **mathRandomInt(min, max)** – Returns a random integer between `min` and `max`, inclusive.
- **onClicked(entityId)** – Callback invoked whenever a sprite or item is clicked by a player.
- **onEvent_addItem(data)** – Runs when the `addItem` event is emitted to spawn new items.
- **onEvent_itemClicked(data)** – Runs when an item click event is received.
- **onEvent_removeItem(data)** – Runs when an item removal event occurs.
- **onHostStart()** – Initialization routine that only executes for the host player when the game begins.
- **onInit()** – Sets up variables and prepares the scene when the game first loads.
- **onPlayerJoined(playerId)** – Executes when a new player joins the session.
- **onPlayerLeft(playerId)** – Executes when a player leaves the session.
- **onSpriteCollisionStart(aId, bId)** – Fired the moment two sprites begin colliding.
- **onStep(delta)** – Runs on every simulation step to update game logic.
- **onVariableChanged_playerQueue(value)** – Responds when the `playerQueue` variable is modified.
- **prepForNextGame()** – Clears temporary variables and readies the engine for another round.
- **putPublicKeyAnalytics(key)** – Records an analytics event for the provided public key.
- **removeFromQueue(playerId)** – Removes the player from any waiting queue.
- **removeItem(itemId)** – Removes an existing item from the board.
- **removePlayerText(playerId)** – Clears floating text that was shown for a player.
- **removeSprite(id)** – Deletes a sprite from the current stage.
- **resetGame()** – Restores all game variables and state back to defaults.
- **setCurrentStage(stageName)** – Switches the active stage or scene.
- **setVariable(name, value)** – Stores a value that can be read later with `getVariable`.
- **startGame()** – Begins a new game session and resets scores.
- **teleportPlayers(position)** – Moves every player to the given position.
- **triggerParticleEffect(effectId, position)** – Plays a particle animation at the specified location.
- **updateDataObject(key, updates)** – Applies updates to a stored data object.
- **updateScore(playerId, amount)** – Recalculates and stores the player's score based on `amount`.
- **updateSprite(id, props)** – Changes properties such as text or position for an existing sprite.
- **utils_getPosition(entityId)** – Convenience wrapper around `getPosition` for scripts.
- **utils_text(value)** – Helper that returns a formatted text string for display.
