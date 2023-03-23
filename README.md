# Gomoku AI

## What is Gomoku?
Gomoku is a traditional board game originating from Japan, played by two players who take turns placing stones on a board with the goal of connecting five stones in a row horizontally, vertically, or diagonally.

## What does the app do?
This app allows the players to play Gomoku. The app supports 1 player mode against CPU and 2 players mode. A custom AI has been implemented for 1 player mode. The user can select each mode at the main menu. 

Standard board size for Gomoku, 13 x 13, is used. To enhance the user immersion, you can hear the sound when the stone is placed on the board. Joyful and asian-like background music has been chosen so that the users can feel like they are actually playing traditional oriental game. 

When the game is over, the game-over menu is displayed showing the winner, and the user has an option to replay or return to the main menu. 

## How is AI implemented?
### What is Minimax algorithm
The mini-max algorithm has been chosen for the AI. The minimax algorithm is a decision-making algorithm commonly used in two-player games. It works by exploring all possible future moves and outcomes in the game tree, and then selecting the move that maximizes the player's chance of winning or minimizes the opponent's chance of winning. It assumes that the opponent will make the move that is worst for the player, and then tries to find the best move based on that assumption.

For example, in minimax algorithm can be implemented in Tic Tac Toe in the following way. 
    1. Generate all possible moves (i.e., all empty cells on the board).
    2. For each move, simulate the game by placing the player's symbol in the cell and then assume that the opponent will choose their best move.
    3. Continue simulating the game recursively until a terminal state is reached (i.e., a win, loss, or draw).
    4. Assign a score to each terminal state (e.g., +1 for a win, -1 for a loss, 0 for a draw).
    5. Backtrack the scores of each move to the original move, selecting the move that leads to the highest score as the player's next move.

However, in Gomoku, because there are so many possible moves on each turn, it grows exponentially as the turns increase. It takes too much time to track all the possible scenarios. So in this AI, only next two turns have been considered for calculation. Because there needs to be some kind of score to determine which state is better for which player (Step 4 from above example), there had to be an evaluation function. 

### Evaluation Function
Evaluation function is calculated based on number of threats of each player. An example of a threat is 4 stones of the same colors in a row, because the opponent needs to defend if one side is already defended, or the game is over is no side is defended. Different threats have been categorized and provided with different weights. The weighted sum is calculated and based on their sign and magnitude, how much advantage or disadvantage each player has can be determined.

### How Minimax algorithm is implemented
Based on the score, the algorithm decides which move leads to a layout that is the most favored towards the player in turn. A tree has been chosen for the data structure. The root node represents the current board. From the node, the possible moves are shown as children nodes, from which another possible moves derive as grandchildren. The board score at the grandchildren node 
