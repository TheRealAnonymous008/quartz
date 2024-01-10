* A **distributed database** is a database where data is stored across different physical locations. In the system, there are loosely coupled sites that share no physical components. 
	* We may store the data by using fragmentation and replication. Each fragment is stored across sites and the system maintains replicas of each fragment. 
	* a **homogeneous distributed database** is where database is stored identically. 
		* All systems use identical DBMSs and [[Operating System|OS]]'s
		* Data can be accessed and modified simultaneously on several databases.
		* From the user's perspective, the database is no different to a single non-distributed database. 
	* A **heterogeneous distributed database** is where different sites use different schemas or software. 
		* Each site uses different DBMS software. 
		* Coordination is done through generic connectivity, which is usually limited. 

* A **Distributed Database Management System** is a centralized software system that manages a distributed database in a manner as if it were stored in a single location 
	* The DDBMS should facilitate distributed transactions through the following: 
		* Each site has a local **transaction manager**  which controls and coordinates the execution of transactions.  
		* Each site has a **transaction coordinator** which is responsible for 
			* Starting the execution of transactions that originate at its site 
			* Distributing transactions at appropriate sites 
			* Coordinating the termination of each transaction 

* **Data Transparency** refers to the degree in which a system user remains unaware of the details of how and where data are stored in the distributed system. 

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

# Transactions 
## Replication 
* A technique using specialized software that looks for changes in the database. 
* Once changes have been identified, the replication process makes all the databases across all sites look the same.
* *Advantages*
	* More robust system 
	* Better data availability 
	* Easier parallelization on by distributing transactions across several nodes 
	* Reduced data transfer, especially when data is stored close to where it is used.
* *Disadvantages*
	* Increased cost for CRUD operations since we must update all sites 
	* Increased complexity in terms of concurrency control which can affect data consistency.

## Two Phase Commit 
* **Two Phase Commit** is an atomic commit protocol that coordinates all the processes that participate in a distributed transaction.
* *Assume*: 
	* One node is a **designated coordinator**. The remaining nodes in the distributed system are **participants**
	* There is stable storage at each node with a write-ahead log 
	* No node crashes forever; data is never lost or corrupted in a crash.
	* Nodes can communicate to each other.

* The protocol is initiated by the coordinator after the last step of the transaction is reached. 
* Participants then respond with an *agreement* or an *abort* message depending on if the transaction has been processed successfully.

### Commit Request
* Coordinator sends a query to commit message to all participants, and waits until it has received a reply from all participants.
* Participants execute the transaction up to the point where it will be committed. They then write an entry to their undo and redo logs.
* Participants reply with a vote (either *Yes to Commit* or *No to Commit*) depending on if the participant performed the actions successfully or if a failure happened.

### Commit Phase
* *On a success*
	* The coordinator sends the commit message to all participants.
	* Each participant completes the operation, and releases any resources held during the transaction.
	* Send an acknowledgement to the coordinator.
	* The coordinator completes the transaction when all acknowledgements are received
* *On a failure of any kind from the participants.*
	* Send a rollback message to all participants.
	* All participants undo the transaction and release resources held during the transaction.
	* All participants send an acknowledgement.
	* The coordinator undoes the transaction when all acknowledgements are received.

* *On a failure of any kind from the coordinator.*
	* Look at the transaction logs to determine the fate of the transactions.
	* Treat the transaction as a success if all participants sent a yes-to-commit, then handle the success.
	* Treat the transaction as a failure if at least one participants sent a no-to-commit, then handle the failure as normal.

* Note that this introduces a blocking problem-all participants must wait for the coordinator to finish. 

# Links 
* [[Database Basics]]
* [[Graph Theory]] - because the system is distributed, we can interpret the nodes as vertices and connections as edges. 
* [[Transactional Database]]
* [[Multiprogramming]] - typically distributivity implies concurrency control. 