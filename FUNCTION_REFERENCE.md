# Sushi Smash Function Reference

This document describes each game function defined in `Sushi Smash_.json`. Each section presents a snippet from the JSON and explains the function.

## addItem

```javascript
"gameId":"iyIxxiVJASPqGIHVbt6i","name":"addItem","description":"","type":"INPUT","gameEventId":"addI
```
Spawns a new item into the board at the given coordinates and returns its identifier.

## addPlayerText

```javascript
t6i","methodSignatures":[{"methodName":"addPlayerText","parameters":[{"label":"__0","type":"{ isPlay
```
Displays floating text above the specified player. The text fades after a short duration.

## addSprite

```javascript
upiedPositions });\n\n    spriteManager.addSprite(`${this.theme}${spriteId}`, {\n      uniqueId,\n  
```
Inserts a sprite into the current stage using the provided asset and optional position or settings.

## attachComponent

```javascript
sitionY: y,\n    });\n    scriptManager.attachComponent({\n      objectUniqueId: uniqueId,\n      co
```
Attaches a behavior component to an entity so the engine can process it each frame.

## attachSystem

```javascript
ublicKey',\n    );\n\n    scriptManager.attachSystem({ scriptId: 'utils_getPosition' });\n  }\n\n  o
```
Registers a system function with the game manager so it runs during the update loop.

## boardManager

```javascript
,"scriptType":"component","scriptName":"boardManager","className":"boardManager","contentUpdatedAtIS
```
Manager object used for board-level state changes such as adding or removing tiles.

## buttonManager

```javascript
"}],"scriptType":"system","scriptName":"buttonManager","className":"buttonManager","contentUpdatedAt
```
Utility that creates and tracks interactive buttons for the user interface.

## emit

```javascript
this.itemTimer = 0;\n\n    eventManager.emit('itemClicked', {\n      isBad,\n      isPlayer1,\n     
```
Fires a custom event so other scripts or systems can react to `eventName`.

## endGame

```javascript
meters":[],"isAsync":true,"methodName":"endGame","returnType":"Promise<void>"},{"parameters":[],"isA
```
Stops the current match and tallies final scores.

## gameManager

```javascript
"}],"scriptType":"system","scriptName":"gameManager","className":"gameManager","contentUpdatedAtISO"
```
Provides access to the core game controller and global settings.

## getComponent

```javascript
  });\n\n    const item = scriptManager.getComponent({\n      objectUniqueId: uniqueId,\n      compo
```
Retrieves a component instance from the specified entity.

## getDataObject

```javascript
   let dataObject = integrationsManager.getDataObject({\n      interactivePublicKey: this.interactiv
```
Returns a stored data object associated with the given key.

## getMyPlayerId

```javascript
t(){\n    // const ids = [playerManager.getMyPlayerId()]\n    // console.log(\"onSpriteCollisionStar
```
Returns the identifier for the current player.

## getPlayerDetails

```javascript
 {\n    const profileId = playerManager.getPlayerDetails(playerId)?.profileId;\n\n    integrationsMa
```
Looks up metadata, such as name or score, for a player.

## getPlayerIds

```javascript
s\n    // let playerIds = playerManager.getPlayerIds();\n    // playerIds = playerIds.filter(\n    /
```
Returns an array containing all active player identifiers.

## getPosition

```javascript
Manager.attachSystem({ scriptId: 'utils_getPosition' });\n  }\n\n  onInit() {\n    this.resetGame();
```
Returns the current x and y coordinates of the entity.

## getRandomUUID

```javascript
mIsBad ? 8 : 12);\n    const uniqueId = getRandomUUID();\n\n    const { position, x, y } = scriptMan
```
Generates a random unique identifier string.

## getSystem

```javascript
n    const main = scriptManager\n      .getSystem({ systemName: 'main' })\n      .startGame({ theme 
```
Fetches a registered system instance by name.

## getVariable

```javascript
his.interactivePublicKey = stateManager.getVariable(\n      'interactivePublicKey',\n    );\n\n    s
```
Reads a game variable that was previously stored with `setVariable`.

## itemClicked

```javascript
"gameId":"iyIxxiVJASPqGIHVbt6i","name":"itemClicked","description":"","type":"INPUT","gameEventId":"
```
Handler that executes when a player clicks an item.

## itemManager

```javascript
queId: uniqueId,\n      componentName: 'itemManager',\n      scriptId: 'itemManager',\n    });\n\n  
```
Helper object that maintains item state and performs spawn/removal logic.

## main

```javascript
heme = this.sprite.uniqueId;\n    const main = scriptManager\n      .getSystem({ systemName: 'main' 
```
Entry point for scripts executed by the game engine.

## mathRandomInt

```javascript
nt > 3) return;\n\n    const spriteId = mathRandomInt(1, lastItemIsBad ? 8 : 12);\n    const uniqueI
```
Returns a random integer between `min` and `max`, inclusive.

## onClicked

```javascript
atures":[{"parameters":[],"methodName":"onClicked","returnType":"void"}],"scriptType":"system","scri
```
Callback invoked whenever a sprite or item is clicked by a player.

## onEvent_addItem

```javascript
"}],"returnType":"void"},{"methodName":"onEvent_addItem","parameters":[{"label":"__0","type":"{ isPl
```
Runs when the `addItem` event is emitted to spawn new items.

## onEvent_itemClicked

```javascript
"}],"returnType":"void"},{"methodName":"onEvent_itemClicked","parameters":[{"label":"__0","type":"{ 
```
Runs when an item click event is received.

## onEvent_removeItem

```javascript
"}],"returnType":"void"},{"methodName":"onEvent_removeItem","parameters":[{"label":"__0","type":"{ i
```
Runs when an item removal event occurs.

## onHostStart

```javascript
atures":[{"parameters":[],"methodName":"onHostStart","returnType":"void"},{"methodName":"onVariableC
```
Initialization routine that only executes for the host player when the game begins.

## onInit

```javascript
atures":[{"parameters":[],"methodName":"onInit","returnType":"void"},{"parameters":[],"methodName":"
```
Sets up variables and prepares the scene when the game first loads.

## onPlayerJoined

```javascript
":"void"},{"isAsync":true,"methodName":"onPlayerJoined","parameters":[{"label":"__0","type":"{ playe
```
Executes when a new player joins the session.

## onPlayerLeft

```javascript
e<void>"},{"isAsync":true,"methodName":"onPlayerLeft","parameters":[{"label":"__0","type":"{ playerI
```
Executes when a player leaves the session.

## onSpriteCollisionStart

```javascript
:"void"},{"parameters":[],"methodName":"onSpriteCollisionStart","returnType":"void"}],"scriptType":"
```
Fired the moment two sprites begin colliding.

## onStep

```javascript
meters":[],"isAsync":true,"methodName":"onStep","returnType":"Promise<void>"},{"parameters":[],"isAs
```
Runs on every simulation step to update game logic.

## onVariableChanged_playerQueue

```javascript
rt","returnType":"void"},{"methodName":"onVariableChanged_playerQueue","parameters":[{"label":"__0",
```
Responds when the `playerQueue` variable is modified.

## prepForNextGame

```javascript
meters":[],"isAsync":true,"methodName":"prepForNextGame","returnType":"Promise<void>"},{"parameters"
```
Clears temporary variables and readies the engine for another round.

## putPublicKeyAnalytics

```javascript
?.profileId;\n\n    integrationsManager.putPublicKeyAnalytics({\n      interactivePublicKey: this.in
```
Records an analytics event for the provided public key.

## removeFromQueue

```javascript
e<void>"},{"isAsync":true,"methodName":"removeFromQueue","parameters":[{"label":"__0","type":"{ play
```
Removes the player from any waiting queue.

## removeItem

```javascript
"gameId":"iyIxxiVJASPqGIHVbt6i","name":"removeItem","description":"","type":"INPUT","gameEventId":"r
```
Removes an existing item from the board.

## removePlayerText

```javascript
"}],"returnType":"void"},{"methodName":"removePlayerText","parameters":[{"label":"__0","type":"{ pla
```
Clears floating text that was shown for a player.

## removeSprite

```javascript
rId: number;\n  }) {\n    spriteManager.removeSprite(itemId);\n\n    const occupiedPositions = isPla
```
Deletes a sprite from the current stage.

## resetGame

```javascript
<void>"},{"parameters":[],"methodName":"resetGame","returnType":"void"},{"isAsync":true,"methodName"
```
Restores all game variables and state back to defaults.

## setCurrentStage

```javascript
: 'gameManager' });\n\n    stageManager.setCurrentStage('sushi');\n\n    spriteManager.addSprite('su
```
Switches the active stage or scene.

## setVariable

```javascript
player2_id);\n    }\n\n    stateManager.setVariable('playerQueue', playerQueue);\n\n    if (!this.pl
```
Stores a value that can be read later with `getVariable`.

## startGame

```javascript
"gameId":"iyIxxiVJASPqGIHVbt6i","name":"startGame","description":"","type":"INPUT","gameEventId":"st
```
Begins a new game session and resets scores.

## teleportPlayers

```javascript
nStart ids\",ids)\n    // playerManager.teleportPlayers(ids, {\n    //   distributionType: 'area',\n
```
Moves every player to the given position.

## triggerParticleEffect

```javascript
e} wins!`;\n        integrationsManager.triggerParticleEffect({\n          interactivePublicKey: thi
```
Plays a particle animation at the specified location.

## updateDataObject

```javascript
 ],\n    });\n\n    integrationsManager.updateDataObject({\n      interactivePublicKey: this.interac
```
Applies updates to a stored data object.

## updateScore

```javascript
"}],"returnType":"void"},{"methodName":"updateScore","parameters":[{"label":"__0","type":"{ playerId
```
Recalculates and stores the player's score based on `amount`.

## updateSprite

```javascript
\n      } else {\n        spriteManager.updateSprite('timer', {\n          text: `Next game starts i
```
Changes properties such as text or position for an existing sprite.

## utils_getPosition

```javascript
scriptManager.attachSystem({ scriptId: 'utils_getPosition' });\n  }\n\n  onInit() {\n    this.resetG
```
Convenience wrapper around `getPosition` for scripts.

## utils_text

```javascript
"}],"scriptType":"system","scriptName":"utils_text","className":"utils_text","contentUpdatedAtISO":"
```
Helper that returns a formatted text string for display.

