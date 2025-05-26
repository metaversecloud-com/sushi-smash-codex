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

## Function Reference

Below is an overview of all unique functions referenced inside `Sushi Smash_.json`.
Each plays a role in managing gameplay, updating sprites, or handling player
interactions.

- **_getPsuedoProxy** – creates an internal proxy object used by the engine.
- **addItem** – spawns a new item into the game board.
- **addPlayerText** – displays floating text for a specific player.
- **addSprite** – inserts a sprite into the current stage.
- **attachComponent** – attaches a component to an entity or sprite.
- **attachSystem** – registers a system with the game manager.
- **boardManager** – utility for board‑level state updates.
- **buttonManager** – manages interactive buttons.
- **concat** – joins arrays or strings within script logic.
- **constructor** – initializes object instances.
- **emit** – fires a custom event.
- **endGame** – stops the game and tallies results.
- **filter** – filters lists based on a condition.
- **forEach** – iterates over arrays in scripts.
- **gameManager** – provides access to the central game controller.
- **getComponent** – retrieves a component from an entity.
- **getDataObject** – fetches stored data for a game object.
- **getMyPlayerId** – returns the current player's identifier.
- **getPlayerDetails** – looks up metadata for a player.
- **getPlayerIds** – returns all player identifiers in the session.
- **getPosition** – obtains an entity's current position.
- **getRandomUUID** – generates a random unique identifier.
- **getSystem** – fetches a registered system instance.
- **getVariable** – reads a game variable's value.
- **indexOf** – searches for an element within an array.
- **itemClicked** – handler triggered when an item is clicked.
- **itemManager** – helper that maintains item state.
- **log** – outputs a message for debugging.
- **main** – main entry point for scripts.
- **mathRandomInt** – returns a random integer.
- **onClicked** – event triggered when a sprite or item is clicked.
- **onEvent_addItem** – callback for the `addItem` event.
- **onEvent_itemClicked** – callback when an item is selected.
- **onEvent_removeItem** – callback for removing an item.
- **onHostStart** – initialization routine run by the host.
- **onInit** – game initialization function.
- **onPlayerJoined** – executes when a player enters the game.
- **onPlayerLeft** – executes when a player leaves the game.
- **onSpriteCollisionStart** – fired when two sprites collide.
- **onStep** – runs on every simulation step.
- **onVariableChanged_playerQueue** – handles changes to the player queue.
- **prepForNextGame** – resets variables for another round.
- **push** – adds an element to an array.
- **putPublicKeyAnalytics** – records analytics for public keys.
- **removeFromQueue** – deletes a player from the queue.
- **removeItem** – removes an item from the board.
- **removePlayerText** – clears floating player text.
- **removeSprite** – deletes a sprite from the stage.
- **resetGame** – clears game state back to defaults.
- **setCurrentStage** – switches the active stage.
- **setVariable** – sets a game variable's value.
- **splice** – modifies arrays by removing or inserting entries.
- **startGame** – begins a new game session.
- **teleportPlayers** – moves all players to a new location.
- **toObject** – converts data into an object form.
- **triggerParticleEffect** – plays a particle effect animation.
- **updateDataObject** – updates stored data for an object.
- **updateScore** – recalculates and stores a player's score.
- **updateSprite** – modifies sprite properties like text or position.
- **utils_getPosition** – utility wrapper for retrieving positions.
- **utils_text** – helper for generating text strings.
