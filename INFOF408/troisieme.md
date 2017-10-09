# Chapter 3

**USEFUL LINK:** http://cs.umw.edu/~finlayson/class/fall14/cpsc326/notes/17-variants.html

## Nondeterministic Turing Machine (3.2)

**THEOREM 3.16:** Every *NTM* has an equivalent *DTM*. (equivalent $\to$ recognizes the same language).

**Transition function:** $\delta:Q\times\Gamma\to P(Q\times\Gamma\times\{L,R\})$.
**Proof idea:** We can do a research in the tree of execution (depth first or breadth first). We'll find a branch that goes to $q_{accept}$, so we take that branch and it will be our *DTM* (because there'll be just one $q_accept$, so a way). The best to do is to do a *breadth first*, so we can find the best way from the initial state to the accepting state.

We use 3 tapes to do this breadth first search. The input, adress (identity of a node in the execution tree), and simulation tape. This is then the equivalent *DTM*. (check https://xrpbitom.wordpress.com/2012/01/25/notes-on-equivalence-of-deterministic-and-nondeterministic-turing-machines/)

![](https://xrpbitom.files.wordpress.com/2012/01/dtm1.png)

## Turing-Recognizability

**THEOREM 3.21:** A language is Turing-recognizable if and only if some *enumerator* enumerates it.

An enumerator is a Turing Machine with a printer attached. A printer is a write-only move-right only tape.

![](http://cs.umw.edu/~finlayson/class/fall14/cpsc326/notes/images/enum.png)

There exists such a device that prints every word of $L$ at least once, and prints only words of $L$.

**PROOF:**
 - $\Leftarrow$ Suppose there exists an enumerator $E$ for $L$. $M=$ On input $w$:
    - 1.- Run $E$. Every time that $E$ outputs a string, compare it to $w$.
    - 2.- If equal, accept.
 - $\Rightarrow$ Suppose there exists a Turing Machine that recognizes $L$. $E =$ ignore input.
    - 1.- Repeat for $i$ = 1,2,3...
        * Run $M$ for $i$ steps on inputs $s_1, s_2,\dots,s_i$.
        * If any computation accepts, print the correspnding $s_j$.

**Regular languages:** Recognized by a FA.

**Decidable languages:** Decidable by a TM.

**Recognized languages:** Recognized by a TM / have an enumeration.

**Recursive Enumerable languages:** We can enumerate them with an enumerator.

We can represent those languages in a Venn Diagram, where *Regular $\subseteq$ Decidable $\subseteq$ Recognizable $\subseteq$ Recursive Enumerable*.

## The Church-Turing Thesis

**DEFINITION:** The intuitive notion of algorithm equals turing machine algorithms. Ergo, every known algorithm has an equivalent Turing Machine.

**10th Hilbert's Problem:** Is there an algorithm that finds an integer root in a polynomial. This problem is *recognizable* but not *decidable*. It was proved undecidable in 1970 by Matijaseviĉ.

# Chapter 4

## The Halting Problem

**DEFINITION:** Diagonalization [(Cantor)](https://en.wikipedia.org/wiki/Cantor%27s_diagonal_argument)

**DEFINITION:** $f:A\to B$ is *one-to-one* if all elements of $A$ are mapped to distinct elements of $B$.

**DEFINITION:** It is *onto* whenever it hits all elements of $B$, i.e. $\forall b\in B, \exists a \in A : f(a)=b$

If one-to-one and onto = one-to-one *correspondance* aka *bijection*.

**DEFINITION:** A set $A$ is *countable* if *either* it is finite or there exists a one-to-one correspondance between $A$ and $\mathbb{N}$ or it has the same "size" as $\mathbb{N}$.

Example:
 - Even numbers ? Yes.
 - Rational numbers? $\mathbb{Q}$ - Yes
 - $\mathbb{Z}$ is also countable (we can map the negative to even numbers and positive to odd ones).

 **THEOREM (CANTOR'S DIAGONAL):** $\mathbb{R}$ is not countable.

 **PROOF:** By contradiction: Suppose *it is countable*. We can construct a new by taking a cipher on every row for a different element in the mapped list we constructed. As we have at least one different digit in every element, this new element constructed cannot be in the mapped list, so it's a contradiction (see wikipedia page).

**HOMEWORK:** Let $L$ be the set of all languages over alphabet $\Sigma$, prove that $L$ is uncountable.
