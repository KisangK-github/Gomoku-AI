# Gomoku AI

## What is Gomoku?
Gomoku is a traditional board game originating from Japan, played by two players who take turns placing stones on a board with the goal of connecting five stones in a row horizontally, vertically, or diagonally.

## What does the app do?
This app allows the players to play Gomoku. The app supports 1 player mode against CPU and 2 players mode. A custom AI has been implemented for 1 player mode. The user can select each mode at the main menu. 

Standard board size for Gomoku, 13 x 13, is used. To enhance the user immersion, you can hear the sound when the stone is placed on the board. Joyful and asian-like background music has been chosen so that the users can feel like they are actually playing traditional oriental game. 

When the game is over, the game-over menu is displayed showing the winner, and the user has an option to replay or return to the main menu. 

## How is AI implemented?
The mini-max algorithm has been chosen for the AI. The minimax algorithm is a decision-making algorithm commonly used in two-player games. It works by exploring all possible future moves and outcomes in the game tree, and then selecting the move that maximizes the player's chance of winning or minimizes the opponent's chance of winning. It assumes that the opponent will make the move that is worst for the player, and then tries to find the best move based on that assumption.

For example, in minimax algorithm can be implemented in Tic Tac Toe in the following way. 
    1. Generate all possible moves (i.e., all empty cells on the board).
    2. For each move, simulate the game by placing the player's symbol in the cell and then assume that the opponent will choose their best move.
    3. Continue simulating the game recursively until a terminal state is reached (i.e., a win, loss, or draw).
    4. Assign a score to each terminal state (e.g., +1 for a win, -1 for a loss, 0 for a draw).
    5. Backtrack the scores of each move to the original move, selecting the move that leads to the highest score as the player's next move.

However, in Gomoku, because there are so many possible moves on each turn, it grows exponentially as the turns increase. It takes too much time to track all the possible scenarios. So in this AI, only next two turns have been considered for calculation. Because there needs to be some kind of score to determine which state is better for which player (Step 4 from above example), there had to be an evaluation function. 

### Evaluating Function
