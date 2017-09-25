# COMPUTABILITY AND COMPLEXITY. premier cours

- Références: Introduction to the theory of computation 2nd edition - Michael SIPSER (BOUQUIN, AVOIR ET LIRE)

# Introduction

## Questions
- What problems can be *solved* by a computer?
- What is a problem that *is* solved? Either we can give an answer (yes or no) to a problem.
- What is a computer? -> Something that computes.
- How much resources are required to solve a problem ?
  - What is a resource? -> Time and space (time and space complexity)

**Reduction**: 2 problems that are different can be *reduced* (state that one can just be represented in an instance of another, ergo, it's the same problem).

## Compilers, programming languages
Algorithms like LP, genetic algo, SAT, pathfinding are optimization problems.

**P vs NP** is a problem that can be reduced to travelling salesman. (they are equivalent)

**Known scientists in this branch:** Hilbert, Gödel, Turing, Kleene, Church,
Cook-Levin, Karp

## Things we are supposed to know:
- Set theory (union, intersection, etc...)
- Boolean logic
- Sequences
- Relations
- Functions
- Graph theory
- Strings
- Proofs by contradiction
- Induction
- Big O (complexity) as logarithms definitions

If not -> (read chapter 0 in the textbook)

# Decision problems
Problems for which the answer is yes or no. (ex. classification -> is a cat or a dog?).
A problem has to be *well-defined* and *self-contained* (only need of the problem to attribute a solution, nothing else).

**Problem vs instance:** An instance is an "input" of the kind of problem to be solved. Each instance has a solution (yes or no) if it's a decision problem. Then the problem is a set of inputs for which the answer is YES. (problem: all possible inputs, instance: one input). Example: even numbers, prime numbers, connected graphs (is it connected or not?).

Those problems are encoded in binary. For even and prime numbers it's easy, but for graps for example we need to encode it in binary (for exemple, with adjacency matrices). The nature of the instances will not change depending on the encoding of the problem.

Language: set of strings/words (alphabet = {0,1} )

## Decision vs Optimization

You can use bisection (dichotomic search) to find the best answer that decides the problem also (like the shortest path of at least cost d).

# Chapter 1: Finite automata

## Determinism

Beginning of the answer about "what is a computer?".

**DEFINITION** Finite automata is a 5-tuple ($Q$, $\Sigma$, $\delta$, $q_0$, $F$)
  - $Q$ is a finite set of states
  - $\Sigma$ is a finite set called the alphabet
  - $\delta$ : $Q$ $\times$ $\Sigma$ $\rightarrow$ $Q$ (transition function)
  - $q_0$ $\in$ $Q$ : initial state
  - $F$ $\subseteq$ $Q$ is the set of accepting states

**DEFINITION** (1.16) A language is called a regular language if some finite automata recognizes it.

Finite automaton $M$ defines a language $L(M)$.
Automate seen in the course is defined as:

$A=\{w \in \{0,1\}^* |$ $w$ contains at least one $1$ and an even number of $0$ follow the last $1$ $\}$.

Then A is the language recognized by the automata M: $L(M)=A$.

## Non Deterministim

In the previous automata, given a position we go to another position given the input, just one position. There is not a choice, it's determined by the automata (deterministic automata). In the other hand, non determinism is the idea that an input passed in a transition function can give multiple positions.

[Example of non deterministic automata]

Then, a string is accepted in the language of the non determinstic automata if there's at least *one execution* of the automata for that string that finishes in a state in $F$.

For the finding of that execution we use *branch and bound* with a tree with every possible execution of the automata. Then we check the leaf of the tree and we see if it's in $F$.

**DEFINITION** The transition function for non deterministic automata is then $\delta:Q\times\Sigma_{\epsilon}\to P(Q)$. So now there's a set of transition states for an input.

**THÉORÈME** (1.39) Every nondeterminstic finite automaton has an equivalent deterministic finite automaton.
