# Fragmentation  
* **Fragmentation** - pertains to partitioning a relation into several fragments. These fragments may then be stored in different sites (i.e., a distributed system)

* **Horizontal Fragmentation** - is a variation of fragmentation wherein each tuple in a relation is assigned to one of more fragments. It allows for: 
	* Parallelization on fragments of a relation 
	* The relation can be split so that tuples are closer to where they are frequently accessed.

* **Vertical Fragmentation** - a subtype of fragmentation wherein the schema for a relation is split into smaller schemas such that
	* All schemas contain a common candidate key 
	* Optionally, a **tuple id** attribute is added to each schema to serve as a candidate key.
	* This has the following consequences
		* Allows a tuple to be split so that each part of the tuple is closer to where it is frequently accessed. Allows a tuple to be split so that each part of the tuple is closer to where it is frequently accessed.
		* The tuple-id allows joins across vertical fragments.
		* Parallelization for relations

# Replication 
* **Replication** - a technique in managing distributed databases using specialized software that looks for changes in the database. 
	* Once changes have been identified, the replication process makes all the databases across all sites look the same.
	* This may be done on the relation level or on the database level. In either case, we say this group of data is **replicated**.

* **Full Replication** - a subtype of replication wherein an entire relation is stored across all sites in a distributed database. 
	* A **fully-redundant database storage** is one where the entire database is replicated across all sites in a distributed database 

# Links 
* [[Database Basics]]
* [[Graph Theory]] - because the system is distributed, we can interpret the nodes as vertices and connections as edges. 