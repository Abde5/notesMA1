# Practical information

Course: Data Structures and Algorithms
Teacher: Jean Cardinal
Textbook: Randomized Algorithms (R. Motwani & P. Raghavan)

## Programming assignments
 - 3 assignments, we'll implement an algorithm seen in course and verify it experimentally.

## Exam
  Based on the exercises seen on the course. Same type of questions but slightly different.
# Presentation

This course is particularly based on randomized algorithms.

**Randomized algorithms:** Algorithms that take decisions based on probabilities. (like flipping a coin). This can be used to expect better results than deterministic algorithms. For example: for hashing, the average occupancy of a hashmap is determined randomly (by probabilities). Also quicksort to chose the pivot before sorting/splitting.

## Las Vegas vs Montecarlo

  There are 2 kinds of randomized algorithms.
  - Las Vegas: running time is random
  - Montecarlo: result (choices are) random

  Binary space partitions (computer graphics) [check real time rendering]

  Complexity classes (we match those kind of algorithms to several complexity classes)

## Game-theoritic techniques

  Game theory: Finding a strategy to beat an adversary.
  Some notions: (Nash equilibrium, etc..)

  Yao's Minimax principle...

## Moments/Derivations...
  Chebyshev / Chernoff Bounds: Randomized selection (find the median in a set of numbers).

## Random data Structures
  **Random treaps:** Like binary trees but with random operations with very high probability its operations of deletion/insertion/search are in $\log(n)$.

  **Hashing:** Perfect hashing, if you know what you're putting in the table, you can also use some probabilities...

## Randomized graph algorithms
  Mincut and *linear time MST*.

# Introduction

  ## Quicksort

  An algorithm to sort a list
  - We pick a "pivot" = an arbitrary element $x$
  - partition the remaining elements into 2 groups = those $\leq x$ and those $\gt x$
  - recurse on both parts (unless too small)

  The quicksort can be represented by a binary tree, the root being the pivot chosen in the first step. If splits are event, the number of comparaisons done is $n\log_2(n)$.

  **Randomized quicksort:** When we pick $x$ at random! (Uniformly).

  - $S_{(i)} =$ the element in the ith position in the sorted order.
  - $X_{ij_{(j>i)}} =$ $\#$ times $S_{(i)}$ and $S_{(j)}$ are compared. (This can be either 0 or 1 $\to$ because the pivot disappears after each sort).
  - Expected running time ($\#$ comparaisons) $= E[\Sigma^n_{i=1}\Sigma_{j>i}X_{ij}]=\Sigma^n_{i=1}\Sigma_{j>i}E[X_{ij}]$ (Because linearity of expectation).
  - So we can say: $E[X_{ij}] = P[X_{ij}=1]$

  The question is then, what is the probability that $S_{(i)}$ and $S_{(j)}$ are compared? $\to$ It's equal to the probability that the first chosen pivot in $S_{(i)}$, $S_{(i+1)}$,... $S_{(j)}$ is either $S_{(i)}$ or $S_{(j)}$.

  Probability that one of those elements between $i$ and $j$ is $\frac{1}{j-i+1}$. So $P[X_{ij}=1]=\frac{2}{j-i+1}$. We can then say that, interestingly, the further the numbers are in the ordered set from each other, the less chances they have to be compared between them.

  Then finally we have $\#$ comparaisons:

  $$\#comparaisons = \Sigma^n_{i=1}\Sigma_{j>i}\frac{2}{j-i+1} = 2\Sigma^2_{i=1}\Sigma^{n-i-1}_{k=1}\frac{1}{k} \leq \Sigma^2_{i=1}\Sigma^{n}_{k=1}\frac{1}{k}$$

  Finally, by the definition of harmonic series ($H_n = 1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{n} + \dots + \frac{1}{n} \simeq \ln(n)$):
  $$\Sigma^2_{i=1}\Sigma^{n}_{k=1}\frac{1}{k} \leq 2n\ln(n)$$

  So we can then say that the complexity is $O(n\log(n))$. And we cannot beat $n\log(n)$.

  **PROOF:** Determinitic comparaison-based algorithms cannot beat $n\log(n)$ comparaisons for the complexity in sorting algorithnms.

  To prove it let's imagine that we have an algorithm that does less than $n\log(n)$.
  We have a tree of comparaisons that will give in the end, the leafs, a permutation. We have $n!$ permutations possible. And the height of the tree is $k\log(n!)$. If we assume that the asymptotic behaviour of $n! \simeq n^n$, then the height is $n\log(n)$ (as we said before, it's the number of comparaisons).
