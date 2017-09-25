# Chapter 1: Finite Automata
## Nondeterminism

**Deterministic Finite Automata:** $\delta:Q \times\Sigma \to Q$.

**Nondeterministic Finite Automata:** $\delta:Q\times\Sigma_{\epsilon}\to P(Q)$, $P(Q) \subseteq Q$, so we can reach several different states instead of one for the DFA. The size of $P(Q)$ is the combinaison of every possible subset of $Q$, so: $|P(Q)| = 2^{|Q|}$.

To have an accepting word in a NFA there has to be at least one way to reach a final state in every possible execution.

**THEOREM 1.39:** Every NFA has an equivalent DFA. (They work in the same language)

**Proof:** Let's state a NFA $N=(Q,\Sigma,\delta,q_0,F)$ and a DFA $M=(Q',\Sigma,\delta',q_0',F')$.
  - 1: $Q' = P(Q)$
  - 2: $\delta(R,a) = \bigcup_{r\in R} \delta(r,a)\ \ \ \ a \in\Sigma$.
  - 3: $q_0'$ = $\{q_0\}$
  - 4: $F' = \{R\in Q\  | \ R$ contains an element of F $\}$.

Then we have construct an equivalent DFA. The inconvenient is that the size of the DFA $M$ is exponential to the size of $Q$.

# Chapter 3: The Church-Turing Thesis

## The Turing Machine

Turing machine has a **tape**, that will be used as storage. There are some operations that can be done in this tape: move the head (left or right), write or read something where the head is located. It also has infinite storage (infinite tape). Finally, it has a finite set of states and a transition function (like automata).

![Basic turing machine](http://science.slc.edu/~jmarshall/courses/2002/fall/cs30/Lectures/week08/TuringMachine.gif)

**DEFINITION:** A Turing machine is defined as a 7-tuple: $(Q,\Sigma,\Gamma, \delta, q_0, q_{accept}, q_{rej})$. With $\Sigma \subseteq \Gamma$. $q_{accept}$ and $q_{rej}$ are the accepted and rejected states (only one).

**DEFINITION:** $\delta:Q\times\Gamma \to Q \times \Gamma \times \{L,R\}$. What this means is that the transition function takes in consideration moving and writing. $\Gamma$ being the alphabet of the tape.

The idea of *process* is to not stop until we are in the state $q_{accept}$ or $q_{rej}$.

*Example*: The process of deciding $B = \{w\#w\ |\ w\in \{0,1\}\}$. $010\#010 \in B$. (see book).

**DEFINITION:** A language $L$ is *Turing-Decidable* if there exists a Turing Machine that *halts on all inputs*, such that $L$ is the set of accepted inputs. A Turing Machine halting on all inputs is called a *decider*.

**DEFINITION:** A language $L$ is *Turing-Recognizable* if there exists a Turing Machine such that $L$ *is the set of accepted inputs*.

So for an input $x$... A language $L$ is **decidable** if $\exists$ a Turing Machine such that:
  - if $x \in L$ : it halts in $q_{accept}$.
  - if $x \notin L$ : it halts in $q_{reject}$.

The language $L$ is **recognizable** if $\exists$ a Turing Machine such that:
  - if $x \in L$: it halts in $q_{accept}$.
  - if $x \notin L$: either it halts in $q_{reject}$ or it never halts.

By definition, **all decidable languages are recognizable**.

## Multitape Turing Machine

It a Turing Machine with multiple tapes and multiple heads, so we can add more power to this basic idea of TM.

**DEFINITION:** $\delta:Q\times\Gamma^k \to Q\times\Gamma^k\times\{L,R,S\}^k$. Example: $S(q,(a,b,c))\to(q',(a,b,d),(L,R,S))$.

**Theorem 3.13:** Every multitape TM has an equivalent single-tape TM.

**Proof idea:** "Simulate" $k$ tapes on one. We can do this by introducing another symbol in the language (by convention, $\#$), so we can separate the *contexts* of the multiple tapes in one single tape. So we augment $\Gamma$ with $\#$ and a symbol $x^.$ (point on top of x) for every $x \in \Gamma$ (so we can update where were we, like the marking on the example from the deciding problem of equivalent words).

## Nondeterministic Turing Machine (3.2)

**Transition function:** $\delta:Q\times\Gamma\to P(Q\times\Gamma\times\{L,R\})$.

So there are "branches" of computation and an input is accepted $\Leftrightarrow$ there exists one branch leading to $q_{accept}$ (see *NFA*).

**THEOREM 3.16:** Every *NTM* has an equivalent *DTM*. (equivalent $\to$ recognizes the same language).

**Proof idea:** We can do a research in the tree of execution (depth first or breadth first). We'll find a branch that goes to $q_{accept}$, so we take that branch and it will be our *DTM* (because there'll be just one $q_accept$, so a way). The best to do is to do a *breadth first*, so we can find the best way from the initial state to the accepting state.

(See book for 3 tapes deterministic TM for this proof).
