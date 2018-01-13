# Messages

All messages must have `referenceId` (of type integer) field.
Game Master (Communication Server?) must include `referenceId` in response.
This mechanism allows Players for matching each response to its request.
`referenceId` value is arbitrarily set by each Player.

## Messages from Game Master

### Game start

To: all Players

Structure:

```
- type: "gameStart"
- body:
    - position_x: <int>
    - position_y: <int>
    - pieceDistance: <int>
```

### End of game

To: all Players

Structure:

```
- type: "gameEnd"
```

### Communication request

Structure:

```
- type: "communicationRequest"
- body:
    - playerId: <int>
    - mustAccept: <bool>
```

Note: `mustAccept` field must be set according to the settings and whether the request was sent by a leader.

Response:

```
- type: "communicationRequest"
- body:
    - board: <Board>
```

## Messages from Player

### Join

Structure:

```
- type: "join"
- body:
    - teamId: <int>
```

Response (success):

```
- type: "join"
- body:
    - success: True
    - playerId: <int>
    - boardWidth: <int>
    - boardHeight: <int>
    - goalAreaHeight: <int>
    - upperGoalAreaTeamId: <int>
    - maxShamCount: <int>
    - eventCosts: Map<Event, int>
```


Response (failure):

```
- type: "join"
- body:
    - success: False
```

### Move

Structure:

```
- type: "move"
- body:
    - direction: <int>
```

Where `direction` is some kind of enum.

Response (success):

```
- type: "move"
- body:
    - success: True
    - pieceDistance: <int>
```

Response (failure):

```
- type: "move"
- body:
    - success: False
    - pieceDistance: <int>
```

### Test a piece

Structure:

```
- type: "test"
```

Response:

```
- type: "test"
- body:
    - isSham: <bool>
```

### Place a piece

Structure:

```
- type: "place"
```

Response:

```
- type: "place"
- body:
    - success: <bool>
```

### Pick up

Structure:

```
- type: "pickUp"
```

Response:

```
- type: "place"
- body:
    - success: <bool>
```

### Discover

Structure:

```
- type: "discover"
```

Response:

```
- type: "discover"
- body:
    - discovered: <tuple of 9 nullable ints>
```

### Communicatation request

Structure:

```
- type: "communicationRequest"
- body:
    - targetPlayer: <int>
```

Response (accepted):

```
- type: "communicationRequest"
- body:
    - success: False
    - board: <Board>
```

Response (denied):

```
- type: "communicationRequest"
- body:
    - success: False
```
