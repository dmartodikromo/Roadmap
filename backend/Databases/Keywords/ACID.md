source: https://en.wikipedia.org/wiki/ACID

 **ACID** ([atomicity](https://en.wikipedia.org/wiki/Atomicity_(database_systems) "Atomicity (database systems)"), [consistency](https://en.wikipedia.org/wiki/Consistency_(database_systems) "Consistency (database systems)"), [isolation](https://en.wikipedia.org/wiki/Isolation_(database_systems) "Isolation (database systems)"), [durability](https://en.wikipedia.org/wiki/Durability_(database_systems) "Durability (database systems)")) is a set of properties of [database transactions](https://en.wikipedia.org/wiki/Database_transaction "Database transaction") intended to guarantee data validity despite errors, power failures, and other mishaps. In the context of [databases](https://en.wikipedia.org/wiki/Database "Database"), a sequence of database operations that satisfies the ACID properties (which can be perceived as a single logical operation on the data) is called a _transaction_.

### Atomicity

Main article: [Atomicity (database systems)](https://en.wikipedia.org/wiki/Atomicity_(database_systems) "Atomicity (database systems)")

[Transactions](https://en.wikipedia.org/wiki/Database_transaction "Database transaction") are often composed of multiple [statements](https://en.wikipedia.org/wiki/SQL_syntax "SQL syntax"). [Atomicity](https://en.wikipedia.org/wiki/Atomicity_(database_systems) "Atomicity (database systems)") guarantees that each transaction is treated as a single "unit", which either succeeds completely or fails completely: if any of the statements constituting a transaction fails to complete, the entire transaction fails and the database is left unchanged. An atomic system must guarantee atomicity in each and every situation, including power failures, errors, and crashes. A guarantee of atomicity prevents updates to the database from occurring only partially, which can cause greater problems than rejecting the whole series outright. As a consequence, the transaction cannot be observed to be in progress by another database client. At one moment in time, it has not yet happened, and at the next, it has already occurred in whole (or nothing happened if the transaction was canceled in progress).

### Consistency

Main article: [Consistency (database systems)](https://en.wikipedia.org/wiki/Consistency_(database_systems) "Consistency (database systems)")

[Consistency](https://en.wikipedia.org/wiki/Consistency_(database_systems) "Consistency (database systems)") ensures that a transaction can only bring the database from one consistent state to another, preserving database [invariants](https://en.wikipedia.org/wiki/Invariant_(computer_science) "Invariant (computer science)"): any data written to the database must be valid according to all defined rules, including [constraints](https://en.wikipedia.org/wiki/Integrity_constraints "Integrity constraints"), [cascades](https://en.wikipedia.org/wiki/Cascading_rollback "Cascading rollback"), [triggers](https://en.wikipedia.org/wiki/Database_trigger "Database trigger"), and any combination thereof. This prevents database corruption by an illegal transaction. [Referential integrity](https://en.wikipedia.org/wiki/Referential_integrity "Referential integrity") guarantees the [primary key](https://en.wikipedia.org/wiki/Unique_key "Unique key")–[foreign key](https://en.wikipedia.org/wiki/Foreign_key "Foreign key") relationship.

### Isolation

Main article: [Isolation (database systems)](https://en.wikipedia.org/wiki/Isolation_(database_systems) "Isolation (database systems)")

Transactions are often executed [concurrently](https://en.wikipedia.org/wiki/Concurrent_computing "Concurrent computing") (e.g., multiple transactions reading and writing to a table at the same time). [Isolation](https://en.wikipedia.org/wiki/Isolation_(database_systems) "Isolation (database systems)") ensures that concurrent execution of transactions leaves the database in the same state that would have been obtained if the transactions were executed sequentially. Isolation is the main goal of [concurrency control](https://en.wikipedia.org/wiki/Concurrency_control "Concurrency control"); depending on the isolation level used, the effects of an incomplete transaction might not be visible to other transactions.

### Durability[

Main article: [Durability (database systems)](https://en.wikipedia.org/wiki/Durability_(database_systems) "Durability (database systems)")

[Durability](https://en.wikipedia.org/wiki/Durability_(computer_science) "Durability (computer science)") guarantees that once a transaction has been committed, it will remain committed even in the case of a system failure (e.g., power outage or [crash](https://en.wikipedia.org/wiki/Crash_(computing) "Crash (computing)")). This usually means that completed transactions (or their effects) are recorded in [non-volatile memory](https://en.wikipedia.org/wiki/Non-volatile_memory "Non-volatile memory").