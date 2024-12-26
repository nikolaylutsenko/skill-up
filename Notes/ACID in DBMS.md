---
tags:
  - database
  - acid
---
![[Pasted image 20241226141124.png]]

## Transaction
a __transaction__ is a single logical unit of work that accesses and possibly modifies the contents of a database. ACID are properties that __maintain consistency__ in a database before and after the transaction.

## Atomicity
either the entire transaction takes place at once or doesn’t happen at all, there is no midway

## Consistency
integrity constraints must be maintained so that the database is consistent before and after the transaction
## Isolation
ensures that multiple transactions can occur concurrently without leading to the inconsistency of the database state.

## Durability
ensures that once the transaction has completed execution, the updates and modifications to the database are stored in and written to disk and they persist even if a system failure occurs.

ACID properties are the four key characteristics that define the reliability and consistency of a transaction in a Database Management System (DBMS). The acronym ACID stands for Atomicity, Consistency, Isolation, and Durability. Here is a brief description of each of these properties:

1. ****Atomicity:**** Atomicity ensures that a transaction is treated as a single, indivisible unit of work. Either all the operations within the transaction are completed successfully, or none of them are. If any part of the transaction fails, the entire transaction is rolled back to its original state, ensuring data consistency and integrity.
2. ****Consistency:**** Consistency ensures that a transaction takes the database from one consistent state to another consistent state. The database is in a consistent state both before and after the transaction is executed. Constraints, such as unique keys and foreign keys, must be maintained to ensure data consistency.
3. ****Isolation:**** Isolation ensures that multiple transactions can execute concurrently without interfering with each other. Each transaction must be isolated from other transactions until it is completed. This isolation prevents dirty reads, non-repeatable reads, and phantom reads.
4. ****Durability:**** Durability ensures that once a transaction is committed, its changes are permanent and will survive any subsequent system failures. The transaction’s changes are saved to the database permanently, and even if the system crashes, the changes remain intact and can be recovered.