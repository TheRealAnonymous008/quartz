* **Genetic [[Programming]]** is an evolutionary algorithm where individuals are programs and every generation, programs are transformed using [[Genetics|genetic]] operations (crossover and mutation)
* *One advantage of GP is interpretable programs*

* In GP, it is important to maintain population diversity. This can be done  by:
	* Not allowing reproduction
	* Use mutation
	* Use small tournament sizes or uniform random selection.
	* Splitting large populations into semi-isolated subgroups. 
	* Use fitness sharing.

# Primitives
* In genetic programming, we represent a program using its [[Compiler Theory|Abstract Syntax Tree]] (alternatively prefix notation)
	* We refer to internal nodes as **functions** and end nodes as **terminals**. Both are referred to as **primitives**
	* If we have more complicated programs, we may use an entire forest. 
	* The overall structure of the subtrees in the forest is called the **architecture** of the program.
	* *The choice of primitives to allow may introduce unintended biases*.
* In GP, we first initialize the population. The following are some ways to do this
	* **Full** - nodes are taken at random from the function set until the maximum tree depth is reached. After which, we only choose terminals. 
		* It generates trees with a known size and shape
	* **Grow** - nodes are selected from both the primitive set until the depth limit is reached. After which, we only choose terminals. 
		* It generates trees of varying structures.
		* It is sensitive to the size of the function and terminal set. Larger = deeper
	* **Ramped Half and Half** - a mix of Full and Grow. Half the population is constructed with Full and the other half with Grow.
		* This uses a range of depth limits (a ramp)
		* It allows trees of varying shapes and sizes.
	* *Using domain knowledge*. If knowledge about the intended use of the program is known, we can use this to seed the initial population.
		* When doing this, make sure the population remains diverse across generations

* The terminal set typically consists of 
	* *External inputs* - typically in the form of external variables.
	* *Functions with no arguments* - which either return different values at different invocations or produce side effects. [^tset]
	* *Constants* 
* The function set typically depends on the domain of the application. They also include standard programming constructs
	* Arithmetic
	* Mathematical Functions
	* Boolean Operations
	* Conditionals
	* Loops

* *Function sets need to have **closure*** which means the following
	* **[[Type Theory|Type]] Consistency** - any subtree can be used in any of the argument positions for every function in the function set. [^consistency].
	  
	  An alternative to this is to include type information and constrain operations (i.e., crossover and mutation) so they do not perform illegal operations. 
		* Constraints can be enforced in the following ways.
			* **Structure Enforcement** - if a particular structure is believed or known to be important or sensible, we require all individuals to have that structure.  
			  
			  Additionally, we can constrain genetic operations to preserve this structure. 
			  
			  Alternatively, we can treat each structure as a component to be evolved and then merge them together.
	
			* **Strong Typing** - incorporate types and their constraints into the GP system. All genetic operations are made to not violate these type constraints.
	
			* **Grammar Based Constraints** - use a defined grammar to express the constraints allowed. 
		  
			  Genetic operations are restricted to only swapping sub-trees deriving from a common non-terminal symbol in the grammar. 
		  
			  This also lends itself well to **Grammatical Evolution**. Programs are represented as a sequence of integers which correspond to the rules in the grammar. We interpret this sequence as defining the choice in each production rule to use in derivation.

		* *Using constraints both limits the search space at the cost of additional complexity*. 
			* Systems that focus on syntactic constraints (i.e., grammar-based) require less machinery than those that focus on semantic constraints (i.e., types). 
			* For semantic constraints, the problem is that the system may become heavily biased towards programs that only satisfy the type system but are otherwise not performant.
			  
			  Generating such programs also becomes difficult.
			* For syntactic constraints, the problem is more tied to designing the grammar so that it is unbiased. 

	* **Evaluation Safety** - many operations can fail in various ways. 
	  
	  Functions should either always throw exceptions and handle them safely or we should penalize programs that throw errors. [^eval_safety]


* The primitive set should be **sufficient**. It should be able to represent all possible solutions to the problem
	* An alternative to this is not to represent the solution as a program, but *have the program generate a solution at runtime*. 

* We can make use of **Automatically Defined Functions** which simulate subroutines and classes. *This allows nodes to reuse already defined functions*. 
	* ADFs are defined as their own trees independent of the main program tree.
	* ADFs are typically bound to their own instance of the main program in the population
	* Other Automatically Defined Components (i.e., loops, iterations, and recursions) can also be used to add reuse.

* The overall architecture of the program can be determined in three ways
	* The architecture is pre-defined prior to the run.
	* We use evolutionary selection of the architecture.
	* We alter the architecture itself. 

[^tset]: When using random number generators, it is common to use **ephemeral random constants**. Every time the terminal is chosen for either constructing a new tree or mutation, a different random value is generated for that particular terminal (which is treated as a constant when that terminal is ran). We denote this with $\mathcal{R}$.
[^consistency]: If we introduce type coercion (which is possible as a design decision), we should be careful of introducing bias. 
[^eval_safety]: The danger with penalizing programs is if too many of the population throw errors, then the penalty does not select "fit" programs well enough.

# Crossover
* **Subtree Crossover**
	* Given two parents, randomly select a crossover point in each parent tree. 
	* Then create offspring by replacing the subtree rooted at the cross-over point with a copy of the subtree rooted in cross-over point of the other parent.
	* *Selection of crossover points should not be uniform* since most of the time we will end up selecting terminals. Choose 90% functions, 10% terminals. 

* **One point crossover** - select a common crossover point in both parent programs and then swap the corresponding subtrees
	* Prior to this, we analyze the topology of the trees. We only select from regions on the trees that have the same topology (same degrees)

* **Context Preserving crossover** - select the same crossover point on both trees, but without One Point Crossover's restriction of sampling from a common region.

* **Size-Fair Crossover** 
	* Select a crossover point from the first parent. 
	* Then, the size of the subtree to be excised is calculated which constrains the choice of the second crossover point. 
	* The goal is to preserve size and to make sure the subtree from the second parent that is excised is not too big.

# Mutation
* **Subtree Mutation** - randomly select a mutation point in the tree and substitute the corresponding subtree with a randomly generated sub-tree.
* **Point Mutation** 
	* Select a random node in the tree and replace the primitive in that node with another primitive of the same arity. 
	* If no such alternative exists, nothing happens.
	* We can mutate multiple nodes independently

* **Hoist Mutation** - the new subtree is selected from the subtree being removed from the parent with the guarantee the new program is smaller than the parent.
* **Shrink Mutation** - a special case of subtree mutation where a randomly chosen subtree is replaced by a randomly chosen terminal with the goal of preventing bloat.

* **Mutating Constants** - we can apply mutation on the constants defined within nodes as well
	* Use Gaussian noise. 
	* Use Gradient Ascent or other optimization algorithms.

# Fitness
* We use a **fitness function** to quantify the program's performance.

* One issue is that *some metrics may require us to run the programs*. Thus, we typically use interpreters or find ways to reduce the runtime cost.
	* We can enforce a time limit for each program. This is especially useful if we have iteration or recursion.
		* **Maxwell System** - the program gains fitness over time. At the cutoff, we then get the accumulated fitness.
		  
		  If all programs used the same number of CPU quanta, then the fittest program is the winner.
		  
		  Otherwise, we restart interrupted programs on where they were until it has used as much CPU as the others.
		* **Teller System** - all programs are run for the same amount of time. After which, an answer is extracted. 
	* Another alternative to reducing the computation cost is *run the less costly fitness functions first*. 
	  
	  We organize a run in stages. Each stage has an associated fitness function and a threshold that individuals must meet to proceed. 
	* **Backward Chaining** - use tournament selection with small tournament sizes. 
	  
	  Even if we repeat this multiple times, when the tournaments are small there is a significant probability an individual is never chosen. 
	* *Use caches* to store values and reduce recomputation of a particular subtree. This is useful if we know in advance which test cases are used. *Caches are preserved on crossover and reset on mutation*
	  
	  Caches higher up on the tree may need to be re-evaluated. 

* We can also use **fitness cases** which act as specific test cases for the evaluated program. 
	* *When doing this, we should make sure the fitness function is dynamic*
	* We can use holdout sets and change the elements of the test sets as needed to reduce overfitting.

* Many practical applications are multi-objective so we can have combinations of fitness measures.
* Sometimes, we need not run the program to evaluate it. We only need to determine, using this fitness metric, which programs should get children.
	* We can use tournaments for selection.
	  
	  As a general rule, if $T$ is the tournament size, about $\log_T(\text{Pop Size})$ generations are needed for the whole population to become descendants of a single individual.

# Theory
* Although the number of programs of a particular length grows exponentially with length, beyond a certain threshold, the fraction of programs implementing any particular functionality is effectively constant. 
* *Typically GP suffers from **bloat***. That is, at some point, programs rapidly grow in size (no. of nodes) but a comparable increase in fitness was not  observed.  Some theories to explain bloat are:
	* **Replication Accuracy Theory** - the success of a GP individual depends on its ability to have offspring functionally similar to the parent, so *GP evolves towards bloated representations that increase replication accuracy*
	* **Removal Bias Theory** - inactive code in the tree is low. Crossover events excising inactive subtrees produce the same fitness as their parents. *On average, the inserted subtree is bigger than the excised one* so offspring are bigger on average with more inactive code.
	* **Nature of Program Search Spaces Theory** - Above a certain size, the distribution of fitnesses does not vary with size. Since there are more long programs, the number of long programs of a given fitness is greater than the number of short programs of the same fitness. Over time *GP samples longer and longer programs simply because there are more of them*
	* **Crossover Bias Theory** -  On average, crossover does not produce growth or shrinkage (since we do not add new material that wasn't already in the population). However, *crossover pushes the population towards a highly skewed distribution* where there are more small programs. Small programs do not typically solve the problem, so we are *biased towards selecting programs that are longer on average* which affects mean program size. 

# Extensions
* **Developmental Genetic Programming** involves using indirect representations. Programs do not solve the problem but generate solutions to solve the problem. The quality of such solutions is then assessed as the program's fitness
	* This allows indirect representations to be used and manipulated by GP. 
	* This comes at the cost of introducing an additional genotype to phenotype decoding step.

* **Linear Genetic Programming** - instead of ASTs, we represent programs as a sequence of instructions similar to assembly or machine code
	* Motivated by how computer programs are represented in a linear fashion. 
	* It allows for speedups in execution because we no longer have to use a tree-based interpreter. 
	* It allows for rapid analysis.

* **Graph-Based Genetic Programming** - instead of ASTs, we extend and use more graphs. 
	* It requires more complex representations
	* It allows for the exploration of more complex programs (i.e., logic networks, FSAs, and neural networks)
	* It allows for evolving parallel programs
	* **Cartesian GP** - a subvariant where programs are represented by linear chromosomes of integers. 
		* They are grouped into threes or fours. Each group has an associated position on a 2D array. 
		* Other elements of the group determine the location on the 2D array that the primitive should read. 

* **Parallel Genetic Programming** - apply parallelization techniques to speedup training and evaluation or to simulate the fact that evolution in nature happens in parallel. 
	* **Master-Slave GP** - all genetic operations are ran on the same computer. All fitness functions are ran across a distributed network of computers
	* **Geographically Distributed GP** - the population is divided into sub-populations and the exchange of individuals among populations is limited by a migration limit, and the geography that constrains which populations can communicate with which.

# Links
* [[Genetic Programming An Introduction and Tutorial with a Survey of Techniques and Applications by Langdon et al|Langdon et al.]]