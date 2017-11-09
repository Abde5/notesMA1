# Introduction

## Convex Hull

$\forall p,q \in C$, $[p,q] \subseteq C$

**DEFINITION:** A segment $[a,b] = \{\lambda a+(1-\lambda)b : 0 \leq \lambda \leq 1\}$ (this is a convex combination).

**DEFINITION:** Convex combination of $n$ points $p_1,\dots,p_n$: $\{\lambda_1p_1
  +\lambda_2p_2+\dots+\lambda_np_n:\lambda_i\geq0,\ \  \lambda_1+\dots+\lambda_n=1\}$

![convex hull](http://axon.cs.byu.edu/Dan/312/projects/project2_files/image002.png)

**DEFINITION:** Convex Hull of a set $S\subseteq\mathbb{R}^2 : CH(S)$. Multiple definitions:
  - The unique "smallest" convex set $C$ that contains $S$.
  - $\bigcap_\mathbb{c:convex} c, S \subseteq c$
    - $c_1,c_2$ are convex $\to c_1\cap c_2$ is convex ($\forall p,q \in c_1\cap c_2$; $p,q \in c_1$ and in $c_2$; $[p,q] \subseteq c_1$ and $c_2$; $[p,q] \subseteq c_2$)
  - $CH(S)\ \ \ S={p_1,p_2,\dots,p_n}$ = conv. comb of $p_1,p_2,\dots,p_n$.
  - $CH(S)= \bigcup_{p,q,r \in S} \triangle pqr$

**CARATHEODORY'S THEOREM:** if $x$ is a convex combination of $p_1,\dots,p_n \in \mathbb{R}^d \Rightarrow x$ is a convex combination of just $(d+1)$ of them.

$$x = \sum^n_{i=1} \lambda_i p_i\ \ \ \ \ \ \lambda_i \geq 0,\ \ \sum\lambda_i = 1$$
- if $n = d+1$: done.
- if $n > d+1$: look at the vectors $p_2-p_1, p_3-p_1,\dots,p_n-p_1$ ($n-1 > d$ vectors).

$\sum^n_{i=2} \mu_i (p_i-p_1) = 0\ \ \ \mu_i$ not all $\varnothing$ (so the vectors are independent).

$0 = (\sum^n_{i=2}-\mu_i)p_1 + \sum^n_{i=2}\mu_i p_i = \sum^n_{i=1}\mu_ip_i$

So then we can say that: $x = \sum^n_{i=1}\lambda_ip_i + \alpha\sum^n_{i=1}\mu_ip_i =
\sum_{i=1}^n(\lambda_i + \alpha \mu_i)p_i$

We want $\lambda_i + \alpha \mu_i$ to be positive, so we can say that $\lambda_i + \alpha\mu_i \geq 0 \Rightarrow \alpha \geq \frac{-\lambda_i}{\mu_i}$ s,t, $\mu_i > 0 \Rightarrow \alpha \leq \frac{-\lambda_i}{\mu_i}$ s.t. $\mu_i < 0$

Algorithm (in general):

```
for all a:
  for all b:
    for all c:
      for all d:
        if d in abc triangle:
          Throw it away
```

## Algorithms for computing $CH(S)$

- $\forall a,b,c$: remove every point in $\triangle abc \Rightarrow O(n^4)$ -> FINDS EXTREMAL POINTS (not in a convex combination of others)
- + $O(n\log n)$ to find the order (quicksort) -> we take the orient determinant as the comparaison function in the sort.
- $O(n)$ to decide if a point is extremal (with half planes)
  - On every point $O(n)$
- Gift Wrapping algorithm or Jarvis March $\Rightarrow O(nH)$ ($H$ = size of convex hull)
- Graham Scan $\Rightarrow O(n\log n)$ because of the radially sorting.

Graham Scam Algorithm:
```
find point with minimum x coordinate
sort all other points radially using the orientation determinant
STACK Q = [p1,p2]
for i=3 to n:
  while [Q.top()-1,Q.top(), pi] is a right turn:
    Q.pop()
  push p_i
```
TO IMPLEMENT FOR HOMEWORK (GRAHAM SCAN OR MONOTONE GRAHAM SCAN).
