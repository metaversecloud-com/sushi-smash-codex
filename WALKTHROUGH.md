# Sushi Smash Game Walkthrough

This guide summarizes how the Sushi Smash game operates using the primary engine functions found in `FUNCTION_REFERENCE.md`.

## 1. Game Initialization

When the host starts the session, `onHostStart()` sets baseline variables and loads the sushi stage:

```javascript
stateManager.setVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'playerQueue', []);
stateManager.setVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'gameTimer', 10);
scriptManager.attachSystem({ scriptId: 'gameManager' });
stageManager.setCurrentStage({ _rs: _rs, _rsId: _rsId, as: false }, 'sushi');
```

The game manager attaches the `utils_getPosition` system and resets all scores in its own `onInit()` hook. This prepares the board for players.

## 2. Starting a Match

`startGame()` begins a new round by clearing old state and moving players into position:

```javascript
gameManager.prototype.startGame = function () {
    pseudoProxy.resetGame({ _rs: _rs, _rsId: _rsId, as: false });
    // only moving players and not spectators
    // let playerIds = playerManager.getPlayerIds();
    // playerIds = playerIds.filter(
```

After resetting, sprites for each player's score text are added with `addSprite()` and positioned relative to the stage.

## 3. Spawning Items

Items appear at random board positions through `addItem()` which checks the remaining game timer before spawning:

```javascript
gameManager.prototype.addItem = function (_a) {
    var isPlayer1 = _a.isPlayer1, playerId = _a.playerId, lastItemIsBad = _a.lastItemIsBad;
    var gameTimer = stateManager.getVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'gameTimer');
    if (!pseudoProxy.isGameInProress || gameTimer === 0)
        return;
```

The helper `mathRandomInt(min, max)` selects a sprite ID, and the spawned entity receives an `itemManager` component with `attachComponent()` so it can react to clicks.

## 4. Player Interaction

When a player clicks an item, `itemClicked()` adjusts their score and triggers follow‑up actions:

```javascript
gameManager.prototype.itemClicked = function (_a) {
    var itemId = _a.itemId, isBad = _a.isBad, isPlayer1 = _a.isPlayer1, playerId = _a.playerId, itemPosition = _a.itemPosition;
    if (isPlayer1) {
        if (isBad)
            pseudoProxy.player1_score = pseudoProxy.player1_score - 1;
```

The function then calls `updateScore()` which updates on‑screen text using `updateSprite()`:

```javascript
utils_text.prototype.updateScore = function (_a) {
    var playerId = _a.playerId, score = _a.score;
    spriteManager.updateSprite({ _rs: _rs, _rsId: _rsId, as: false }, `${playerId}_score`, {
        text: `Score: ${score}`,
    });
```

## 5. Removing Items

After an item is handled, or when the timer expires, `removeItem()` cleans the board:

```javascript
gameManager.prototype.removeItem = function (_a) {
    var itemId = _a.itemId, itemPosition = _a.itemPosition, isPlayer1 = _a.isPlayer1, playerId = _a.playerId;
    spriteManager.removeSprite({ _rs: _rs, _rsId: _rsId, as: false }, itemId);
    var occupiedPositions = isPlayer1
        ? pseudoProxy.player1_occupiedPositions.toObject({ _rs: _rs, _rsId: _rsId, as: false })
```

This frees the position so another item can later spawn there.

## 6. Ending a Match

Once the game timer reaches zero, `endGame()` tallies final scores and announces the winner. Particle effects play using `triggerParticleEffect()` before the scene resets:

```javascript
gameManager.prototype.endGame = function () {
    var _a;
    if (pseudoProxy.isEndGameRunning)
        return;
```

Finally `resetGame()` clears variables, preparing for the next round:

```javascript
gameManager.prototype.resetGame = function () {
    pseudoProxy.player1_score = 0;
    pseudoProxy.player2_score = 0;
    pseudoProxy.isGameInProress = false;
    pseudoProxy.player1_occupiedPositions = {
```

## 7. Looping Gameplay

During active play, `onStep()` runs every frame on the host to update timers and spawn new items. When `gameTimer` hits zero, it triggers `endGame()` and eventually `prepForNextGame()` so everything can start over.

---

This walkthrough shows how the core functions from `FUNCTION_REFERENCE.md` fit together when Sushi Smash runs. The engine scripts manage sprites, handle player actions, and maintain game state without any separate backend code.
