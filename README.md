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


### Normalization Types

Normalization is a process to organize data in a database to minimize data redundancy and dependency. Normalization involves dividing a database into two or more tables and linking them using relationships.

The three main normalization rules are 1NF, 2NF, and 3NF. Higher Normal Forms (4NF, 5NF, etc.) are also possible but are generally not used in practice.

### 1NF (First Normal Form)

1NF states that all the records in a table should contain different values. There should not be any repeating groups or arrays in a table.

### Example

Suppose we have a table with customer information.

| customer_id | customer_name | phone |
| --- | --- | --- |
| 1 | John Smith | 123-456-7890, 098-765-4321 |
| 2 | Jane Doe | 555-123-4567 |


The table above is not in 1NF because the phone column contains multiple values. To put it in 1NF, we need to create a new table that contains the customer_id and one phone number per row.

| customer_id | phone |
| --- | --- |
| 1 | 123-456-7890 |
| 1 | 098-765-4321 |
| 2 | 555-123-4567 |

### 2NF (Second Normal Form)

2NF states that all the non-prime attributes in a table should depend on the entire primary key. In other words, a non-prime attribute should not depend on only one part of the primary key.

### Example

Suppose we have a table with customer information.

| customer_id | customer_name | address | city | state |
| --- | --- | --- | --- | --- |
| 1 | John Smith | 123 Main St | New York | NY |
| 1 | John Smith | 456 Elm St | New York | NY |
| 2 | Jane Doe | 789 Oak St | Los Angeles | CA |

The table above is not in 2NF because the address, city, and state attributes depend on only the customer_name part of the primary key. To put it in 2NF, we need to create a new table that contains the customer_id and one address per row.

| customer_id | address | city | state |
| --- | --- | --- | --- |
| 1 | 123 Main St | New York | NY |
| 1 | 456 Elm St | New York | NY |
| 2 | 789 Oak St | Los Angeles | CA |

### 3NF (Third Normal Form)

3NF states that if a table is in 2NF, and a non-prime attribute depends on another non-prime attribute, then it should be moved to a separate table.

### Example

Suppose we have a table with customer information.

| customer_id | customer_name | address | city | state | zip_code |
| --- | --- | --- | --- | --- | --- |
| 1 | John Smith | 123 Main St | New York | NY | 10001 |
| 1 | John Smith | 456 Elm St | New York | NY | 10001 |
| 2 | Jane Doe | 789 Oak St | Los Angeles | CA | 90001 |

The table above is not in 3NF because the zip_code attribute depends on the city attribute. To put it in 3NF, we need to create a new table that contains the customer_id and one zip_code per row.

| customer_id | zip_code |
| --- | --- |
| 1 | 10001 |
| 1 | 10001 |
| 2 | 90001 |


