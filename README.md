# Database Concepts

This document explains various database concepts, including SQL Join types, ACID properties, and database normalization forms. Each concept is detailed with examples to support learning and understanding of relational databases.



## SQL Join Types

A **JOIN** clause is used to combine rows from two or more tables based on a related column between them.

### INNER JOIN
The SQL INNER JOIN statement joins two tables based on a common column and selects rows that have matching values in these columns.

#### Example
```sql
SELECT customers.customer_id,customers.firstname,customers.lastname,orders.order_name,orders.order_id FROM customers INNER JOIN orders ON customers.order_id= orders.order_id;
```

![innerjoin results](./images/Inner%20join.jpg)

### LEFT JOIN

The SQL LEFT JOIN combines two tables based on a common column. It then selects records having matching values in these columns and the remaining rows from the left table.

### Example
```sql

SELECT customers.customer_id,customers.firstname,customers.lastname,orders.order_name,orders.order_id FROM customers LEFT JOIN orders ON customers.order_id= orders.order_id;
```

![leftjoin results](./images/Left%20join.jpg)


### RIGHT JOIN
The SQL RIGHT JOIN statement joins two tables based on a common column. It selects records that have matching values in these columns and the remaining rows from the right table.

### Example

```sql
SELECT customers.customer_id,customers.firstname,customers.lastname,orders.order_name,orders.order_id FROM customers RIGHT JOIN orders ON customers.order_id = orders.order_id;
```
![Rightjoin results](./images/Right%20Join.jpg)

### FULL JOIN

The SQL FULL OUTER JOIN statement joins two tables based on a common column. It selects records that have matching values in these columns and the remaining rows from both of the tables.
### Example

```sql
SELECT customers.customer_id,customers.firstname,customers.lastname,orders.order_name,orders.order_id FROM customers FULL JOIN orders ON customers.order_id= orders.order_id;
```

![Fulljoin results](./images/Full%20join.jpg)


## ACID Properties

**ACID** stands for **Atomicity, Consistency, Isolation, and Durability**. These properties ensure reliable database transactions.

- **A = Atomicity**: Database transactions must be all or nothing. If any part of the transaction fails, the entire transaction is rolled back.
  - **Example**: When transferring money between two accounts, either both the debit and credit occur, or neither occurs, ensuring no partial transaction.

- **C = Consistency**: Only valid data is written to the database, ensuring accuracy and correctness.
  - **Example**: A transaction that exceeds the permissible overdraft limit of a bank account will be blocked to maintain data consistency.

- **I = Isolation**: Transactions are processed independently of one another, preventing one transaction from interfering with another until it is committed.
  - **Example**: If one transaction is updating a row, other transactions will not see the update until the first transaction is committed.

- **D = Durability**: Once a transaction is committed, it will remain in the system even in case of a failure.
  - **Example**: If a transaction updates customer data, the changes will persist even after a system crash.

## Introduction to Normalization

Normalization is a systematic approach to organizing data in a database to minimize redundancy and improve data integrity. It involves structuring a relational database in such a way that relationships among data are clearly defined, and anomalies in data insertion, update, and deletion are eliminated.