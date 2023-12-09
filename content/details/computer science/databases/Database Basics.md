# Schemas
* **Data Domain** - a usually named set of *atomic values* - each value is indivisible.  *We provide a description of the domain using data types or formats*. 

* **Data Definition Language** - a computer language that is used to create and modify the structure of database objects, especially data schemas. 
	* Typically includes  CREATE, ALTER, and DROP applicable for tables. 
* **Data Manipulation Language** - computer programming language used for operating on data within a database. 

* A **schema** is a description of a particular collection of data using a given data model .
* **Database View** - a subset of a database based on a query that runs on one or more tables .

* A **relational database schema** $S$ is defined as a set of relation schemas $R$ and a set of integrity constraints $C$ where 
  $$
  S=R\cup C
  $$
* A **relational database instance** is a set of relation instances which satisfy the relational database schema. 
	* We may think of this as a snapshot of the state of a particular database at any given time.
# Relations
* A **relation** is a set of tuples $(d_1,\dots d_n)$. Where $d_j\in D_j$ and $D_j$ is the data domain. 

* Informally, we may think of relations as some logical structure with columns and rows such that:
	* The columns represent attributes 
	* The allowed values for each attribute represent the data domain
	* The rows represent a tuple

* A **Relation Schema** is a description of a  relation. More formally it is notated as 
  $$
  R(A_1,A_2,\dots, A_n)
  $$
  where $R$ is the name of the relation, and $A_1,\dots , A_n$ are the set of attributes of the relations. 
## Basic Properties 
* Each relation name in a relational database must be distinct
* The attribute names must be distinct from any attribute names of the same relation.
* The order of the attributes specified in $R$ is not significant.
* Each tuple in a relation is distinct. No duplicate tuples exist.
* The order of tuples is insignificant.
* Each cell in the relation table must contain exactly one value (**Atomicity**).
* Each of $d_j$ refers to an attribute of the relation.

## Keys 
* A **key** is a minimal superkey 
* A **superkey** is a proper subset of attributes for which no tuples may have the same combination of values.

* A **candidate key**  is any key. It is any set of attributes chosen from the relation. 
* A **primary key** is a key chosen to act as the means to which to identify tuples in a relation. We prefer this to be as small as possible. 
* A **foreign key** of relation $R$ is a set of its attributes intending to be used (by each tuple in $R$) for identifying or referring to a tuple in some relation $S$.
  
  $R$ is the **referencing relation**. $S$ is the **referenced relation**.
	* The set of attributes of $R$ forming the foreign key should correspond to some super key of $S$ (typically its primary key )

## Multiplicity 
* The **Degree** refers to the number of attributes in a relation (i.e., number of columns)
* The **Cardinality** denotes how many tuples of the referenced relation $S$ can correspond to a tuple in the referencing relation $R$. 
* The **Participation** denotes whether or not some tuple of the referencing relation $R$ should correspond to a tuple in the referenced relation $S$. 
* The **Multiplicity** of entity relationships is a pair which specifies the participation and the cardinality given two relations $R$  and $S$ related by a foreign key
 
## Relational Algebra 
* The **relational algebra** is an approach that defines fundamental operations that manipulate and operate on tuples in a relation.  
* They are defined as follows. 
  
  Let $,S$ be relations 
  $A_1,\dots,A_n$ be a set of attributes in the relation 
  
	* **Select** - denoted $\sigma_\text{predicate}(R)$. We *choose a subset of tuples* in $R$ that satisfy the predicate. The predicate acts as a filter based on some requirements.
	* **Projection** - denoted $\Pi_{A_1,\dots,A_n}(R)$. We *generate relations that contain only the specified attributes* allowing for rearranging their orderings and manipulate their values.
	* **Union** - denoted $R\cup S$. It is the relation that *contains all the tuples that appear in at least one* of the relations.
	* **Intersection** - denoted $R\cap S$. It is the relation that *contains all the tuples that appear in both* of the relations.
	* **Differnce** - denoted $R-S$. It is the relation that contains all the tuples that appear in $R$ *but not in* $S$
	* **Product** - denoted $R\times S$. It is the relation that contains *all possible combinations of tuples* from the input relations.
	* **Join** - denoted $R\bowtie S$. It is the relation  that contains all tuples that are a *combination of two tuples* (one from each of R and S) with a common value for one or more attributes.

## Constraints 
* **Data Integrity** - maintenance and assurance of accuracy and consistency of data within the database.
* An **integrity constraint** specifies permissible values inside the database. It must hold for all valid relation instances and states. 
  
  *Motivation*: They serve to guard against accidental damage to the database such that authorized changes should not result in a loss of data consistency. 
	* **Inherent or Implicit Constraints** - Constraints inherent in the definitions and assumptions of a particular data model hold in every database having that data model as its underpinning.
	* **Schema-based or Explicit Constraints** - expressed by using the facilities provided by the model via its DML. 
		* **Domain Constraint** - the *value of each attribute must be an atomic value* from its domain. 
		* **Key Constraint** - *no two tuples may have the same combination of values* in their attributes.
			* A relation is a set of tuples, and each tuple's "identity" is given by the values of its attributes. Hence, it makes no sense for two tuples in a relation to be identical (because then the two tuples are actually one and the same tuple).
		* **Entity Integrity Constraint** - in a tuple, none of the values of the attributes forming the relation's *primary key may have the (non)-value null. *
		* **Referential Integrity Constraint** - for every tuple in relation $R$, the tuple $S$ to which it refers to must actually be in $S$. 
			* *When a foreign key exists, the value must match a candidate key value of some tuple in the referenced relation*. 
			* In some cases we may permit the foreign keys have NULL values . but it must does so in all its attributes. Such a value denotes that the tuple in $R$ does not refer to any tuple in $S$.
		* **Semantic Integrity Constraint**-  a business specific rule that limits the permissible values within a relation. It ensures that the *values must be in a specified domain*
	* **Application-based or Semantic Constraint** - Constraints that are beyond the expressive power of the model and must be specified and enforced by the application itself. These are specifically related to the business rules.

## Dependencies 
* Given a relation $R$ with attributes $X,Y\subseteq R$. $X$ is said to **functionally determine** $Y$ if and only if each $X$ value in $R$ is associated with precisely one value of $Y$. That is, the values of $Y$ can be determined simply by looking at the corresponding values of $X$.

* A **transitive dependency** exists when $A$ is dependent on $B$, and $B$ is dependent on $C$ implies that $A$ is dependent on $C$. 
# Normalization 
* **Normalization** is a database design technique that is designed to reduce data redundancy and improve data integrity by following a normal form. 
* **Denormalization** is the opposite process. This is relevant in query optimization to minimize the number of joins we need to perform 

## First Normal Form 
* **First Normal Form** is a property of a relation wherein 
	* No attribute domain has relations as elements (i.e., no table columns may have tables or repeating groups as values).
	* Each set of related data must be its own table identified with their own primary key

* *Enforcement*: Do not use multiple fields in a single table to store similar data. 
* *Enforcement*: Use foreign keys to declare relationships between relations. 

## Second Normal Form 
* **Second Normal Form** is a property of a relation wherein 
	* It is in first normal form 
	* It does not have any candidate key that is functionally dependent on any proper subset of any candidate key of the relation 
	* It does not depend on anything other than the primary key .

* *Enforcement*: Create separate tables for sets of values that apply to multiple records.
* *Enforcement*: Relate tables with a foreign key 

## Third Normal Form 
* **Third Normal Form** is a property of a relation wherein 
	* It is in second normal form 
	* All attributes in the relation solely depend on the primary key 
	* No attributes have transitive dependency with another key 

* *Enforcement*: We can enforce as follows 
	* Eliminate attributes in the relation that are not dependent on the key. 
	* If the contents of a group of attributes may apply to more than a single record in the table, then separate them into a new table.
	* *Compromise*: If it is not feasible to enforce this, consider enforcing it only on data that frequently changes.

