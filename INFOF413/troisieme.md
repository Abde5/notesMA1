# Introduction

## Asignment details

 - Not random graphs (choose meaningful graphs).
 - We can use libraries, but actually program the algorithm.

## Computation model and complexity classes

**DEFINITION:** Randomized Turing Machine, it's a TM with probabilistic transitions.

**DEFINITION:** $P$ is the set of all languages $L$ with a deterministic polynomial time with respect to $|x|=n$ algorithm $A$ such that for all $x\in\Sigma^*$, so if $x\in L \Rightarrow A(x)$ accepts and if $x\notin L \Rightarrow A(x)$ rejects.

**DEFINITION:** $RP$ is the set of all languages $L$ such that exists a worst-case poly-time randomized algorithm $A$ such that $x \in L \Rightarrow A(x)$ accepts with probability $\geq \frac{1}{2}$, else if $x\notin L \Rightarrow A(x)$ rejects.

**DEFINITION:** $ZP$ (zero error proabilistic polynomial) is the set of all languages $L$ such that exists a Las Vegas algorithm with polynomial *expected* time.

**DEFINITION:** $CORP$ is the same as the $RP$ class just that it rejects $x$ with probability $\geq \frac{1}{2}$.

Suppose $L\in RP\cap CORP \Rightarrow L\in ZPP$. We can also say that $ZPP=RPP\cap CORP$.

**DEFINITION:** $BPP$ (bounded error probabilistic polynomial) is the set of all languages $L$ such that they have a randomized algorithm worst-case poly-time such that $x\in L \Rightarrow P($ A accepts $)) \geq \frac{3}{4}$. Else $x \notin L \Rightarrow P($ A accepts $) \leq \frac{1}{4}$.

Example: we can take the algorithm for min-cut. $P(\mathbb{error}) < \frac{1}{4}$. Decision problem: is mincut $\leq k$?
 - It's a RP algorithm, because if mincut $> k$, because we answer YES with a probability of $\frac{3}{4} > \frac{1}{2}$.

Example: Decision problem is mincut $= k$?
 - It's a BPP algorithm, because there are 2 sided errors.

# Game-theoretic techniques

## Game tree evaluations

![](http://slideplayer.com/slide/6379740/22/images/4/%E2%80%A6+Game+tree+Max+Min+Max+Min+X+X+X+X+O+O+X+O+X+X+O+O+X+X+O+X+O+X+O+X.jpg)

The motivation for game theory is this problem of evaluating a game. In your turn you wish to do the max, while your enemy wil do the min (because he plays well). This is how it works, the layer max will be replaced by the AND logic operaiton and the min by the OR operation, and it'll do the or/and between his 2 sons (beginning from the leafs).

Exercise: Prove that any deterministic algorithm can be forced to read all $4^k$ leaves. Response: It's intuitive, just check that in each pair of leaves, there's a zero.

With a randomized algorithm, that's not the case if at each step the leaf is chosen equitably.

**RANDOMIZED ALGO:** Recursively:
  - pick L/R with probability $\frac{1}{2}$
  - if AND node:
    - if first subtree returns 0 $\to$ return 0
    - otherwise, recurse and combine
  - else if OR node:
    - if first returns 1 $\to$ return 1
    - otherwise, recurse on the other and combine

**THEOREM:** Expected $\#$ evaluations is $< 3^k$ (more or less more little) $= n^{0.793}$.

**PROVE:** By induction:

  - Best case $k=1$: We have then a tree with root AND, and one layer of OR before. There are then 3 cases:
    - 0 and 1 in the OR nodes: $\frac{1}{2}2 + \frac{1}{2}(\frac{3}{2} + 2)$
    - We have both 0: 2 evaluations in each case
    - We have both 1: $\frac{3}{2} + \frac{3}{2}$.

  - Induction: For k-1, $\leq 3^{k-1}$ evaluations.
    - Suppose root is an OR evaluating 1: $\frac{1}{2}3^{k-1}+\frac{1}{2}2\times3^{k-1} = 3^{k-1}\times\frac{3}{2} < 3^k$.
    - Suppose root is an OR evaluating 0: $2\times3^{k-1} < 3^k$.
    - Suppose root is an AND evaluating 1: $2\times 3^{k-1}\times\frac{3}{2} = 3^k$ (because we test 2 times OR).
    - Suppose root is an AND evaluating 0: $\frac{1}{2}(2\times3^{k-1}) + \frac{1}{2}(\frac{3}{2}3^{k-1} + 2\times3^{k-1}) = 3^{k-1} + 3^{k-1} + \frac{3}{4}3^{k-1} < 3^k$ (because at least one child is 0).
