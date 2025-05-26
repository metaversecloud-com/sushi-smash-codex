## addItem(itemType, x, y)
\`\`\`javascript
        };
    };
    gameManager.prototype.addItem = function (_a) {
        var isPlayer1 = _a.isPlayer1, playerId = _a.playerId, lastItemIsBad = _a.lastItemIsBad;
        var gameTimer = stateManager.getVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'gameTimer');
\`\`\`
Spawns a new item into the board at the given coordinates and returns its identifier.

## addPlayerText(playerId, message, color?)
\`\`\`javascript
    function utils_text() {
    }
    utils_text.prototype.addPlayerText = function (_a) {
        var isPlayer1 = _a.isPlayer1, playerId = _a.playerId;
        console.log({ _rs: _rs, _rsId: _rsId, as: false }, "utils_text playerId", playerId);
\`\`\`
Displays floating text above the specified player. The text fades after a short duration.

## addSprite(id, asset, options)
\`\`\`javascript
            .getSystem({ systemName: 'utils_getPosition' })
            .getPosition({ _rs: _rs, _rsId: _rsId, as: false }, { isPlayer1: isPlayer1, occupiedPositions: occupiedPositions }), position = _b.position, x = _b.x, y = _b.y;
        spriteManager.addSprite({ _rs: _rs, _rsId: _rsId, as: false }, "".concat(pseudoProxy.theme).concat(spriteId), {
            uniqueId: uniqueId,
            applyPhysics: true,
\`\`\`
Inserts a sprite into the current stage using the provided asset and optional position or settings.

## attachComponent(entityId, component)
\`\`\`javascript
            positionY: y,
        });
        scriptManager.attachComponent({ _rs: _rs, _rsId: _rsId, as: false }, {
            objectUniqueId: uniqueId,
            componentName: 'itemManager',
\`\`\`
Attaches a behavior component to an entity so the engine can process it each frame.

## attachSystem(systemFn)
\`\`\`javascript
        pseudoProxy.isNextGamePreped = false;
        pseudoProxy.interactivePublicKey = stateManager.getVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'interactivePublicKey');
        scriptManager.attachSystem({ _rs: _rs, _rsId: _rsId, as: false }, { scriptId: 'utils_getPosition' });
    }
    gameManager.prototype.onInit = function () {
\`\`\`
Registers a system function with the game manager so it runs during the update loop.

## boardManager
\`\`\`javascript
    "use strict";
    var pseudoProxy = scriptManager._getPsuedoProxy({ scriptInstanceId: scriptInstanceId });
    function boardManager() {
    }
    boardManager.prototype.onInit = function () {
\`\`\`
Manager object used for board-level state changes such as adding or removing tiles.

## buttonManager
\`\`\`javascript
    "use strict";
    var pseudoProxy = scriptManager._getPsuedoProxy({ scriptInstanceId: scriptInstanceId });
    function buttonManager() {
    }
    buttonManager.prototype.onClicked = function () {
\`\`\`
Utility that creates and tracks interactive buttons for the user interface.

## emit(eventName, data)
\`\`\`javascript
            return;
        pseudoProxy.itemTimer = 0;
        eventManager.emit({ _rs: _rs, _rsId: _rsId, as: false }, 'itemClicked', {
            isBad: isBad,
            isPlayer1: isPlayer1,
\`\`\`
Fires a custom event so other scripts or systems can react to `eventName`.

## endGame()
\`\`\`javascript
        }
    };
    gameManager.prototype.endGame = function () {
        var _a;
        if (pseudoProxy.isEndGameRunning)
\`\`\`
Stops the current match and tallies final scores.

## gameManager
\`\`\`javascript
    "use strict";
    var pseudoProxy = scriptManager._getPsuedoProxy({ scriptInstanceId: scriptInstanceId });
    function gameManager() {
        pseudoProxy.player1_occupiedPositions = {};
        pseudoProxy.player2_occupiedPositions = {};
\`\`\`
Provides access to the core game controller and global settings.

## getComponent(entityId, componentName)
\`\`\`javascript
            scriptId: 'itemManager',
        });
        var item = scriptManager.getComponent({ _rs: _rs, _rsId: _rsId, as: false }, {
            objectUniqueId: uniqueId,
            componentName: 'itemManager',
\`\`\`
Retrieves a component instance from the specified entity.

## getDataObject(key)
\`\`\`javascript
        var player1 = playerManager.getPlayerDetails({ _rs: _rs, _rsId: _rsId, as: false }, pseudoProxy.player1_id);
        var p1profileId = player1.profileId;
        var dataObject = integrationsManager.getDataObject({ _rs: _rs, _rsId: _rsId, as: false }, {
            interactivePublicKey: pseudoProxy.interactivePublicKey,
            scope: 'WORLD',
\`\`\`
Returns a stored data object associated with the given key.

## getMyPlayerId()
\`\`\`javascript
        });
        var itemPosition = item.itemPosition, isBad = item.isBad, isPlayer1 = item.isPlayer1, playerId = item.playerId;
        if (playerId !== playerManager.getMyPlayerId({ _rs: _rs, _rsId: _rsId, as: false }))
            return;
        pseudoProxy.itemTimer = 0;
\`\`\`
Returns the identifier for the current player.

## getPlayerDetails(playerId)
\`\`\`javascript
        var _b;
        var playerId = _a.playerId;
        var profileId = (_b = playerManager.getPlayerDetails({ _rs: _rs, _rsId: _rsId, as: false }, playerId)) === null || _b === void 0 ? void 0 : _b.profileId;
        integrationsManager.putPublicKeyAnalytics({ _rs: _rs, _rsId: _rsId, as: false }, {
            interactivePublicKey: pseudoProxy.interactivePublicKey,
\`\`\`
Looks up metadata, such as name or score, for a player.

## getPlayerIds()
\`\`\`javascript
        pseudoProxy.resetGame({ _rs: _rs, _rsId: _rsId, as: false });
        // only moving players and not spectators
        // let playerIds = playerManager.getPlayerIds();
        // playerIds = playerIds.filter(
        //   (number) => number !== this.player1_id && number !== this.player2_id,
\`\`\`
Returns an array containing all active player identifiers.

## getPosition(entityId)
\`\`\`javascript
    function utils_getPosition() {
    }
    utils_getPosition.prototype.getPosition = function (_a) {
        var isPlayer1 = _a.isPlayer1, _b = _a.occupiedPositions, occupiedPositions = _b === void 0 ? {} : _b;
        var col1 = 200;
\`\`\`
Returns the current x and y coordinates of the entity.

## getRandomUUID()
\`\`\`javascript
            return;
        var spriteId = mathRandomInt({ _rs: _rs, _rsId: _rsId, as: false }, 1, lastItemIsBad ? 8 : 12);
        var uniqueId = getRandomUUID({ _rs: _rs, _rsId: _rsId, as: false });
        var _b = scriptManager
            .getSystem({ systemName: 'utils_getPosition' })
\`\`\`
Generates a random unique identifier string.

## getSystem(name)
\`\`\`javascript
        var theme = pseudoProxy.sprite.uniqueId;
        var main = scriptManager
            .getSystem({ _rs: _rs, _rsId: _rsId, as: false }, { systemName: 'main' })
            .startGame({ theme: theme });
    };
\`\`\`
Fetches a registered system instance by name.

## getVariable(name)
\`\`\`javascript
        pseudoProxy.endGameTimer = 10;
        pseudoProxy.isNextGamePreped = false;
        pseudoProxy.interactivePublicKey = stateManager.getVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'interactivePublicKey');
        scriptManager.attachSystem({ _rs: _rs, _rsId: _rsId, as: false }, { scriptId: 'utils_getPosition' });
    }
\`\`\`
Reads a game variable that was previously stored with `setVariable`.

## itemClicked(itemId)
\`\`\`javascript
            pseudoProxy.addItem({ _rs: _rs, _rsId: _rsId, as: true }, { isPlayer1: isPlayer1, playerId: playerId });
    };
    gameManager.prototype.itemClicked = function (_a) {
        var itemId = _a.itemId, isBad = _a.isBad, isPlayer1 = _a.isPlayer1, playerId = _a.playerId, itemPosition = _a.itemPosition;
        if (isPlayer1) {
\`\`\`
Handler that executes when a player clicks an item.

## itemManager
\`\`\`javascript
        scriptManager.attachComponent({ _rs: _rs, _rsId: _rsId, as: false }, {
            objectUniqueId: uniqueId,
            componentName: 'itemManager',
            scriptId: 'itemManager',
        });
\`\`\`
Helper object that maintains item state and performs spawn/removal logic.

## main()
\`\`\`javascript
    buttonManager.prototype.onClicked = function () {
        var theme = pseudoProxy.sprite.uniqueId;
        var main = scriptManager
            .getSystem({ _rs: _rs, _rsId: _rsId, as: false }, { systemName: 'main' })
            .startGame({ theme: theme });
\`\`\`
Entry point for scripts executed by the game engine.

## mathRandomInt(min, max)
\`\`\`javascript
        if (count > 3)
            return;
        var spriteId = mathRandomInt({ _rs: _rs, _rsId: _rsId, as: false }, 1, lastItemIsBad ? 8 : 12);
        var uniqueId = getRandomUUID({ _rs: _rs, _rsId: _rsId, as: false });
        var _b = scriptManager
\`\`\`
Returns a random integer between `min` and `max`, inclusive.

## onClicked(entityId)
\`\`\`javascript
    function buttonManager() {
    }
    buttonManager.prototype.onClicked = function () {
        var theme = pseudoProxy.sprite.uniqueId;
        var main = scriptManager
\`\`\`
Callback invoked whenever a sprite or item is clicked by a player.

## onEvent_addItem(data)
\`\`\`javascript
        });
    };
    main.prototype.onEvent_addItem = function (_a) {
        var isPlayer1 = _a.isPlayer1, playerId = _a.playerId, lastItemIsBad = _a.lastItemIsBad;
        if (!playerManager.isHost)
\`\`\`
Runs when the `addItem` event is emitted to spawn new items.

## onEvent_itemClicked(data)
\`\`\`javascript
        }
    };
    main.prototype.onEvent_itemClicked = function (_a) {
        var itemId = _a.itemId, isBad = _a.isBad, isPlayer1 = _a.isPlayer1, playerId = _a.playerId, itemPosition = _a.itemPosition;
        if (!playerManager.isHost)
\`\`\`
Runs when an item click event is received.

## onEvent_removeItem(data)
\`\`\`javascript
            .addItem({ _rs: _rs, _rsId: _rsId, as: false }, { isPlayer1: isPlayer1, playerId: playerId, lastItemIsBad: lastItemIsBad });
    };
    main.prototype.onEvent_removeItem = function (_a) {
        var itemId = _a.itemId, itemPosition = _a.itemPosition, isPlayer1 = _a.isPlayer1, playerId = _a.playerId;
        if (!playerManager.isHost)
\`\`\`
Runs when an item removal event occurs.

## onHostStart()
\`\`\`javascript
    function main() {
    }
    main.prototype.onHostStart = function () {
        stateManager.setVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'playerQueue', []);
        stateManager.setVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'gameTimer', 10);
\`\`\`
Initialization routine that only executes for the host player when the game begins.

## onInit()
\`\`\`javascript
    function boardManager() {
    }
    boardManager.prototype.onInit = function () {
    };
    boardManager.prototype.onSpriteCollisionStart = function () {
\`\`\`
Sets up variables and prepares the scene when the game first loads.

## onPlayerJoined(playerId)
\`\`\`javascript
        pseudoProxy.resetGame({ _rs: _rs, _rsId: _rsId, as: false });
    };
    gameManager.prototype.onPlayerJoined = function (_a) {
        var _b;
        var playerId = _a.playerId;
\`\`\`
Executes when a new player joins the session.

## onPlayerLeft(playerId)
\`\`\`javascript
        }
    };
    gameManager.prototype.onPlayerLeft = function (_a) {
        var playerId = _a.playerId;
        pseudoProxy.removeFromQueue({ _rs: _rs, _rsId: _rsId, as: true }, { playerId: playerId });
\`\`\`
Executes when a player leaves the session.

## onSpriteCollisionStart(aId, bId)
\`\`\`javascript
    boardManager.prototype.onInit = function () {
    };
    boardManager.prototype.onSpriteCollisionStart = function () {
    };
    ;
\`\`\`
Fired the moment two sprites begin colliding.

## onStep(delta)
\`\`\`javascript
        stateManager.setVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'playerQueue', playerQueue);
    };
    gameManager.prototype.onStep = function () {
        if (!playerManager.isHost)
            return;
\`\`\`
Runs on every simulation step to update game logic.

## onVariableChanged_playerQueue(value)
\`\`\`javascript
        });
    };
    main.prototype.onVariableChanged_playerQueue = function (_a) {
        var newValue = _a.newValue;
        var text = ' ';
\`\`\`
Responds when the `playerQueue` variable is modified.

## prepForNextGame()
\`\`\`javascript
        pseudoProxy.isEndGameRunning = false;
    };
    gameManager.prototype.prepForNextGame = function () {
        var _a;
        // 5 seconds before next game counter starts or when 2nd player joins
\`\`\`
Clears temporary variables and readies the engine for another round.

## putPublicKeyAnalytics(key)
\`\`\`javascript
        var playerId = _a.playerId;
        var profileId = (_b = playerManager.getPlayerDetails({ _rs: _rs, _rsId: _rsId, as: false }, playerId)) === null || _b === void 0 ? void 0 : _b.profileId;
        integrationsManager.putPublicKeyAnalytics({ _rs: _rs, _rsId: _rsId, as: false }, {
            interactivePublicKey: pseudoProxy.interactivePublicKey,
            analytics: [
\`\`\`
Records an analytics event for the provided public key.

## removeFromQueue(playerId)
\`\`\`javascript
        pseudoProxy.removeFromQueue({ _rs: _rs, _rsId: _rsId, as: true }, { playerId: playerId });
    };
    gameManager.prototype.removeFromQueue = function (_a) {
        var playerId = _a.playerId, _b = _a.shouldMoveToBottom, shouldMoveToBottom = _b === void 0 ? false : _b;
        var playerQueue = stateManager.getVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'playerQueue');
\`\`\`
Removes the player from any waiting queue.

## removeItem(itemId)
\`\`\`javascript
        }
    };
    gameManager.prototype.removeItem = function (_a) {
        var itemId = _a.itemId, itemPosition = _a.itemPosition, isPlayer1 = _a.isPlayer1, playerId = _a.playerId;
        spriteManager.removeSprite({ _rs: _rs, _rsId: _rsId, as: false }, itemId);
\`\`\`
Removes an existing item from the board.

## removePlayerText(playerId)
\`\`\`javascript
        });
    };
    utils_text.prototype.removePlayerText = function (_a) {
        var playerId = _a.playerId;
        spriteManager.removeSprite({ _rs: _rs, _rsId: _rsId, as: false }, "".concat(playerId, "_name"));
\`\`\`
Clears floating text that was shown for a player.

## removeSprite(id)
\`\`\`javascript
    gameManager.prototype.removeItem = function (_a) {
        var itemId = _a.itemId, itemPosition = _a.itemPosition, isPlayer1 = _a.isPlayer1, playerId = _a.playerId;
        spriteManager.removeSprite({ _rs: _rs, _rsId: _rsId, as: false }, itemId);
        var occupiedPositions = isPlayer1
            ? pseudoProxy.player1_occupiedPositions.toObject({ _rs: _rs, _rsId: _rsId, as: false })
\`\`\`
Deletes a sprite from the current stage.

## resetGame()
\`\`\`javascript
        pseudoProxy.isNextGamePreped = true;
    };
    gameManager.prototype.resetGame = function () {
        pseudoProxy.player1_score = 0;
        pseudoProxy.player2_score = 0;
\`\`\`
Restores all game variables and state back to defaults.

## setCurrentStage(stageName)
\`\`\`javascript
        stateManager.setVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'gameTimer', 10);
        scriptManager.attachSystem({ scriptId: 'gameManager' });
        stageManager.setCurrentStage({ _rs: _rs, _rsId: _rsId, as: false }, 'sushi');
        spriteManager.addSprite({ _rs: _rs, _rsId: _rsId, as: false }, 'sushiLayer1', {
            uniqueId: 'sushiLayer1',
\`\`\`
Switches the active stage or scene.

## setVariable(name, value)
\`\`\`javascript
            playerQueue.push(pseudoProxy.player2_id);
        }
        stateManager.setVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'playerQueue', playerQueue);
        if (!pseudoProxy.player2_id && !pseudoProxy.isGameInProress)
            pseudoProxy.prepForNextGame({ _rs: _rs, _rsId: _rsId, as: false });
\`\`\`
Stores a value that can be read later with `getVariable`.

## startGame()
\`\`\`javascript
        }
    };
    gameManager.prototype.startGame = function () {
        pseudoProxy.resetGame({ _rs: _rs, _rsId: _rsId, as: false });
        // only moving players and not spectators
\`\`\`
Begins a new game session and resets scores.

## teleportPlayers(position)
\`\`\`javascript
        // );
        // console.log("playerIds",playerIds)
        // playerManager.teleportPlayers(playerIds, {
        //   distributionType: 'area',
        //   positionX: 100,
\`\`\`
Moves every player to the given position.

## triggerParticleEffect(effectId, position)
\`\`\`javascript
            if (winnerId) {
                text = "".concat(playerManager.getPlayerDetails({ _rs: _rs, _rsId: _rsId, as: false }, winnerId).nameplate, " wins!");
                integrationsManager.triggerParticleEffect({ _rs: _rs, _rsId: _rsId, as: false }, {
                    interactivePublicKey: pseudoProxy.interactivePublicKey,
                    duration: 4,
\`\`\`
Plays a particle animation at the specified location.

## updateDataObject(key, updates)
\`\`\`javascript
            ],
        });
        integrationsManager.updateDataObject({ _rs: _rs, _rsId: _rsId, as: false }, {
            interactivePublicKey: pseudoProxy.interactivePublicKey,
            scope: 'WORLD',
\`\`\`
Applies updates to a stored data object.

## updateScore(playerId, amount)
\`\`\`javascript
        spriteManager.removeSprite({ _rs: _rs, _rsId: _rsId, as: false }, "".concat(playerId, "_score"));
    };
    utils_text.prototype.updateScore = function (_a) {
        var playerId = _a.playerId, score = _a.score;
        spriteManager.updateSprite({ _rs: _rs, _rsId: _rsId, as: false }, "".concat(playerId, "_score"), {
\`\`\`
Recalculates and stores the player's score based on `amount`.

## updateSprite(id, props)
\`\`\`javascript
            }
            else {
                spriteManager.updateSprite({ _rs: _rs, _rsId: _rsId, as: false }, 'timer', {
                    text: "Next game starts in ".concat(nextGameTimer),
                });
\`\`\`
Changes properties such as text or position for an existing sprite.

## utils_getPosition(entityId)
\`\`\`javascript
        pseudoProxy.isNextGamePreped = false;
        pseudoProxy.interactivePublicKey = stateManager.getVariable({ _rs: _rs, _rsId: _rsId, as: false }, 'interactivePublicKey');
        scriptManager.attachSystem({ _rs: _rs, _rsId: _rsId, as: false }, { scriptId: 'utils_getPosition' });
    }
    gameManager.prototype.onInit = function () {
\`\`\`
Convenience wrapper around `getPosition` for scripts.

## utils_text(value)
\`\`\`javascript
    "use strict";
    var pseudoProxy = scriptManager._getPsuedoProxy({ scriptInstanceId: scriptInstanceId });
    function utils_text() {
    }
    utils_text.prototype.addPlayerText = function (_a) {
\`\`\`
Helper that returns a formatted text string for display.

