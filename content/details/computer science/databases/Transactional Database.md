* A **Transaction** is a logical unit of work that may involve several accesses and or updates to the database. 
* *Even though transactions run concurrently, the end result must be as though they were carried out sequentially*. 
# ACID and Database Integrity 
* The **ACID properties** are properties which hold for a transaction in a database. These properties ensure the validity of data regardless of any system failures. 
	* **Atomicity** - a guarantee that *each transaction is treated as a single unit*, which either succeeds completely or fails completely. 
		* If any statements in the transaction fail to complete, the entire transaction fails and the database is left unchanged. This is a guarantee even in crashes or errors.
		* It guarantees that no update operation  will happen only partially. As a result, a transaction in progress cannot be observed by another client. 
	* **Consistency** - ensures that transactions can only bring the database from one consistent, valid state to another. *All invariants are preserved*. 
		* It prevents corruption by illegal transactions 
		* It also enforces referential integrity. 
	* **Isolation** - guarantees that any concurrent execution of transactions leaves the database in *the same state that would have been done if they were executed in series.* 
		* Depending on the isolation level, the effects of an incomplete transaction may not be visible to others. 
		* An **isolation level** is a means to relax this constraint. *It offers a tradeoff between concurrency (speed) and data integrity*. Strong isolation levels also implement the weaker isolation levels. 
			* **Serializable** - It requires read and write locks to be released at the end of a transaction. 
				* It prevents any issues due to concurrency. 
				* In a non-lock based system it requires detection of write collisions and also managing range locks. 
				* This prevents phantom reads, non-repeatable reads, and dirty reads.
			* **Repeatable Reads**  - manages any read and write locks but not range locks.
				* It doesn't prevent phantom reads. 
				* It is possible to have **write skew** - wherein two writes are allowed in the same column in a table by two different writers that have previously read the columns. The columns may have a mix of the two transactions 
			* **Read Committed** - we keep any write locks but release read locks 
				* It guarantees that any data read by a transaction is committed the moment it is read. 
				* It prevents the reader from reading any uncommitted data, however it makes no promise of repeatable reads. 
			* **Read Uncommitted** -  allow transactions to perform even dirty reads. 
	* **Durability** - guarantees that once a transaction has been committed to the database, it will remain committed even in the case of system failure. *Completed transactions and their effects should be recorded in non-volatile storage*. 

* *The database can face various issues*
	* A **blind write** occurs when a transaction *writes a value without reading it.* 
	* A **lost update** occurs when an apparently successfully completed update operation by one transaction is *overridden by another transaction running concurrently.* 
	* A **phantom read** occurs when a transaction attempts to read a row using a certain criteria. However, a *row that passes this criteria is initially missed*. This can happen when a transaction retrieves rows twice and new rows were modified by another concurrently running transaction.
	* A **non-repeatable read** occurs when a *transaction reads the same table twice but it gets different data each time*. It happens when another transaction concurrently updates, inserts or deletes from the table in between the first 
	* A **dirty read** is a read which occurs when a transaction retrieves a tuple that was updated by a concurrent transaction that was *not yet committed.* 

# DBMS structures 
* The DMBS provides **concurrency control** is a procedure for managing concurrent transactions while maintaining the ACID properties. 

## Commits and Atomicity
* A **commit** is the making of a set of tentative changes (i.e., via a transaction) permanent. *By durability, transactions should end with a commit if successful*
* A **rollback** is an operation which returns the database to some previous state. This ensures data integrity as well as consistency. No transaction interrupted by a crash will cause the database to be in an incorrect state. 

* **Logging** is an approach that ensures all transactions are atomic. 
	* This is done by logging all actions so that it can undo the actions of aborted transactions. 
	* This approach is most commonly used because it is efficient, and auditable. 
* An **atomic commit protocol** is a protocol that ensures atomicity when committing a transaction 
	* We require **stable storage** for atomicity of any write operation. Stable storage should be robust against hardware and power failure.

### Write-Ahead Logging 
* **Write-Ahead Logging** is a technique for providing atomicity and durability 
* Within stable storage, prior to performing a write, we record: 
	* The transaction that performed the write 
	* The state of the database before the write 
	* The state of the database after the write 
	* The item which will be modified with the write 
* *Write-Ahead logging leads to the following*
	* We can reconstruct lost changes via the log.
	* We can persist all operations until the cached copies of pagesare synchronized.
	* We can allow the page cache to buffer updates while ensuring durability.

## Concurrency Control 
* **Serializability** is a criterion wherein the effect of running transaction concurrently is equivalent to running the same transactions in some order.

* A **database lock** is a concurrency control mechanism that prevents simultaneous access to data stored in a database. *Locks ensure consistency and isolation*
	* An **exclusive lock** is exclusively held by a single entity. Effectively, we block any other entity that requires the lock from processing. 
	* A **shared lock** can be held by multiple entities. This allows multiple entities to perform reads with the guarantee that the data will not be changed until the lock is released.
* Using a database lock means that 
	* We must make sure the lock is held for as short period of time as possible for performance as other transactions will stall 
	* We must prevent [[Deadlock]]
	* In the event of system failure, the lock must be released to allow other entities to access the data.

* A **lock manager** grants or blocks incoming requests based on what locks are being held by other transactions 

* A **lock hierarchy** is a hierarchy of locks which allows a transaction to take more coarse grained locks in the system.  
	* When a transaction acquires a lock for an object in the hierarchy, it implicitly acquires the locks for all children objects. There are 5 levels 
		* Database 
		* Table 
		* [[Database Management System|Page]]
		* Tuple 
		* Attribute 
	* *Rationale*: If a transaction wants to update one billion tuples, it has to ask the lock manager for a billion locks. This will be slow as we have to manage the acquisition and releasing of many locks.
	* An **intention lock** is a lock that is placed on a higher granularity when a lower granularity object needs to be locked.  *This affords a check that no other user holds a lock on the higher granularity object.*
		* **Intention-Shared (IS)** locks explicitly lock at a lower granularity with shared locks 
		* **Intention-Exclusive (IX)** locks explicitly lock at a lower granularity with exclusive or shared locks 
		* **Shared + Intention Shared** indicate explicit locking at the current level with shared locks and the at the lower level, locking is done with exclusive locks 

* **Timestamp Ordering** is a technique where each object is tagged with the timestamp of the last transaction that successfully performed an operation on it. 
	* For each operation, we check the object. If a transaction is accessing an object from the future, it aborts and restarts. 
	* When performing accesses, we make a local copy similar to shadow paging. 
	* It prevents deadlocks entirely 
	* It may cause starvation for long transactions since short transactions could cause conflicts. 
	* There is high overhead from copying data to transaction's workspace and from updating timestamps.

## Scheduling
* A **schedule** $S$ of transaction $T_1, \dots, T_n$ is an ordering of operations of the transactions subject to the constraint that for each transaction $T_i$ that participates in $S$, the operations of $T_i$ in $S$ must appear in the same order in which they occur in $T_i$.  Other operations from other transactions can be interleaved with the operations of $T_i$ in $S$.

* Two operations are **conflicting** if:
	* They are by different transactions 
	* They are on the same object 
	* One of them is a write operation 
* Read-Write conflicts mean non-repeatable reads 
* Write-read conflicts mean dirty reads
* Write-Write conflicts mean lost updates. 

* A schedule is **serial** is for every transaction $T$ participating in the schedule, all the operations of $T$ are executed consecutively in the schedule. That is, we do not allow any any interleaving between transactions; *all transactions run serially*
	* *Every serial schedule is correct*, that is it ensures valid state of the data. This follows by consistency.
	* Serial schedules come at the trade-off of slower performance since we can stall because we do not perform tasks concurrently.

* Two schedules are **result-equivalent** if executing these schedules have the same effect on the database. 
* Two schedules are **conflict-equivalent** if and only if they involve the same operations of the same transaction and conflict operations are ordered in the same way in both schedules. 
* A schedule is **conflict-serializable** if it is conflict equivalent to some serial schedule. 
* *The dependency graph of the operations in a conflict serializable schedule is acyclic since we can topologically order the nodes*. 

* A schedule is **view serializable** if it allows for all schedules that are conflict schedules and we are able to perform blind writes. 
* A schedule is **strict** if any values written by a transaction is never read or overwritten by another transaction until the first transaction commits.

* **Optimistic Locking** is an approach to locking where the DBMS assumes that *transactions will rarely conflict*, so it chooses to deal with these conflicts after commits. 
	* It avoids the overhead that comes with locking.  This is relevant when modifications have lower overhead than locking. 
	* There is a need to resolve conflicts
* **Pessimistic Locking** - is an approach to database locking where the DBMS assumes that *transactions will conflict*. the system prevents this by placing a locks on records that are being modified. Other users must wait until the lock is released. 
	* It avoids the issue of conflict resolution by avoiding conflicts. It makes the schedule serializable 
	* It is slow especially when multiple transactions are performing modifications. 

### Two Phase Locking 
* **Two Phase Locking** is a pessimistic concurrency control protocol that uses locks to determine whether a transaction is allowed to access an object in the database 
* In the *growing phase*:  Each transaction requests the locks that it needs from the lock manager. The lock manager grants or denies these requests.
* In the *shrinking phase*: Transactions enter this phase immediately after it releases its first lock. In this phase, transactions release blocks, and they cannot acquire new ones.

## Deadlocks 
* **Deadlock Detection** is an approach of detecting deadlocks before they happen. 
	* The DBMS maintains a wait-for [[Fundamental Constructs in Graph Theory|graph]] where transactions are nodes and there is a directed edge from $T_i$ to $T_j$ if $T_i$ is waiting for $T_j$ to release a lock 
	* The system periodically checks for [[Graph Connectivity|cycles]] in the graph and then makes a decision how to break it 
	* *Latches are not needed since  if the system misses a deadlock on the first pass, it will find it in subsequent passes*. There is, however, a tradeoff to the frequency of deadlock checks and the wait time until a deadlock is broken.
	* On finding a deadlock, the DBMS decides how to break the cycle by selecting a victim transaction that will restart or abort. The victim can be chosen
		* By age (newest or oldest time stamp)
		* By progress (least / most queries executed)
		* Number of items already locked
		* Number of transactions needed to rollback with it 
		* Number of times the transaction has been restarted in the past.
	* The DBMS can then either rollback the whole transaction or just enough queries to break deadlock.

* **Deadlock Prevention** prevents transactions from acquiring a lock that could cause a deadlock. 
	* When a transaction is about to acquire a lock held by another transaction, the DBMS kills one of the transactions. Priorities are determined based on their timestamps 
		* **Wait-Die** - if the requesting transaction has a higher priority than the holding transaction, it waits. Otherwise, it aborts. *Older transactions wait for younger transactions to finish*. 
		* **Wound-Wait** - If the requesting transaction has a higher priority than the holding transaction, the holding transaction aborts and releases the lock. Otherwise, the requesting transaction waits. *Younger transactions give way to older transactions*

	* This ensures that no deadlocks occur because only one type of direction is allowed when waiting for a lock.

* **Starvation** occurs when a transaction or process is indefinitely delayed because it requires a resource to execute, but the resource is never provided, despite the fact that it is available. 
## Recovery 
* **Database Recovery** pertains to a set of techniques that ensure consistency, atomicity, and durability despite system failures. 
* Recovery algorithms have two parts 
	* Actions during normal transaction processing to ensure that the DBMS can recover from a failure 
	* Actions after a failure to recover the database to a state that ensures atomicity, consistency, and durability.
* Recovery is somewhat contingent on the method for [[#Commits]]. 

* **Log Based Recovery** is a recovery system wherein 
	* We maintain a log of each transaction in stable storage so that if any failure occurs, it can be recovered from there. 
	* Use a write-ahead log 
	* Logs also record whether or not transactions were aborted. 
* *There are two approaches to log-based recovery*
	* **Immediate Database Modification** - an approach for modifying the database wherein the transaction modifies the database while it is active. 
		* The database is updated immediately after each operation transaction. It cannot be modified without committing. 
		* Logs must contain both the old and new values. Before each write, the record of the old and the new values are written on the database.  
		* To recover the data, we consider two cases 
			* **Redo**: If the log contains the record $\braket\text{T, start}$ and $\braket\text{T, commit}$ then set the value of all data items updated by $T$ to the new values. Go *forward* from the first log record of $T$.
			* **Undo**: If the log contains the record $\braket\text{T, start}$ but not $\braket\text{T, commit}$, then restore the values of all data items updated by $T$ to their old values  Go *backward* from the first log record of $T$.
	
	* **Deferred Database Modification** -  an approach for modifying the database wherein transaction does not modify the database until it has committed. 
		* Logs are created and stored in the stable storage and the database is updated when the transaction is committed. 
		* We do a redo for transaction $T$ if and only if the log contains both $\braket\text{T, start}$ and $\braket\text{T, commit}$.

# Links 
* [[Database Basics]]
* [[Multiprogramming]]