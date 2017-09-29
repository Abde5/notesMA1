# Introduction
## Remember: Properties about probabilities

We have 2 events $\epsilon_1$ and $\epsilon_2$.
  - If independent $P(\epsilon_1\cap\epsilon_2) = P(\epsilon_1)P(\epsilon_2)$.
  - And in general $P(\epsilon_1\cap\epsilon_2) = P(\epsilon_1|\epsilon_2)P(\epsilon_2)$.

## Min Cut problem

**PROBLEM DEFINITION:** Given a graph $G = (V,E)$, a *min cut* is a minimum-size subset of $E$ that disconnects the graph $G$. This problem can be connected to max-flow/min-cut (linear programming), for example.

**OBSERVATION:** Min-cut $\leq$ min degree (because we can isolate that vertex from the graph).

**ALGORITHM:** Choose and edge at random and contract it. Repeat until only 2 vertices left. We can convert the graph into a *multigraph* (repetition of same edges). The edges that separate the 2 final vertices is a *cut*.

It is a *Montecarlo algorithm*, because we pick the edges randomly.

### Analysis

**1st step:** Give a lower bound on the probability that the returned cut is minimum. Consider a minimum cut $C$ of size $k$. What can we say about $|E|$?.

**Handshake lemma:** $|E| \geq \frac{kn}{2}$.

Probability that the chosen edge $\in C \leq \frac{k}{k\frac{n}{2}} = \frac{2}{n}$. So we can also say that the probability that the chosen edge $\notin C \geq 1- \frac{2}{n}.$

$\epsilon_i$: we do not pick an edge of $C$ at the $i$th step.
  - $P(\epsilon_1) \geq 1 - \frac{2}{n}$.
  - $P(\epsilon_2 | \epsilon_1) \geq 1 - \frac{2}{n-1}$ (we have at least $\frac{k(n-1)}{2}$).
  - $P(\bigcap_{i=1}^{n-2} \epsilon_i) \geq \prod^{n-2}_{i=1}(1-\frac{2}{n-i-1}) = \prod^{n-2}_{i=1}(\frac{n-i+1}{n-i+1}-\frac{2}{n-i-1}) = \prod^{n-2}_{i=1}(\frac{n-i-1}{n-i+1}) = \frac{2}{n(n-1)}$ (because numerators cancel the denominators).

**2nd step:** Repeat $\frac{n^2}{2}$ times and pick the best probability of success (lower bound)? and to fail (upper bound)? $\leq (1 - \frac{2}{n^2})^{\frac{n^2}{2}}$.

Let's see:

$$1-x < e^{-x}$$
$$1-\frac{2}{n^2} < e^{-\frac{2}{n^2}}$$
$$(1-\frac{2}{n^2})^{\frac{n^2}{2}} < e^{-1}$$
Also:
$$\lim_{n\to\infty} (1 - \frac{1}{n})^n = \frac{1}{e}$$

So then the probability they *ALL* fail $\leq (1 - \frac{2}{n^2})^{\frac{n^2}{2}} \leq \frac{1}{e}$.

## Binary Planar Partitions

![](http://images.slideplayer.com/31/9720350/slides/slide_4.jpg)

**DEFINITION:** Binary Planar Partitions is a computational geometry problem. We have a set of line segments in the plane. The motivation of this problem is to optimize rendering in computer graphics (Binary Space Partitions - BSP $\to$ DOOM, with the walls, etc...).

The objective of this problem is to separate by bipartitions the set of $n$ disjoint line segments in the plane. We can use a tree structure (see image before). A leaf is then a cell in the plane partition.

**GOAL:** Randomized algorithm producing a BPP of size $O(n\log(n))$.

Special class of BPP = Autopartitions (partitions done on the segments).

![](http://images.slideplayer.com/31/9720350/slides/slide_7.jpg)

### Algorithm

**INPUT:** The set $\{s_1,s_2,...,s_n\}$ of segments.
**OUTPUT:** A binary autopartition.
  - 1.- Pick a random permutatoin $\pi$ of $\{1,2,...,n\}$.
  - 2.- *While* region contains more than 1 segment, we cut it with $l(s_i)$, where $i$ is the first index in $\pi$ such that $s_i$ cuts that region.

index($u$,$v$) = $i$ if $l(u)$ intersects $i-1$ segments before intersecting $v$ or $\infty$ if it does not intersect $v$ (visual representation in figure below).

**Event:** $u \dashv v = l(u)$ cuts $v$ in the partition. So $u\dashv v$ happens only if $u$ occurs in $\pi$ before any of the $u_1, u_2,\dots,u_{-1},v$.

![](http://images.slideplayer.com/31/9720350/slides/slide_12.jpg)

$$P(u\dashv v) = \frac{1}{i+1}$$
So we'll calculate then the total number of intersections:

- $C_{u,v} =$ $1$ if $u\dashv v$, $0$ otherwise.
- $E(C_{u,v}) = \frac{1}{index(u,v)+1}$
- $E($ total $\#$ intersections $)$ $= \sum_u\sum_{v\neq u} \frac{1}{index(u,v) + 1} \leq \sum_u\sum_{i = 1}^{n-1} \frac{2}{i+1} \leq n2H_n = O(n\log(n))$. 
