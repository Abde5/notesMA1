# Practical information

  - Prof: Gwenaël Joret
  - Référence: Graph Theory 5th edition (Reinhardt Diestel)

# Overview

  ## Matchings

  Graph = Finite, simple, undirected graph.
  - simple: without multiple edges or self edge

  **DEFINITION:** Graph is $G=(V,E)$, where $V$ is a set of vertices and $E$ is a set of edges.

  **CONVENTION:** We simply write $ab$ instead of $(a,b)$ for edges.

  **DEFINITION:** If G is a graph, we use $V(G)$ to denote the vertex set of G.

  **DEFINITION:** If G is a graph, we use $E(G)$ to denote the edge set of G.

  **DEFINITION:** H is a *subgraph* of G if $V(H)\subseteq V(G)$ and $E(H)\subseteq E(G)$.

  **DEFINITION:** H is a *induced subgraph* of G if it's a subgraph of G and $\forall v,w \in V(H), v \neq w : vw \in E(H) \Leftrightarrow vw \in E(G)$.

  **DEFINITION:** Two edges are independent if they do not have a vertex in common.

  **DEFINITION:** A *matching* is a set independent edges.

  **DEFINITION:** A graph is bipartite if $\exists$ bipartition $A,B$ of $V(G)$ so that each edge of $G$ has one end point in $A$ and the other in $B$.

  **DEFINITION:** Marriage problem: is there a matching of size $n$ in a bipartite graph $G$?

  **THEOREM (HALL, 1935):** Given a bipartite graph $G$ with bipartition $A,B$, there exists a matching covering $A$ *if and only if* $|N(S)| \geq |S| \ \ \ \ \forall S\subseteq A$ ($N$ = neighbours, $S$ = subset).

  **DEFINITION:** A vertex cover is a subset $X\subseteq V(G)$ so that every edge of $G$ has at least one endpoint in $X$.

  **THEOREM (König, 1931):** In a bipartite graph, the maximum size of a matching = the minimum size of a vertex cover.

*Clarification:* In every graph $G$, the min. size of a vertex cover is $\geq$ the max size of a matching.

  **THEOREM (Tutte, 1961):** A graph $G$ has a *perfect matching* (matching covering all of $V(G)$)
  $\Leftrightarrow|S| \geq q(G-S)\ \ \ \ \  \forall S\subseteq V(G)$

  **NOTATION:** $q(G) =$ number of odd components of $G$.

  **THEOREM (Menger, 1927):** Given a graph $G$ and $A,B \subseteq V(G)$ the maximum number of $A-B$ disjoint paths = the minimum size of a set $X\subseteq V(G)$. separating $A$ from $B$ in $G$.

  **NOTATION:** $X$ separates $A$ from $B$ if $\nexists A - B$ path in $G - X$.

## Connectivity

  **DEFINITION:** A graph $G$ is k-connected if $|V(G)| \geq k+1$ and $G-X$ is connected $\forall X\subseteq V(G), |X| \leq k-1$.

  **THEOREM (Tutte, 1961):** If $G$ is a 3-connected and $|V(G)| \geq 5$ then $\exists vw \in E(G)$ so that $G / vw$ is 3-connected.

## Planar graphs

  **DEFINITION:** $H$ is a minor of $G$ if $H$ can be obtained from $G$ using edge deletions, vertex deletions, edge contractions (in any order).

  *Planar graphs are closed under taking minors.*

  **COROLLARY:** Planar graphs on $n \geq 3$, vertices have $\leq 3n-6$ edges. And in case of bipartite planar graphs: $\leq 2n-4$.

Two key non-planar graphs:
  - $K_5$
  - $K_{3,3}$

  **THEOREM (Kuratowski, 1930):** G is planar $\Leftrightarrow$ neither $K_5$ nor $K_{3,3}$ is a minor of $G$.

  **THEOREM (Robertson-Seymour, 1970's $\to$ 2014):** Every minor-closed family of graphs is characterized by a *finite* set of excluded minors.

  $\chi(G):=$ chromatic number of $G$, which is the minimum number of colors in a vertex coloring of $G$,

  **THEOREM (Appel & Haken, 1977):** $G$ planar $\to \chi(G) \leq 4$.

  **THEOREM (Robertson-Seymour-Thomas-Sanders, 1995):** Reproved Appel & Haken.
