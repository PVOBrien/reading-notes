## [Database Normalization](https://www.essentialsql.com/get-ready-to-learn-sql-database-normalization-explained-in-simple-english/)

Ah, making data look right. While sql syntax isn't yet my cup of tea, making content easier and cleaner sure is. SQL is nice in that it is very straight forward, but with that simplicity, levels of nuance and complexity are also stripped away. So database normalization is a thing to tidy up data so that a DBA (DataBase Administrator) can keep a sane head dealing with large tables of data.

There are three vectors or causes of data becoming broken or hard to reach, and they are:

1. Insert Anomaly - when you need addtl details from that row (in another of it's columns) before you can update any other row. 
2. Update Anomaly - when a single column change should be populated in every row
3. Deletion Anomaly - when a single row deletion would remove other unique and relevant information (in this example, deleting an employee would also remove all references to their clients).

### Normalizing Data

Each of the _nth_ Normal Forms normalize (aka "refactor", yeah?) tables to me more modular and representative of the data.

There's too much info to dig into right now, but each of the following articles serve as a basis for  fundamentally decent approach to ensuring your tables are properly referenced, contain only the right info for each field, and correctly relational to the next (and with it's own data), so that no "collateral information" is lost when removing one of the individuals entries.

[First Normal Form - 1NF](https://www.essentialsql.com/get-ready-to-learn-sql-8-database-first-normal-form-explained-in-simple-english)

[Second Normal Form - 2NF](https://www.essentialsql.com/get-ready-to-learn-sql-10-database-second-normal-form-explained-in-simple-english)

[Third Normal Form - 2NF](https://www.essentialsql.com/get-ready-to-learn-sql-11-database-third-normal-form-explained-in-simple-english)
