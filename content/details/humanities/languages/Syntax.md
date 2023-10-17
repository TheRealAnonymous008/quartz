* The study of how linguistic units are assembled to form larger, meaningful linguistic units.
* The aim is to distinguish between grammatical and ungrammatical sentences within the language.
	* Note: *Grammar is not [[Semantics|meaning]]*. Some sentences can be meaningless but grammatically correct (i.e., "Colorless green ideas sleep furiously").
	* There is a distinction between **prescriptive grammar**--that which has been taught to learners of the language, and **descriptive grammar**--how people actually use the language.
	* There is a distinction between **competence** -- studying what a language speaker would say without any distractions, and **performance** -- what people actually say in practice, including considerations of being interrupted mid-sentence or forgetfulness.

* **Topicalization** - a mechanism that establishes an expression as the sentence or clause topic by having it appear at the front of the sentence.
	* Expressions that can be topicalized are constituents.
	* In a parse tree, we may only topicalize phrases and individual words that pass the test of having them appear at the front of the sentence.

# Rules
* Syntactical rules can be described by using a parse tree, which specifies how to assemble linguistic units to form larger units.
	* Some key units in the parse tree. These are determined by the function of the word or phrase, the latter is determinable through constituent words in the phrase.
		* **Determiner** - a unit that occurs together with a noun serving to express reference to the noun
		* **Nouns** - functions as the name of a specific object
		* **Verbs** - a unit that conveys an action
			* **Transitive Verbs** - verbs that require an object to act upon.
			* **Intransitive Verb** - verbs that do not act upon an object.
			* 
		* **Adjective** - a unit that describes a noun.
		* **Adverb** - a unit that describes a verb.
		* **Pronoun** - a unit that substitutes a noun or noun phrase in the sentence.
		* **Adposition**  - used to express spatial or temporal relations or mark semantic relations for a word. This includes prepositions and postpositions.
	* In the parse tree,  the order we merge the linguistic units matters with respect to topicalization, and thus the overall meaning of the sentence
	* The **head** of a phrase is the word that determines the syntactic category of the phrase. Its sister in the tree is the **complement**.

	* Other categories
		* **Complementizer** - includes words that can be used to turn a clause into the subject or object of a sentence.
		* **Argument** - expressions that complete the meaning of a predicate.
		* **Adjuncts** - optional expressions that may be excluded without changing the meaning of a predicate.

* For each word in the language, we should specify its syntactical rules--which categories of words (or even which instances of words) can the word combine with to produce a syntactically correct constituent. This is called **selection** 
	* Arguments are typically subject to selection rules where they tend to prefer to merge with certain word classes. Adjunct are not like this.
	* If a head has both an argument and an adjunct, the argument is closer to the head. 
		* Thus, for a verb head, the argument is closer than any adjunct.

### Relations
* In a parse tree, we say that a node 
	* If  $A$ and $B$ are merged to common parent $M$, we say that $A$ and $B$ are **sisters** and $M$ is the **mother** of its **daughters**.
	* $A$ **immediately dominates** $B$ if $A$ is the parent of $B$.
	* $A$ **dominates** $B$ if $B$ is a part of the subtree where $A$ is the root (i.e., $B$ is anywhere below $A$ in the hierarchy)
	* $\alpha$ is a **constituent** if all and only the words in $\alpha$ are dominated by a single node (i.e., every word in $\alpha$ is dominated and no more.)
	* A node $A$ **c-commands** its sister node $B$, and all of its sister's descendants.
		* Another way to say this is that $A$ and $B$ do not dominate each other, and every node that dominates $A$, dominates $B$.

### Headedness
* A **head initial** language always puts its heads before its complements.
* A **head final** language always puts its heads after its complements.
* A **mixed-headed** language will put its head either before or after its complements depending on other syntactical rules.

### Rules
* **Projection Principle**: If a head selects for an argument, merge the head with the argument first and make the argument a **complement**.
	* **wh-movement** - a phenomenon in many (but not all language) where certain words (in English, the interrogative pronouns who, what, where, etc...), can move to another part of the clause.
		* For example: "Did you put *what* on the table" becomes "*What* did you put on the table"
		* The first sentence follows the Projection Principle (in terms of constructing the parse tree). We then perform a movement operation to get the second sentence.
		* Interesting phenomena observed in practice: 
			* There is no wh-movement to the right of the sentence.
			* When dealing with multiple wh-words, we either move none, one, or all of them and not in between.

* **Extended Projection Principle**: Clauses must contain a noun phrase or determiner phrase in the subject position. *Most verbs require meaningful subject*.
	* In the absence of any words that can ordinarily satisfy EPP in the sentence, use an **expletive** like a dummy word (it)
	* This can force movements in sentences, particularly observed when transitioning between active and passive voice. This is called **NP-movement**, where noun phrases are moved so that the sentence will have a subject.
	* *Idioms are always constituents*. That said, because of NP movement, we can spread the words in the idiom apart.
	* **VP-internal subject hypothesis** - all subjects, even the subjects of active sentences, originate in the verb phrase and are moved to their surface position. 

* **Final-Over-Final Constraint** - for certain parts of the tree. If $A$ has in its complement another head $B$, and if $A$ follows its complement, $B$ must follow its complement.

* **Verb Second (V2) Ordering** -  clauses with no complementizers must start with exactly one phrase followed by the verb.
	* There are no subject second or direct object second languages.

* **Shortest Movement Heuristic** - given various possible movements that can happen for a phrase, pick the one that requires the shortest path (nodes traversed up and down the tree from the initial position to the landing site.)

* **Ellipsis** - we can omit certain words in a sentence as they are implied by other synonymous words in the sentence.
	* **Parallelism** - two clauses should have parallel structures.
	* **Sluicing** - having an ellipsis at the end of a question. (i.e., "I ate something, but I don't know what (I ate)").
		* One theory why this happens is because create a complete sentence, and we can perform a wh-move, coupled with not pronouncing part of the sentence.
		* Another theory is that we form the incomplete sentence, and it is [[Semantics|semantically]] implied what the complete sentence is.
	* **Preposition stranding** - having an option to move a prepositional phrase out or leave only the preposition at the end
	  
	  i.e., "Peter was talking with someone, but I don't know (with) whom?" so that we can ask either
	  
	  Who was he talking with?
	  With whom was he talking?
# Links
* [[Morphology]] - more on morphemes.

* [[Linguistics]]