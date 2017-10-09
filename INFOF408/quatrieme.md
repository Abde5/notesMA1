# Chapter 4

## The Halting Problem

**DEFINITION:** The halting problem is the problem that describes the language of machines that will either stop or not. The algorithm that solves the halting problem is defined as: $A_{TM} = \{(M,w) |$ M is a TM that accepts w$\}$

**THEOREM:** $A_{TM}$ is undecidable.

**PROOF:** By contradiction. Suppose $A_{TM}$ is decidable.
  - there exists $H(<M,w>)$ = accepts if $M$ accepts $w$ and rejects otherwise.

**Define D:** on input $M$ (a TM):
  - 1. Run $H$ on input $<M,<M>>$
  - 2. Output the opposite of $H$:
    - Accept if $M$ does not accept $<M>$
    - Reject if $M$ accepts $<M>$

And the final blow: we have to run $D$ on itself! ($D(<D>)$).

Then we have a contradiction: $D(<D>)$ accepts $\Leftrightarrow D(<D>)$ rejects.

Then $A_{TM}$ is **undecidable**.


Let's have a language $A$, we define $\overline{A}$ as the complement: $\overline{A} = \{w\  |\  w \notin A\}$. Suppose that both $A$ and $\overline{A}$ are recognizable. Then both $A$ and $\overline{A}$ are also decidable.

**PROOF:** Let $M$ and $M'$ be the recognizers for $A$ and $\overline{A}$, respectively. Construct a decider $D$ for $A$ by executing $M$ and $M'$ "in parallel" (alternate one step of $M$ and one step of $M'$)

$A_{TM}$ is undecidable, is it recognizable? *Yes*, $A_{TM}$ is recognizable (proof: simulate $M$ on $w$). This means that $\overline{A}_{TM}$ is not recognizable. ($\overline{A}_{TM} = \{<M,w> |\  w$ is not accepted by $M\}$)

For a TM $M$, denote by $L(M)$ the language recognized by $M$. $L(M) = \{w\in\Sigma^*\ |\ M$ accepts $w\}$


# Chapter 5 (Reducibility)

**THEOREM 5.3:** $\mathrm{Regular}_{TM} = \{<M> |\ M$ is a TM and $L(M)$ is regular $\}$. This is *undecidable*.

**PROOF:** Define a TM $M_2$ as a function of $M$ and $w$.

$M_2=$ "on input $x$:
  - 1. If $x$ has the form $0^n1^n$, accept.
  - 2. Otherwise, run $M$ on $w$ and accept if $M$ accepts $w$.

What is $L(M_2)$?
  - 1. If $M$ accepts $w$; $L(M) = \Sigma^*$ (it accepts everything!)
  - 2. If $M$ does not accept $w$, $L(M_2) =\{0^n1^n\ |\ n\geq 0\}$

Now by contradiction, suppose $\mathrm{Regular}_{TM}$ is decidable. ie there exists $R$, a decider for $\mathrm{Regular}_{TM}$.

Define S= "on input <M,w> :"
  - 1. Construct $M_2$ from $M,w$.
  - 2. Run $R$ on $M_2$. Accept iff $R$ accepts.

$S$ decides $A_{TM}\to$ CONTRADICTION!

## Rice's theorem

**Exercise 5.28:** Let $P$ be any nontrivial property of a language.

**THEOREM:** Determining whether a TM's language has property $P$ is *undecidable*.

$\{<M> | \ M$ is a TM and $L(M)$ has a property $P\}$

**PROOF:** By contradiction: Let $R_p$ be the decider for $L_p$.
  - Let $T_{\varnothing}$ be a TM that always rejects. ($L(T_{\varnothing}) = \varnothing$). Suppose that $\varnothing \notin P$. (without loss of generality).
  - Let $T$ be a TM such that $L(M)\in P$.

Given $M,w$, construct $M_w:$ on input $x$:
  - 1. simulate $M$ on $w$. If it accepts, go to step 2. If rejects, reject.
  - 2. simulate $T$ on $x$, accept if it accepts.

The statement we made is that $M$ accepts $w \Leftrightarrow L(M_w)\in P$.

Now construct a decider for $A_{TM}$: $S =$ on input $M,w$:
  - 1. Construct $M_w$.
  - 2. Run $R_p$ on $M_w$ answer the same.
