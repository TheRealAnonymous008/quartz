# Breadth First Search 
### Recursive

```
BFS(G, v):
	if v not discovered:
		label v as discovered
	
	N := all u adjacent to v
	for each u in N:
		if u not discovered: 
			label u as discovered 

	for each u in N:
		BFS(G, u)
```

### Iterative

```
Q := queue()
label root as explored
Q.enqueue(root)

while Q is not empty:
	v := Q.dequeue()
	for all u adjacent to v:
		if u not discovered:
			label u as discovered
			Q.enqueue(u)
```

# Depth First Search 

### Recursive 
```
DFS(G, v):
	label v as discovered
	for each u adjacent to v:
		if u not discovered: 
			DFS(G, u)
```

### Iterative 

```
S := stack()
S.push(root)
while len(S) != 0: 
	v := S.pop()
	if v not discovered:
		label v as discovered 

		for all u adjacent to v: 
			S.push(v)
```

# Dijkstra's Shortest Path
* Let $G$ be a weighted graph.  We take in a source vertex $s$
  $d(v)$ be the distance of $v$ from source $s$ 
  $w(u,v)$ be the weight of edge $uv$
  $\text{prev}(v)$ be the previous vertex to $v$ in a hypothetical shortest path. 

```
for each v in V:
	mark v "unvisited"
	d(v) <- 0
	prev(v) <- NULL

d(s) = 0
Q := priority queue

Q.add(s)

while Q not empty:
	u <- Q.extract_min()
	for each neighbor v of u:
		d'< <- d(u) + w(u,v)
		if d' < d(v):
			d(v) <- d'
			prev(v) <- u
			Q.update_priority(v)
```

### Proof of Correctness 
* Let
  $R$ be the set of visited vertices thus far. 
  $u$ be the last visited vertex 
  $R'=R\cup\{u\}$.
  
  The base case is easy to see. For the inductive hypothesis, every vertex in $R'$ that isn't $u$ has the correct label (i.e., $d(x)=\text{dist}(s,x)$).
  
  Suppose that the shortest path from $s$ to $u$ is $Q$ and has length 
  $$
  \text{dist}(s,u)<d(u)
  $$
  
  i.e., we have a better path than what Dijkstra's algorithm outputs.
  
  Now $Q$ starts in $R'$ and leaves $R'$ to get to $u$ which is not in $R'$ as we have defined. 
  
  Let 
  $xy$ be the first edge on $Q$ that leaves $R'$.
  $Q_x$ be the $s,x$-subpath of $Q$. 
  
  We have that 
  $$
  \text{dist}(s,x)+\text{dist}(x,y)\le \text{dist}(s,u)
  $$
  Equivalently 
  $$
  \text{dist}(s,x)<\text{dist}(s,u)
  $$
  But by our hypothesis, we know that $d(x)\le \text{dist}(s,x)$ so
  $$
  d(x)+\text{dist}(x,y)\le \text{dist}({s,x})
  $$
  And since $y$ is adjacent to $x$, it must have been updated so that 
  $$
  d(y)\le d(x)+\text{dist}(x,y)
  $$
  Finally, since $u$ was selected by the algorithm, $u$ must have had the smallest distance label. We get the following inequality 
  $$
  d(u)\le d(y)
  $$
  Which gives us a contradiction when we apply all inequalities in reverse order. 
  $$
  d(u)\le d(y)\le d(x)+\text{dist}(x,y)\le \text{dist}(s,x) < \text{dist}(s,u) < d(u) 
  $$

# Fleury's Algorithm 
### Algorithm
* Let $G$ be an [[Trails, Walks, Paths and Cycles#Eulerian Graphs|Eulerian]] Graph. Then, the following construction is always possible and produces an Eulerian trail of $G$.
  
  Start at any vertex $u$ and traverse the edges in an arbitrary manner subject to only the following rules:
1. Delete the edges as they are traversed and if any isolated vertices arise, erase them too.
2. At each stage, use a bridge only when there is no alternative (i.e., choose only edges that would not cause the graph to be disconnected).

### Proof
* The algorithm works because we choose edges that do not cause the graph to be disconnected. By choosing to traverse bridges as last resorts, we maintain [[Graph Connectivity|connectivity]]
* It also always yields the complete Eulerian trail since there can be no edge of $G$ left untraversed when the last edge incident to $u$ is used. Otherwise, the removal of some earlier edge disconnected the graph, contradicting what we have established.

# Kruskal's Algorithm 
* A [[Spanning Trees and Forests|Minimum Spanning Tree]] algorithm
### Algorithm 

```
F := []

for each v in E:
	MAKE-SET(v)

S := sort(E)

for each e in S
	if FIND(u) != FIND-SET(v):
		F.add(e)
		UNION(FIND(u), FIND(v))

return F
```

* The algorithm exploits the Minimum Spanning Tree Cut and Cycle property. 

# Links
* [[Trails, Walks, Paths and Cycles]]