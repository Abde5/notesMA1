# Introduction

## Compilers

In the other hand, the **synthesis** phase is responsible of:
  - Intermediary code generation. Example: LLVM...
  - Optimizations. Like for loops, etc...
  - Actual code generation. It depends on the target platform. After optimization we can generate code for different platforms (intel, arm, etc...).

## Language theory

  We know the definitions of word and language...

  **DEFINITION:** The empty word is noted $\epsilon$.

  **DEFINITION:** The length of a word $w$ is noted $|w|$. Example: $|aba|=3$.

  **DEFINITION:** A concatenation of 2 words $w$ and $v$ is a new word $w.v$ of all the characters of $w$ followed by those of $b$: $w.v = w_1...w_nv_1...v_l$. $n$ and $l$ the lengths of $w$ and $v$.

  **DEFINITION:** $w^n=w.w...w$ (n times) and $w^0=\epsilon$. So $w^nw^m = w^{n+m}$.

## Operations on languages
  **DEFINITION:** Concatenation $L_1.L_2=\{w_1.w_2|w_1\in L_1,w_2\in L_2\}$.

  Example: $L_1 = \{a,b\}$ and $L_2=\{ab,c\}$ then $L_1.L_2=\{aab,ac,bab,bc\}$.

  Another example: $L_1 . \varnothing = \varnothing$.

  **DEFINITION:** Exponent $L^n = \{w_1...w_n | w_i \in L \ \forall \ 1 \leq i \leq n\}$

  Example: $L=\{a,b\}\ \ \ L^2 = \{aa,ab,ba,bb\}$

  **DEFINITION:** Kleene closure: $L^* = \{w_1...w_n | n \geq 0\  and\  w_i \in L \ \forall 1 \leq i \leq n\}$

  **DEFINITION:** Let $\Sigma$ an alphabet, it can be considered as a language, every symbol of the alphabet is a word. Then $\Sigma^*$ is the set of all words on the alphabet $\Sigma$.

  **PARENTHESE REFERENCES**

  - References:
      - Introduction to automata theory, languages and computation. (H,M,Ullman)
      - Compilers: Principles, Techniques, and Tools (The dragon book)
      - Automata, computability and complexity (E. Rich)

# Chapter 2: Regular languages

  ![Languages](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Chomsky-hierarchy.svg/2000px-Chomsky-hierarchy.svg.png)

  For regular languages we have already presented some tools like *regular expressions, automata* or *scanners*.

  **DEFINITION:** Let us fix a finite alphabet $\Sigma$. $L$ (on $\Sigma$) is regular iff:
  - $L = \varnothing$ or
  - $L = \{\epsilon\}$ or
  - $L = \{a\} \ \ \ a \in \Sigma$ or
  - $L = L_1\cup L_2$ where $L_1,L_2$ are *regular*.
  - $L = L_1.L.2$ where $L_1,L_2$ are *regular*.
  - $L = L_1^*$ where $L_1$ is *regular*.

## Regular expressions

  We can associate regular expressions to languages:

  |regular expressions | languages|
  |------|--------|
  |$\varnothing$| $\varnothing$ |
  |$\epsilon$   | $\{\epsilon\}$|
  |$a \in \Sigma$   | $\{a\}$|
  |$r_1 + r_2$ ($r_1,r_2$ are regular languages)   | $\{a\}$|
  | $l$ | $a + b + c + ... + z + A + B + ... + Z$ |
  | $d$ | $0 + 1 + ... + 9$|

  An identifier is then represented like this: $l(l+d)^*$

## Finite automata

A finite automaton is a "box" that reads a word $w$ as input and answers the question: "Does $w$ belong to $L$?"*. For more details Computability and Complexity course.
