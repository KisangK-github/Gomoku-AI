# Gomoku AI

## What is Gomoku?
Gomoku is a traditional board game originating from Japan, played by two players who take turns placing stones on a board with the goal of connecting five stones in a row horizontally, vertically, or diagonally.

## What does the app do?
Welcome to our Gomoku app, where you can challenge yourself or a friend to a game of strategy and skill! Our app offers both 1 player mode against the CPU and 2 player mode for friendly matches.

With a custom AI implemented for 1 player mode, you'll face a challenging opponent who will put your Gomoku skills to the test. And with the standard board size of 13 x 13, you'll have plenty of space to plan your moves and outsmart your opponent.

To enhance your immersion, the sound of stones being placed on the board will give you an authentic Gomoku experience. And with joyful, Asian-inspired background music, you'll feel like you're playing a traditional game in the heart of the East.

## How is AI implemented?
### What is Minimax algorithm
The minimax algorithm is a powerful decision-making algorithm that is commonly used in two-player games. It works by exploring all possible future moves and outcomes in the game tree, selecting the move that maximizes the player's chance of winning or minimizes the opponent's chance of winning. This is achieved by assuming that the opponent will make the move that is worst for the player, and then trying to find the best move based on that assumption.

For example, in Tic Tac Toe, the minimax algorithm can be implemented by generating all possible moves and simulating the game recursively until a terminal state is reached. Then, a score is assigned to each terminal state and the scores are backtracked to the original move, selecting the move that leads to the highest score as the player's next move.

However, in games like Gomoku, where there are many possible moves on each turn, it becomes computationally expensive to track all possible scenarios. As a result, in this AI, only the next two turns are considered for calculation. To determine which state is better for each player, an evaluation function is used to assign scores to the states.

### Evaluation Function
The evaluation function plays a crucial role in determining which state is better for each player in a game. In this AI, the evaluation function is calculated based on the number of threats each player has on the board. An example of threat occurs when a player has four stones of the same color in a row, which forces the opponent to defend or risk losing the game.

To account for different types of threats, they have been categorized and assigned different weights. The weighted sum of all threats is then calculated, and based on their sign and magnitude, the advantage or disadvantage of each player can be determined. This allows the AI to make informed decisions about which moves to make, as it can prioritize moves that lead to more threatening positions or avoid moves that leave it vulnerable to attack. 

### How Minimax algorithm is implemented in Gomoku AI
The minimax algorithm utilizes a tree data structure to evaluate all possible moves and determine which move leads to the most favorable layout for the player in turn. At the root node of the tree is the current board layout. The children nodes represent all possible moves from the current layout, and each of those children nodes can have grandchildren nodes that represent further possible moves.

The algorithm then assigns a score to each of the grandchildren nodes based on the outcome of the game. The children nodes choose the score that is most favorable to the opponent, while the root node chooses the score that is most favorable to the player. This allows the algorithm to search through all possible moves and select the move that leads to the best possible outcome for the player.

### Optimization
To improve the efficiency of the algorithm, some assumptions have been made that take advantage of the characteristics of Gomoku. For instance, it is highly improbable that a player will place a stone far from the existing stones on the board. Hence, the algorithm only considers those spaces that are two steps away from current stones as possible moves. This helps to narrow down the number of moves the algorithm needs to explore, saving time and resources.

Furthermore, during the backtracking phase of the algorithm, some branches can be eliminated because they are guaranteed to be worse than the previous branch. This is because the algorithm assumes that the opponent will always make the move that is worst for the player. As a result, some branches can be safely eliminated from consideration because they are less advantageous to the player than the previously evaluated branch. This optimization further streamlines the algorithm and enables it to quickly and accurately identify the best possible move.
