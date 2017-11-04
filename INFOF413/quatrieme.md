# Game-theoretic techniques (The Minimax Principle)

(Based on the notes from the book)

We're gonna prove that there's not any other randomized algorithm that solves the
previous problem in a lower bound that $n^{0.793}$ with the *minimax principle*.


## Game theory

We can represent a game where 2 players are playing a variant of Scissors Paper Stone.
The loser has to pay $1 to the winner. This simple game can be represented by this matrix:

|             | Scissors | Paper | Stone|
|-|-|-|-|
| **Scissors**| 0 | 1 | -1|
| **Paper**   | -1 | 0 | 1 |
| **Stone**   | 1 | -1 | 0 |

This is an instance of a *two-person zero-sum game*, and the matrix is a *payoff matrix*.  It's a zero-sum game because every lose from a player is equilibrated with the wins of the other player. Any zero-sum game is represented by a $n\times m$ matrix $M$. And $M_{ij}$ is the amount paid by the playing player (or received) if he chooses $i$ and the opponent $j$.

When the player chooses the strategy $i$, he's sure he's guaranteed a payoff of $\min_{j}{M_{ij}}$, and an optimal strategy is the strategy that maximizes this, so we'll denote $V_R = \max_i\min_{j}{M_{ij}}$ the lower bound on the value of the payroll when the current player chooses a strategy. An optimal strategy for the opponent is the one that minimizes the payroll that he has to give to the player, so $V_C = \min_j\max_{i}{M_{ij}}$.

We have then an inequality:

$$\max_i\min_{j}{M_{ij}} \leq  \min_j\max_i{M_{ij}}$$

A game can have a solution if $V = V_R = V_C$ ($V$ is called the value of the game), for games with a solution we denote $M_{\rho\gamma}$ where $\rho$ and $\gamma$ are optimal strategies for both of the players.

When there's not a winning strategy, we have to find an optimal strategy without knowledge of the other player's choices. For that we introduce *randomized algorithms*. A mixed strategy is a distribution on the set of every possible strategy. It's represented by the vector $p = (p_1,...,p_m)$ for the player and $q = (q_1,...,q_n)$ for the opponent.

$$E[\mathbb{payoff}] = p^TMq = \sum^n_{i=1}\sum^m_{j=1} p_iM_{ij}q_j$$


**THEOREM (von Neumann's Minimax Theorem):** For any two-person zero-sum game specified by a matrix $M$

$$ \max_p\min_j p^TMq = \min_q\max_ip^TMq $$
