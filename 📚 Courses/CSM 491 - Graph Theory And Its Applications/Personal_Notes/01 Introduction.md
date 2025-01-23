---
date: 2025-01-23
course: CSM 491 - Graph Theory And Its Applications
tags:
  - personal
  - study
  - CSM491
---

## **Overview**

- Graph theory started with Euler who was asked to find a nice path across the seven Köningsberg bridges
	![[Pasted image 20250123062431.png]]
#### Kirchhoff and Cayley
- Kirchhoff developed the theory  of trees in 1847 to solve the linear  equations in branches and  circuits of an electric network.
- In 1857, Cayley discovered the trees. Later he engaged in enumerating the isomers of  saturated hydrocarbons with a given number of carbon atoms.
#### Applications of Graph Theory
- Psychology (Lewin 1936, life-space of an individual)
- Theoretical physics
- Probability
- Study of network flows
- Gant charts
#### Graphs
- Its a diagram consisting of sets of points and lines joining certain pairs of these points.
- G is an ordered triple (V, E, ψG)
	- V -> nonempty set of vertices **(points)**
	- E -> Set of edges **(Lines joining points)**
	- ψG -> incidence function
#### Terminology
- Adjacent edge -> 2 vertices which are incident with a common edge
- Loop -> An edge with identical ends
- Link -> An edge with distinct ends
- Finite Graph -> Both the vertex set and edge set are finite
- Simple Graph -> It has no loops and no 2 of its links join the same pair of vertices.
#### Isomorphism
- Its a way to determine if 2 graphs are structurally the same, even if their visual representation or labels differ.
- Two graphs *G* and *H* are **isomorphic** if there exist **bijections** (one-to-one and onto mappings)

1. $\Theta: V(G) \to V(H)$: A mapping between the **vertices** of **G** and **H**.
2. $\Phi: E(G) \to E(H):$ A mapping between the **edges** of *G* and *H*.

These mappings must preserve the structure of the graph. Specifically:

- If two vertices $u$ and $v$ are connected by an edge $e$ in $G$, then their images $\Theta(u)$ and $\Theta(v)$ in $H$ must also be connected by the corresponding edge $\Phi(e)$ in $H$.
- The incidence relationship between edges and vertices must remain intact.
##### Further Breakdown
- $ψG​(e)=uv:$ In graph $G$, the edge $e$ connects vertices $u$ and $v$.
- $\psi_H(\Phi(e)) = \Theta(u) \Theta(v):$ In graph $H$, the edge corresponding to $e$ (via $\Phi$) connects the vertices corresponding to $u$ and $v$ (via $\Theta$).

This means that the connectivity of the graph $G$ must be preserved when mapped to $H$.

If two graphs are isomorphic:

- They have the same number of vertices and edges.
- The connections between vertices in one graph can be rearranged (via the bijections) to match the connections in the other graph.
#### Complete Graph
- Each pair of vertices is joined by an edge.
A graph is **complete** if:
1. It is **simple**, meaning:
    - No loops (edges connecting a vertex to itself).
    - No multiple edges between the same pair of vertices.
2. Every pair of distinct vertices is connected by a single edge.
##### Properties of a Complete graph
- **Number of Vertices**: A complete graph $K_n$​ has $n$ vertices.
- **Number of Edges**: The total number of edges in $K_n​$ is: 

$$
\binom{n}{2} = \frac{n(n-1)}{2}​ 
$$

This is because each pair of vertices has exactly one edge.
- **Degree of Each Vertex**: In $K_n$ ​, every vertex is connected to all other $n-1$ vertices, so the degree of each vertex is $n-1$.
- **Graph Density**: A complete graph is the densest simple graph possible since every vertex is connected to every other vertex.
	![[Pasted image 20250123072347.png]]
#### Bipartite Graph (Empty Graph)
- It's a type of graph where the vertices can be divided into **two disjoint sets** such that **no two vertices within the same set are connected** by an edge. Instead, edges only exist between vertices in the two sets.
	![[Pasted image 20250123072222.png]]

#### Complete Bipartite Graph
Denoted $K_{m,n}$​ , is a special type of **bipartite graph** where every vertex in one subset of vertices is connected to every vertex in the other subset.
##### Properties
- **Number of Vertices**:

$$
    ∣V∣=m+n
$$

	The total number of vertices is the sum of the vertices in $V_1$​ and $V_2$​.
    
- **Number of Edges**:

$$
    ∣E∣ = m \cdot n
$$

	Since every vertex in $V_1$​ is connected to every vertex in $V_2$​, the number of edges equals $m \times n$.
    
- **Degree of Each Vertex**:
    - Each vertex in $V_1$​ has a degree of $n$ (connected to all $n$ vertices in $V_2$​).
    - Each vertex in $V_2$ has a degree of $m$ (connected to all $m$ vertices in $V_1$​).
- **Planarity**:
    - A complete bipartite graph $K_{m,n}$​ is planar (can be drawn without crossing edges) if and only if $m \leq 2$ or $n \leq 2$. For larger $m$ and $n$, the graph is non-planar.
	![[Pasted image 20250123073512.png]]
#### Planar Graph
- 

## **Key Concepts**

- Two graphs are **isomorphic** if their structures (connections) are identical under some relabeling.
- Each pair of points (vertices) is joined by an edge (Lines) in Complete Graph

## **References**
![[GRAPH THEORY AND APPLICATIONS[2].pptx]]
