* A **Flow Network** is a weighted [[Directed Graph|digraph]] where the edges have a flow and capacity, and there is exactly one source vertex, and one sink vertex 
	* The **sink vertex** has exactly $0$ outdegree.
	* The **source vertex** has exactly $0$ indegree

* The **capacity** is a function denoted $c$ which assigns each edge in the flow network a non-negative real number. 
* A **flow** in a flow network is a function $f$ that assigns each arc in the flow network to a non-negative real number (called the *flow of an arc*) such that the following constraints hold 
	* **Capacity Constraint** - the flow of each arc is no greater than the capacity of each arc. 
	* **Flow Conservation Constraint** - for each vertex, the total flow that comes in the vertex is the same as the total net flow leaving the vertex. 
	  $$
	  \deg^-(v) = \deg^+(v)
	  $$
* The **value** of a flow between vertices $s$ and $t$ is calculated as 
  
  $$
  |f| = \sum_{v\mid sv\in E} f_{sv} = \sum_{v\mid vt\in E} f_{vt}
  $$

# Augmenting Paths and Residual Networks
* A **pseudo-flow** $f$ is a function on each network which satisfies.
	* The capacity constraint.
	* For arc $uv$, $f(u,v)=-f(v,u)$
* The **residual capacity** of an arc $a$ under the pseudo-flow $f$ is the difference between the capacity and the flow of the arc.
* The **residual network** represents the amount of flow that can be transferred across the flow network. 
	* It is obtained by having each arc in the flow network have the residual capacities as their weight.
* An **augmenting path** is a [[Trails, Walks, Paths and Cycles|path]] in the residual network from the source $s$ and sink $t$ and where a flow is available from $s$ to $t$ satisfying the constraints of flow.
* The **bottleneck** of a flow network is the minimum residual capacity of all edges in a given augmenting path.


* The **maximum flow** in a flow network is the maximum value of a flow from source to sink.
	* A network is in maximum flow if and only if there are no augmenting paths.
* The **minimum cut** of a flow network is an edge cut that separates the source and skink in such a way that the capacity of the cut is minimized.

* Computing the max flow can be formulated as a [[Linear Programming]] problem. 
  $$
    \begin{split}
    \text{maximize } & \ \ \ \ \ \sum_{v\mid sv\in E} f_{sv} \\ 
    \text{subject to} & \ \ \ \ \ f_{e} \le c_e & \forall e \in E & \text{ (capacity constraint)}\\ 
    & \ \ \ \ \ \sum_{x | xv \in E} f_{xv} = \sum_{y | vy \in E} f_{vy} & \forall v \in V & \text{ (flow conservation constraint)}\\
    & \ \ \ \ \ f_{e} \ge 0 
    \end{split} 
    $$

# Key theorems
* **Max-Flow Min Cut Theorem** - In any flow network, the maximum flow is equal to the capacity of the minimum cut. 
	* The capacity constraint restricts $\max f \le \min c$. 
	* Generating a residual network by finding  an augmenting path $p$ of bottleneck $c_p$  and increase the flow up to a limit by increasing the flow from $u$ to $v$ by $c_p$ and decreasing the flow from $v$ to $u$ by $c_p$. 
	* The new flow no longer contains the augmenting path $p$. We either augment with $0$ or with the maximum capacity of the new flow. 
	* When the process terminates, we have the maximum flow, and at least the minimum capacity. Hence $\max f \ge \min f$,

* The Max-Flow Min-Cut Theorem is an analogue to the [[Primal-Dual Scheme]] with the Max-Flow problem as the primal and the Min-Cut problem as the dual. 
# Links
* [[Introduction To Graph Theory by Wilson]]