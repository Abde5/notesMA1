# Matchings

## Matchings in arbitrary graphs

**THEOREM (Tutte, 1947):** A graph $G$ has a perfect matching $\Leftrightarrow$ $|S| \geq q(G-S)$.

**DEFINITION:** $q(H):= \#$ odd components in $H$.

**PROOF OF $\Rightarrow$:** (check book, very visual)

**PROOF OF $\Leftarrow$:** Let's prove the contrapositive. Assume $G$ has no perfect matching, and let us prove that $\exists S \subseteq V$ so that $|S| < q(G-S)$. Such an $S$ is called a *witness*.

If $|V|$ odd then $S:=\varnothing$ is a witness so WMA $|V|$ even.

**OBSERVATION:** Say $H'$ obtained from a graph $H$ by adding an edge. Then $q(H') \leq q(H)$.

**OBSERVATION:** If $S$ is a witness for $G$ then $S$ is a witness for all spanning subgraphs $G'$ of $G$

**COROLLARY:** We might assume (WMA) that $G$ is edge-maximal without perfect matching (i.e. adding any edge creates a perfect matching). Indeed, if not, add edges until the graph is edge-maximal without a perfect matching, then find a witness (thanks to proof below), and this set is also a witness for the original graph.

**DEFINITION:** $S\subseteq V$ is *nice* if:
 - 1) each $v\in S$ is adjacent to all vertices in $V - {v}$, and
 - 2) each component of $G-S$ is a complete graph.

 **OBSERVATION:** If $S$ is nice then $S$ is a witness.

 **NOTICE:**
 - $|S|$ and $|X|$ have same parity (bss $|V|$ even) -> $X$ set of odd components.
 - $|X|$ and $q(G-S)$ have same parity.
 - $\Rightarrow |S|$ and $q(G-S)$ have the same parity.

If $|S| \geq q(G-S)$ then we can find a perfect matching in $G$ using so we must have $|S| < q(G-S)$. $\to$ new goal: find a nice subset (since this is enough).

Let  $S:=\{v\in V: v$ adjacent to every vertex in $V - {v}\}$. Then $S$ satisfies condition 1 of "nice".

**IDEA:** Assume $S$ does not satisfy condition 2. Then we will show that $G$ has a perfect matching using its "edge-maximality without a perfect matching" property, which is a contradiction.

Consider a component of $G-S$ which is *not* a complete graph. Let $a,a'$ be distinct vertices in that component so that $aa' \notin E(G)$. Consider a shortest path $P$ in the component linking $a$ to $a'$. Let $a,b,c$ the first three vertices of $P$. We know then that $ac \notin E(G)$.

Since $b\notin S, \exists d\in V-\{a,b,c\}$ so that $bd\notin E(G)$. By our assumption on $G$ :
- $G + ac$ has a perfect matching $M_1$.
- $G + bd$ has a perfect matching $M_2$.

**PLAN:** modify $M_2$ using part of $M_1$ to get a perfect matching avoiding $ac$ and $bd$, which is thus a perfect matching of $G$, a contradiction.

Let's look at $M_1\Delta M_2 = (M_1 - M_2) \cup (M_2 - M_1)$. This set of edges defines a subgraph of $G$ which is a collection of vertex-disjoint cycles, each of even size and alternating between edges from $M_1$ and from $M_2$.

Let $C$ be the cycle of $M_1\Delta M_2$ containing $bd$:
 - *Case 1: $ac\notin E(C)$*: Here we "switch" $M_2$ locally on $C$: $(M_1 - E(C))\cup (E(C) - M_2)$ is a perfect matching of $G$, contradiction.
 - *Case 2: $ac\in E(C)$*: Walk on cycle $C$ from vertex $b$ starting with edge $bd$. WLOG we reach $c$ before $a$. Let $C'$ be the cycle defined by the $bd\dots c$ path on $C + bc$. Then we can "switch" $M_2$ on $C'$ and get a perfect matching of $G$, namely $(M_2 - E(C'))\cup(E(C')-M_2)$ contradiction. (Here we use that $ac\notin E(C')$).
