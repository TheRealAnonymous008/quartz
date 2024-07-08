* Note: We can study [[Syntax|grammar]] independently of meaning.
* *Interpretation does not exactly apply to the sentence that you hear*. 
	* We can elide (add ellipsis) to certain parts of the sentence so that additional words are implied but not pronounced
	* Inversely, the **Association with Focus** (i.e., stressing different words in a sentence) shows that the interpretation of the sentence changes with how we articulate the sentence.
		* We invite a substitution on the stressed word and assert something by association.
		* Even if we focus on one word, we can invite multiple meanings (for example if focus on the word implies focus on the word alone or a phrase the word is a part of.)

* **Compositionality** -- a hypothesis where once you specify the meanings of the parts of a sentence, you should have the meaning of the sentence.

* There are various meaning relations between words
	* **Synonyms** - words that mean the same thing.
	* **Antonyms** - words that mean the opposite thing.

* **Intension** - the function or procedure for determining the reference of a word / phrase (i.e., look at the thermostat)
* **Extension** - the value of the intension (i.e., the measurement in the thermostat)
* We have to be careful about substituting synonymous words / phrases. It has to be in line with whether or not the intension or extension is appropriate to use in the sentence.

# Basic Relations
* **Entailment** - $A$ entails $B$ if whenever $A$ is true, $B$ is true. (a.k.a. $A\implies B$)
* **Equivalence** - $A$ and $B$ are equivalent if $A$ and $B$ entail each other (a.k.a. $A\iff B$).
* **Contradiction** - $A$ and $B$ contradict each other if each entails that the other is false (a.k.a. $A$ XOR $B$ is true.).
* **Presupposition** - $A$ has presupposition $B$ if $B$ is an implicit assumption required for $A$ to be true or $A$ to be false. Crucially, either $A$ or $\neg A$ will hold but it only makes sense to talk about either if $B$ is true.
	* *Accommodating presuppositions* means that in discourse, people will take up their interlocutor's presuppositions unconsciously.
* **Implicature** - something that is generally inferred from hearing a sentence, even if this inference is not true.

# Quantifiers
* **Quantifications** can be used to introduce additional meanings for a particular noun phrase (e.g. universal quantifiers, existential quantifiers, and their negations)

* Some quantifiers can be both true and false (e.g., using existential quantifiers.)
* Some quantifiers do not follow the law of excluded middle.
* Natural language quantifiers are **conservative** which means for a phrase involving sets $A$ and $B$, we can replace $B$ with $A\cap B$ and get the same meaning.

* *Having multiple quantifiers in a sentence can introduce ambiguities*. One possible explanation of this is **quantifier raising (QR)** where the quantifiers are moved around the syntax tree, even though they are not moved around in the sentence (at least in English.)
	* It appears QR is limited by how quantifiers cannot escape the clauses they are in.
	* QR is subject to parallelism. That is, if one clause in the sentence has QR, then the other clause must as well.
* **Downward Entailment**: The following property holds for a quantifier $Q$. If "$Q$ $A$ are $B$"" is true, and $C\subseteq B$, 
  then "$Q$ $A$ are $C$" is true. 
  Examples of such a $Q$ are "No", "Few"

* **Upward Entailment**: The following property holds for a quantifier $Q$. If "$Q$ $A$ are $C$" is true, and $C\subseteq B$, 
  then "$Q$ $A$ are $B$" is true.
  An example of such a $Q$ is "All", "Every"

* Some quantifiers are neither upward nor downward entailing (i.e., "Exactly 10 of").

* **Negative Polarity Items** - Linguistic items that appear only in a sentence that connotes negation. These tend to *avoid upward entailing contexts*. 

* **Positive Polarity Item** - Linguistic items that appear only in a sentence that connotes affirmation. These tend to *avoid downward entailing contexts*. 

# Binding Theory
* Given noun phrase $NP$ and constituent $\alpha$, any noun in $NP$ cannot refer to any noun dominated by $\alpha$

* More generally in **Binding Theory** we have the following principles 
	* We say that $\alpha$ **binds** $\beta$ if $\alpha$ c-commands and corefers with $\beta$.  Otherwise $\alpha$ is **free**. 
	* Pronouns cannot corefer with something (i.e., refer to anything in the same clause / sentence). Thus, *pronouns must be free within the clause*.
	* Anaphors must refer to something in the same sentence. Thus, *anaphors must be bound within the clause*.
	* *R-expressions* (things that are neither pronouns or anaphors) *must be free*.
* Binding Theory is subject to **reconstruction**, that is, we consider the parse tree before any movements were performed.
* Binding Theory also reveals the presence of **invisible pronouns**

# Copy Theory
* **Copy Theory** posits that a movement operation on the [[Syntax|parse tree]] is simply a merge operation with an item in the lexicon, potentially even a copy of one of the words in the sentence.
* Because this may introduce redundancies, we have rules to govern when to pronounce certain words that have been "moved" 
* Thus, reconstruction really is just choosing, out of all instances of copies of the word, where to place the word.

# Links
* [[Linguistics]]