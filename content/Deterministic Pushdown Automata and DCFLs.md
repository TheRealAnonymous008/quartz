# Deterministic Pushdown Automata
* *DPDAs are weaker than PDAs*.
* Formally, a **deterministic pushdown automata** is a $6$-tuple $(Q,\Sigma,\Gamma,\delta,q_0,F)$ where $Q,\Sigma,\Gamma$ and $F$ are all finite sets. We denote $\Sigma_\lambda = \Sigma\cup\lambda$ and $\Gamma_\lambda=\Gamma\cup\lambda$ 
	* $Q$ is the set of all states
	* $\Sigma$ is the input alphabet.
	* $\Gamma$ is the stack alphabet.
	* $\delta : Q \times \Sigma_{\lambda} \times \Gamma_\epsilon \to (Q\times \Gamma_\lambda)\cup\emptyset$ is the transition function.
	* $q_0\in Q$ is the start state.
	* $F\subseteq Q$ is the set of accept states.
* The transition function must satisfy the following. For every $q\in Q, a\in \Sigma, x\in \Gamma$ exactly one of the following is not  $\emptyset$
	* $\delta(q,a,x)$
	* $\delta(q,a,\epsilon)$
	* $\delta(q,\epsilon,x)$
	* $\delta(q,\epsilon,\epsilon)$
* If the output is $\emptyset$ we perform no action. Otherwise, we have a single move of the form $(r,y)$. *In a DPDA, there is no ambiguity*.
* Strings are accepted by the DPDA if the whole string is read and the machine is on an accept state. 
* Strings are rejected if we fail to read the whole string (i.e., because of being unable to pop the stack) or if we never land on the accept state.

# Properties
* *Sipser 2.42*: The class of DCFLs is closed under complementation. [^1]

[^1]: The idea is, first, make the DPDA amenable to complementation by only having accept states in states that read symbol. Then,  just make all accept states reject states and vice versa among reading states.

* An **endmarked input** is one where we have a special endmarker $\dashv$ that is appended to the input string and acts as a way to know when the string ends. An **endmarked language** is one where all strings are endmarked, and it is denoted $A\dashv$.
* *Sipser 2.43*: $A$ is a DCFL if and only if $A\dashv$ is a DCFL.
# Links
* [[Introduction to the Theory of Computation by Sipser|Sipser 2.4]]
* [[Pushdown Automata and Context Free Languages]] - more on PDAs