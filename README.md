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

