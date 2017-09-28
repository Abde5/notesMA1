# Chapter 2: Regular languages

## Nondeterministic automata

NB: Go check *Computability and Complexity* notes. (Execution tree, etc.)

### $\epsilon$-NFA: $\epsilon$-Non Deterministic Finite State Automaton

For the example, we'll take this phrase: "A sequence of a's followed by a sequence of b's".

First, we can draw an automaton that accepts just a's, and then another that accepts just b's (by looping, one state). Then we have to reliate these 2 automaton but we have to put some character for the transition. So we put $\epsilon$ on the transition. This is also called a **spontaneous move**.

Some hidden non-determinisim can be done with $\epsilon$ like this:
![](./img/epsNFA.png)

**DEFINITION:** Definition of automaton: 5-tuple (*Computability and complexity*).

**DEFINITION:** Definition of Language $L(A)$ (*Computability and complexity*).

**PROPERTY:** DFA $\subseteq$ NFA $\subseteq$ $\epsilon$-NFA.

## Kleene's Theorem

**DEFINITION:** Every regular language is accepted by a DFA. For all $\epsilon$-NFA $A$: $L(A)$ is regular.

**PROOF:** The proof is done in 3 parts:
- 1. To each regular expression corresponds an $\epsilon$-NFA.
- 2. To each $\epsilon$-NFA corresponds a DFA.
- 3. To each DFA corresponds a Regular Expression.

So the three are equivalent.

**PROOF 1:** From regular expression to $\epsilon$-NFA.

|Regular expression|Automaton|
|----|--|
|$\varnothing$| ![](./img/nothing.png)|
|$\epsilon$| ![](./img/epsilon.png)|
|$a$| ![](./img/aautomaton.png) |
|$r_1+r_2$| We make the union of the automata by putting a new initial state that jumps to the initial state of $r_1$ and $r_2$ by $\epsilon$, same with the accepting states.|
|$r_1.r_2$| The concatenation of the 2 automata (with epsilons too). |
|$r^*$| We have to loop the automaton of $r$, jumping from the final state to the initial state, also jumping from the beginning to the end to skip it. |
