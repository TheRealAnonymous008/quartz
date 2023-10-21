* Finite Automata represent computers that have a very small amount of memory, encapsulated using states. 
* They are computationally equivalent to Regular Languages--all regular languages can be expressed with a Finite Automata, and all Finite Automata can compute Regular Languages
# Finite Automaton
### DFA
* A **finite automaton** is a five tuple $(Q, \Sigma, \delta, q_0, F)$ consisting of 
	* A finite set of states $Q$
	* A finite set of input symbols called the alphabet $\Sigma$
	* A transition function $\delta: Q\times \Sigma\to Q$ 
	* An initial state $q_0\in Q$
	* A set of accept states $F\subseteq Q$.

* Let $w=a_1a_2\dots a_n$ be a string over the alphabet $\Sigma$. The automaton **accepts** the string $w$ if a sequence of states $r_0, \dots, r_n \in Q$ satisfying the following conditions
	1. $r_0=q_0$
	2. $r_{i+1}=\delta(r_i,a_{i+1})$ for  $i=0,\dots, n-1$
	3. $r_n\in F$.
* The set $A$ of all strings over $\Sigma$ that is accepted by finite automaton $A$ is the **language** of $M$, and that $M$ **recognizes** $A$, and that $A=L(M)$. 

### Transducer
* A **finite transducer** is a five tuple $(Q,\Sigma, \Gamma, \delta, q_0)$ consisting of: 
	* A finite set of states $Q$
	* An alphabet of input symbols $\Sigma$
	* An alphabet of output symbols $\Gamma$
	* A transition function $\delta: Q\times \Sigma \to Q\times \Gamma$
	* An initial state $q_0$.

* The transducer behaves like a regular automaton, except after each transition, it outputs a symbol. (for the **Mealy variant**). It can be modified to a **Moore machine** if we have every output be on the state.

* A **general state transducer (GST)** extends the transducer but allows for more than one output symbol on a transition function 

### Two-Way DFA
* A **two-way DFA** is an $8$ tuple $(Q,\Sigma,L,R,\delta,s,t,r)$ where
	* $Q$ is the finite non-empty set of states.
	* $\Sigma$ is the alphabet.
	* $L$ is the left end marker
	* $R$ is the right end marker.
	* $\delta : Q\times (\Sigma \cup \{\text{L},\text{R}\})\to Q\times \{\text{left}, \text{right}\}$
	* $s$ is the start state.
	* $t$ is the accept state.
	* $r$ is the reject state.

* $\forall q\in Q$ 
  $$
  \begin{split} \delta(q,L)&=(q', \text{right}) &
  \text{ for some } q'\in Q \\
  
  \delta(q, R) &= (q',\text{left}) & \text{ for some } q'\in Q
  \end{split}
  $$
  That is, a transition is possible when reaching either end of the input word. 
* For all symbols $\sigma \in \Sigma \cup \{L\}$ 
  $$
  \begin{split} \delta(t,\sigma)&=(t,R) \\ \delta(r,\sigma) &= (r,L) \\ \delta(t,R) &= (t,L) \\ \delta(r,R) &= (r,L) \end{split}
  $$
  That is, once the automaton reaches the accept or reject state, it stays there forever, and the pointer goes tot he right most pointer and cycles there infinitely.
# Regular Languages
* A **regular language** is a language that is recognized by a finite automaton $M$.
* We may define **regular operations**
	* A **union** is defined as 
	  $$
	  A\cup B=\{w\mid w\in A \text{ or } w\in B\}
	  $$
	  
	* A **concatenation** is defined as 
	  $$
	  A\circ B = AB =  \{xy \mid  x\in A. y\in B\}
	  $$
	  
	* A **star** operator is defined as 
	  $$
	  A^\ast = \{x_1,\dots x_k\ \mid \text{each } x_i\in A \text{ for } k\ge 0\}
	  $$
	  
*  $R$ is a regular expression if $R$ is built from regular operations or symbols in the alphabet. That is, $R$ is: 
	* $a\in \Sigma$
	* $\lambda$
	* $\emptyset$
	* $R_1\cup R_2$ where $R_1$ and $R_2$ are regular expressions
	* $R_1\circ R_2$ where $R_1$ and $R_2$ are regular expressions
	* $R_1^\ast$ where $R_1$ is a regular expression.
	  
* *Theorem*: **Closure properties**:  [^1]
	* *Sipser 1.45*: If $A_1$ and $A_2$ are regular languages, then so is $A_1 \cup A_2$.
	* *Sipser 1.47*: If $A_1$ and $A_2$ are regular languages, then so is $A_1 \circ A_2$.
	* *Sipser 1.49*: If $A_1$ is a regular language, then so is $A_1^\ast$.
	* *Sipser e1.31*: If $A$ is a regular language, then so is its reversal $A^R$

[^1]: All these properties can be shown through the construction of finite automata.
* *Sipser 1.54*: A language is regular if and only if some regular expression describes it.
# Regular Grammars
* A **right linear grammar** is a formal grammar $(N,\Sigma,P,S)$ in which  all production rules in $P$ are of the following forms 
	1. $A\to a$
	2. $A\to aB$
	3. $A\to \lambda$
* A **left linear grammar** has all production rules of the form
	1. $A\to a$
	2. $A\to Ba$
	3. $A\to \lambda$
# Nondeterminism
### NFA
* A **deterministic** machine necessitates that the next state is exactly determined by the input symbol and previous states. Otherwise, the machine is **nondeterministic**.
	* In an NFA, a state may have zero, one, or many exiting arrows. We also allow a transition with input symbol $\lambda$.
	* Compared to a DFA, an NFA has a transition function defined by
	  $$
	  \delta:Q\times\Sigma_\lambda\to \mathcal{P}(Q)
	  $$
	  
* Every deterministic machine is nondeterministic.
* *Sipser 1.39*: Every NFA has an equivalent DFA.

* Computation is done in a similar way to DFAs except:
	* If more than one transition is possible, split computation into parallel branches, taking each transition.
	* If no transition is possible, the machine dies.
	* If $\lambda$ is encountered, we may transition to the outgoing state or stay in the current state.
	* If any computation branch ends on a final state, the NFA accepts the string.

### GNFA
* A **generalized NFA** is an NFA where transition arrows may have any regular expressions as labels instead of only members of the alphabet such that:
	* The start state has outgoing transitions to all states and no incoming transitions. 
	* The accept state has incoming transitions from all states and no outgoing transitions.
	* Except for the start and accept states, One arrow goes from every state to every other state and also from each state to itself 

* GNFAs are used to convert a DFA into a regular expression. This is done as follows:
		Let $G=(Q,\Sigma,\delta,q_s,q_a)$ be a GNFA
		Let $k=|Q|$ 
		If $k=2$, return the regular expression in the transition.
		If $k>2$, select $q_r\in Q$ that is not $q_a$ or $q_s$. Let $G'=(Q',\Sigma,\delta',q_s,q_a)$ be the GNFA where 
	  $$
	  Q'=Q-\{q_r\}
	  $$
	  and for any non-accept state $q_i\in Q'-\{q_a\}$ and non-start state $q_j\in Q'-\{q_s\}$ we have that 
	  $$
	  \delta'(q_i,q_j)=(R_1)(R_2)^\ast(R_3)\cup R_4
	  $$
	  Where 
	  $$
	  \begin{equation}
	  \begin{split}
	  R_1&=\delta(q_i,q_r) \\
	  R_2&=\delta(q_r,q_r) \\
	  R_3&=\delta(q_r, q_j) \\
	  R_4&=\delta(q_i,q_j)
	  
	  \end{split}
	  \end{equation}
	  $$
	  Repeat until $k=2$. [^2]

[^2]: The intuition is this: if we start at $q_i$ and end at $q_j$, either we can avoid passing through $q_r$ (expressed as $R_4$), or we do, in which case we have to: go $q_i\to q_r$, described by $R_1$,  possibly stay at $q_r$ described by $R_2$  then $q_r\to q_j$, described by $R_3$
### ANFA
* An **all-NFA** is a five tuple $(Q,\Sigma, \delta, q_0, F)$ that accepts $x\in \Sigma^\ast$ if every possible state that $M$ could be in after reading input $x$ is a state from $F$.
* *Sipser e1.38*: all-NFAs can recognize the class of regular languages. 

# Other Theorems
* *Sipser e1.52* **Myhill-Nerode Theorem**. Let $L$ be a language and $x$ and $y$ are strings. The *distinguishing extension* is defined as a string $z$ such that exactly one of $xz$ and $yz$  belongs in $L$. The relation $x\sim_L y$ is defined where $x$ and $y$ are indistinguishable (i.e., no distinguishing extension exists). This relation is an equivalence relation.
  
  $L$ is regular if and only if $\sim_L$ has a finite number of equivalence classes. 
  
  Moreover, the number of equivalence classes, called the *index*, is also the number of states in the minimal DFA accepting $L$.
  
  Any minimal DFA acceptor for the language is isomorphic to this one: 
  Let each equivalence class correspond to a state, and the state transitions are $a:[x]\to[xa]$ for each $a\in \Sigma$. The starting state is $[\lambda]$  and the accepting states are $[x], x\in L$.

# Nonregular Languages
* *Sipser 1.70*: The **Pumping Lemma**. 
  
  If $A$ is a regular language, then there is a number $p$ called the **pumping length** where if $s$ is any string in $A$ of length at least $p$, then $s=xyz$ where:
  1. $\forall i\ge 0$, $xy^iz\in A$.
  2. $|y|>0$
  3. $|xy|\le p$.
[^3]

[^3]: The reason the pumping lemma holds is because, for regular languages, we have a DFA that has as many states as the pumping lemma (i.e., a finite number of states). In such a DFA, by pigeonhole principle, we must have crossed at least one state twice via regular expression $y$.

* The pumping lemma implies that *every finite language is regular*. 

# Links
* [[Introduction to the Theory of Computation by Sipser|Sipser Ch. 1]]