# Snake-Ladder-SBK
Snake &amp; Ladder SBK is a fun-filled board game experience that blends chance and strategy. Players race to the top of the board, climbing ladders to leap ahead while avoiding snakes that send them sliding back. 
```mermaid

classDiagram
    class Game {
        -players: vector~Player~
        -board: Board
        -dice: Dice
        -currentPlayerIndex: int
        +play()
    }
    
    class Player {
        -name: string
        -position: int
        +move(steps: int)
        +getPosition() int
    }
    
    class Board {
        -snakes: map~int,int~
        -ladders: map~int,int~
        +checkSnakeOrLadder(pos: int) int
        +isWinPosition(pos: int) bool
    }
    
    class Dice {
        -sides: int
        +roll() int
    }
    
    Game "1" --> "1" Board
    Game "1" --> "1" Dice
    Game "1" --> "2..*" Player
    Player ..> Dice : uses
```
```mermaid
sequenceDiagram
    actor User
    participant Game
    participant Player
    participant Dice
    participant Board
    
    User->>Game: play()
    loop Until someone wins
        Game->>Player: get current player
        Game->>User: "Roll dice"
        User->>Game: rollDice()
        Game->>Dice: roll()
        Dice-->>Game: return steps
        Game->>Player: move(steps)
        Player->>Player: position += steps
        Player-->>Game: new position
        Game->>Board: checkSnakeOrLadder(position)
        Board-->>Game: return finalPosition
        Game->>Player: setPosition(finalPosition)
        Game->>Board: isWinPosition(finalPosition)
        alt Nanalo na
            Board-->>Game: true
            Game->>User: "Player wins!"
        else Nothing yet
            Board-->>Game: false
            Game->>Game: switchPlayer()
        end
    end
```
```memaid

```
