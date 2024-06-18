* **Boolean Algebra** is an algebra wherein values can be truth values ($T$ or $F$) and operators are **logical operators**

* A **Proposition** is a declarative statement that must be exactly one of TRUE or FALSE. The proposition's **truth value** denotes the relation of a proposition to its 

# Logical Operators
* **Conjunction (AND)** - denoted $P\wedge Q$ or $\bigwedge_{i=1}^n P_i$ for sequences  It is true if and only if $P$ and $Q$ are both $T$.

| P   | Q   | $P\wedge Q$ |
| --- | --- | ----------- |
| F   | F   | F           |
| F   | T   | F           |
| T   | F   | F           |
| T   | T   | T           |
* **Disjunction (OR)** - denoted $P\vee Q$ or $\bigvee_{i=1}^n P_i$ for sequences of propositions. It is true if at least one of $P$ and $Q$ are true

| P   | Q   | $P\vee Q$ |
| --- | --- | --------- |
| F   | F   | F         |
| F   | T   | T         |
| T   | F   | T         |
| T   | T   | T         |

* **Negation (NOT)** - denoted $\neg P$ or sometimes $\overline{P}$. It is the opposite truth value to the value given

| P   | $\neg P$ |
| --- | -------- |
| F   | T        |
| T   | F        |

* **NAND** - defined as the negation of the conjunction. It is false only when both inputs are true 

| P   | Q   | $\neg (P\wedge Q)$ |
| --- | --- | ------------------ |
| F   | F   | T                  |
| F   | T   | T                  |
| T   | F   | T                  |
| T   | T   | F                  |

* **NOR** - defined as the negation of the disjunction. It is true only when both inputs are false. 


| P   | Q   | $\neg (P\vee Q)$ |
| --- | --- | ---------------- |
| F   | F   | T                |
| F   | T   | F                |
| T   | F   | F                |
| T   | T   | F                |
* **Material Implication (IF)** - denoted $P\implies Q$. It is defined by the following truth table

| P   | Q   | $P\implies Q$ |
| --- | --- | ------------- |
| F   | F   | T             |
| F   | T   | T             |
| T   | F   | F             |
| T   | T   | T             |

* **Exclusive OR (XOR)** - denoted $P \oplus Q$ or $\bigoplus_{i=1}^nP_i$ for sequences. It is defined as true if exactly an odd number of its inputs are true


| P   | Q   | $P\oplus Q$ |
| --- | --- | ----------- |
| F   | F   | F           |
| F   | T   | T           |
| T   | F   | T           |
| T   | T   | F           |


* **Bidirectional Implication (IFF / XNOR)** - denoted $P\iff Q$ or $\overline{\bigoplus_{i=1}^n P_n}$ for sequences. It is defined as true if exactly an even number of its inputs are true


| P   | Q   | $P\iff Q$ |
| --- | --- | --------- |
| F   | F   | T         |
| F   | T   | F         |
| T   | F   | F         |
| T   | T   | T         |

# Properties of Logical Operations
* Logical operations satisfy the following properties

#### Double Negation
1. $\neg \neg P \equiv P$

#### Identity
1. $A\wedge 1 \equiv A$
2. $A\vee 0 \equiv A$

#### Domination
1. $A\wedge 0 \equiv 0$
2. $A\vee 1 \equiv 1$

#### Complements
1. $A\wedge \neg A \equiv 0$
2. $A\vee\neg A \equiv 1$

#### Commutativity
1. $A\wedge B \equiv B\wedge A$
2. $A\vee B \equiv B \vee A$
3. $A\leftrightarrow B \equiv B\leftrightarrow A$
4. $A\oplus B \equiv B\oplus A$

#### Associativity
1. $A\wedge (B\wedge C) \equiv (A\wedge B)\wedge C$
2. $A\vee(B\vee C)\equiv(A\vee B)\vee C$

#### Distributivity
1. $A\wedge (B \vee C) \equiv (A\wedge B)\vee (A\wedge C)$
2. $A\vee(B\wedge C)\equiv(A\vee B)\wedge (A\vee C)$
3. $A\wedge(B\oplus C)\equiv(A\wedge B)\oplus (A\wedge C)$
4. $A\vee(B\leftrightarrow C)\equiv(A\leftrightarrow B)\vee (A\leftrightarrow C)$

#### Idempotence
1. $A\wedge A \equiv A$
2. $A\vee A \equiv A$

#### Absorption
1. $A\wedge (A\vee B)\equiv A$
2. $A\vee(A\wedge B)\equiv A$

#### Redundancy
1. $(X\wedge Y) \vee (X\wedge \neg Y) \equiv X$
2. $(X\vee Y)\wedge (X\vee \neg Y)\equiv X$
3. $(X\vee \neg Y)\wedge Y \equiv X\wedge Y$
4. $(X\wedge \neg Y)\vee Y \equiv X\vee Y$

#### Consensus Law
1. $(X \wedge Y ) \vee (\neg X \wedge Z) \vee (Y\wedge Z)\equiv (X \wedge Y ) \vee (\neg X\wedge Z)$
2. $(X \vee Y ) \wedge (\neg X \vee Z) \wedge (Y\vee Z)\equiv (X \vee Y ) \wedge (\neg X\vee Z)$

#### De Morgan's Laws
1. $\neg (A\wedge B) \equiv \neg A \vee \neg B$
2. $\neg (A\vee B) \equiv \neg A \wedge \neg B$

#### Monotonicity
1. $A\rightarrow B \equiv (A\wedge C)\rightarrow (B\wedge C)$
2. $A\rightarrow B\equiv(C\vee A)\rightarrow (C\vee B)$
3. $A\rightarrow B \equiv (A\vee C)\rightarrow (B\vee C)$

#### Implications
1. Contraposition $$P\rightarrow Q \equiv \neg Q\rightarrow \neg P$$
2. Import-Export $$(P\rightarrow(Q\rightarrow R))\equiv(P\wedge Q)\rightarrow R$$
3. Negation $$\neg(P\rightarrow Q)\equiv P\wedge \neg Q$$
4. Disjunction $$P\rightarrow Q\equiv\neg P\vee Q$$
5. Commutativity of antecedents$$P\rightarrow(Q\rightarrow R)\equiv Q\rightarrow(P\rightarrow R)$$
6. Distributivity $$R\rightarrow(P\rightarrow Q)\equiv (R\rightarrow P)\rightarrow (R\rightarrow Q)$$


# Links 
* [[Set Theory]]