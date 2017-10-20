# Command-Line-Maze
<pre>
A C++ Command Line Maze and solver. Using a simple path finding algorithm. 
╶─┬───┬───────┬───────────────────────────┬───────┬─────┬─────┬───────────┬─────────┬───┬───────────────┬─────┬─────┬───┐
**│***│       │                           │  *****│*****│*****│           │         │   │            ***│  ***│*****│   │
╷*╵*╷*└─────┐ │ ┌───────────────┬─────┐ ╷ ╵ ╷*┌─┐*│*╶─┐*╵*┌─╴*│ ╷ ┌─╴ ┌───┘ ╷ ╶───┬─┘ ╷ ╵ ┌───────┬─╴*╷*├─╴*╷*╵*┌─╴*│ ╶─┤
│***│*******│ │ │               │*****│ │   │*│ │*│·**│***│***│ │ │   │     │     │   │   │       │***│*│***│***│***│   │
├───┴─────┐*│ ╵ ├───┐ ┌───┬─╴ ┌─┘*┌─┐*└─┤ ╶─┤*│ ╵*│·╷*├───┤*┌─┘ │ ├───┘ ╶───┼───┐ │ ╶─┼───┤ ╶─┐ ┌─┘*┌─┤*╵*┌─┴───┤*╶─┴─┐ │
│*********│*│   │   │ │   │   │***│ │***│   │*│***│·│*│   │*│   │ │         │***│ │   │   │   │ │***│ │***│     │*****│ │
│*┌─┬───┐*│*│ ╶─┘ ╷ └─┘ ╷ ╵ ┌─┘*┌─┘ ├─╴*├─╴ │*│*┌─┴─┘*├─╴ │*└───┤ ╵ ┌─────┐ │*╷*│ └─┐ ╵ ╷ └───┘ │*┌─┘ └─┬─┘ ┌─┐ ├─┬─╴*│ │
│*│ │***│*│*│     │     │   │***│   │***│   │*│*│*****│   │*****│   │*****│ │*│*│   │   │       │*│     │   │ │ │ │***│ │
│*│ │*╷*╵*│*├─────┘ ┌───┴─┬─┘*┌─┤ ╷ │*╶─┴─┐ │*│*│*┌───┤ ╶─┴───┐*└───┘*┌─┐*└─┤*│*└─┐ └───┘ ┌─────┤*│ ╷ ╷ └─╴ │ ╵ ╵ │*╶─┤ │
│*│ │*│***│*│       │*****│***│ │ │ │*****│ │*│*│*│   │       │*******│ │***│*│***│       │*****│*│ │ │     │     │***│ │
│*╵ │*├───┤*│ ╶─┬───┘*┌─┐*│*┌─┤ ╵ │ └───┐*└─┘*│*│*│ ╷ └─┐ ┌─╴ ├─────┬─┘ └─┐*│*├─╴*└───────┘*┌─┐*╵*│ │ ├─────┴─┐ ┌─┴─╴*│ │
│***│*│***│*│   │*****│ │*│*│ │   │     │*****│*│*│ │   │ │   │     │     │*│*│  ***********│ │***│ │ │       │ │*****│ │
├─╴*│*╵*╷*╵*├───┤*┌───┤ ╵*│*│ ╵ ╶─┤ ┌─┐ ├─────┤*╵*│ ├─╴ ╵ ├───┘ ┌─╴ │ ╶─┐ │*│*└─┬───┬───┬───┘ ├───┴─┘ │ ┌───┐ │ │*╶───┤ │
│***│***│***│***│*│   │***│*│     │ │ │ │     │***│ │     │     │   │   │ │*│·**│***│   │     │       │ │   │ │ │*****│ │
│*╶─┴───┼───┘*╷*╵*│ ╷ │*╶─┘*│ ┌───┘ │ ╵ └─╴ ╷ ├───┘ └───┐ │ ┌───┤ ╷ │ ┌─┘ │*│·╷*╵*╷*│ ┌─┘ ╷ ╷ │ ┌─────┘ │ ╷ │ └─┴───┐*│ │
│*******│  ***│***│ │ │*****│ │     │       │ │         │ │ │   │ │ │ │   │*│·│**·│*│ │   │ │ │ │       │ │ │       │*│ │
├─┬───┐*└─╴*┌─┴───┘ ├─┴─────┤ │ ╷ ┌─┴─┐ ┌───┼─┘ ┌─────┐ └─┤ ╵ ╷ │ └─┘ │ ╶─┤*└─┴─┐·│*│ ╵ ┌─┤ │ ╵ │ ┌─────┴─┤ └───┐ ┌─┘*│ │
│ │   │*****│       │       │ │ │ │   │ │   │   │     │   │   │ │     │   │*****│·│*│   │ │ │   │ │       │     │ │***│ │
│ ╵ ╷ └─────┘ ╶─────┘ ╶───┐ ╵ │ └─┘ ╷ └─┘ ╷ ╵ ╶─┴─╴ ╷ └─┐ └───┘ └─────┴─┐ └───╴*└─┘*│ ╶─┘ │ └───┘ └─╴ ┌─╴ └───╴ │ ╵*╶─┘ ╵
│   │                     │   │     │     │         │   │               │      *****│     │           │         │  ***** 
└───┴────────────
</pre>
