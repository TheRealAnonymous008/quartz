* We develop different [[Models of Computation]] and study what classes of problems they can compute through Formal Languages.
# Definitions
* A **string** is a finite sequence of symbols in an **alphabet** $\Sigma$. 
	* The reverse of a string is defined as $\omega^R$.
* A **language** is a set of strings.
	* The reverse of a language is defined as $L^R$, which contains all the strings in reverse. That is $L^R = \{\omega^R \mid \omega \in L\}$
* The **empty string** $\lambda$ is the string of length $0$ 
* The **empty language** $\emptyset$ is the set with no strings.

* A **grammar** consists of a set of production rules. Each rule appears as a line comprising a symbol and a string separated by an arrow. The symbol is called a **non-terminal** and other symbols are called **terminals**. One variable is designated as the start non-terminal.
* More formally, a grammar $G$ is a tuple $(N,\Sigma,P,S)$ where 
	* $N$ is a finite set of nonterminal symbols that is disjoint with the strings formed from $G$.
	* $\Sigma$ is a set of terminal symbols.
	* A finite set $P$ of production rules.
	* $S\in N$ which denotes the start symbol. 
* The sequence of substitutions in the grammar needed to generate a string is called a **derivation**. All strings generated this way are called the **language of the grammar** denoted $L(G)$ for grammar $G$.
	* A **leftmost derivation** is a derivation where we replace the leftmost nonterminal in the production rule first.
	* If there is more than one derivation for a string, we say the string is generated **ambiguously** and the grammar is **ambiguous**.
	* A language is **inherently ambiguous** if it can only be generated with an ambiguous grammar.
# Topics
* [[Finite Automata and Regular Languages]]
* [[Deterministic Pushdown Automata and DCFLs]]
* [[Pushdown Automata and Context Free Languages]]
* [[Complexity Zoo]]
	* PPAD is an interesting complexity class. 
# Links
* [[Introduction to the Theory of Computation by Sipser]]

* [[Linguistics]] - Automata Theory is connected to Linguistics.
* [[String Algorithms]] - since Automata Theory is linked to Linguistics, algorithms that process strings are good to know.