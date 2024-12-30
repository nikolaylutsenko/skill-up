---
tags:
  - database
  - acid
  - transaction
---
# What is a Transaction Isolation

it defines how and when the changes made by one transaction are visible to others to assure data consistency and integrity

Transaction isolation levels are a trade-off between consistency and performance of DBMS. They help in controlling parallel access to data with the view of reducing various anomalies, including dirty reads, nonrepeatable reads, and phantom reads, by defining the level of isolation of two transactions from each other. Selection of the right isolation level is application requirement-dependent, and usually, the level of isolation is a trade-off between data integrity and concurrency, and therefore, system efficiency.

The SQL standard defines four isolation levels  
1. ****Read Uncommitted –**** Read Uncommitted is the lowest isolation level. In this level, one transaction may read not yet committed changes made by other transactions, thereby allowing dirty reads. At this level, transactions are not isolated from each other.
2. ****Read Committed –**** This isolation level guarantees that any data read is committed at the moment it is read. Thus it does not allow dirty read. The transaction holds a read or write lock on the current row, and thus prevents other transactions from reading, updating, or deleting it.
3. ****Repeatable Read –**** This is the most restrictive isolation level. The transaction holds read locks on all rows it references and writes locks on referenced rows for update and delete actions. Since other transactions cannot read, update or delete these rows, consequently it avoids non-repeatable read.
4. ****Serializable –**** This is the highest isolation level. A __serializable__ execution is guaranteed to be serializable. Serializable execution is defined to be an execution of operations in which concurrently executing transactions appears to be serially executing.