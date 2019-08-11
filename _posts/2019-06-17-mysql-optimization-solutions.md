---
layout: post_layout
title: MYSQL optimization solutions
date: 2019-06-17 18:41:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

### 1\.select the most suitable field attribute

MySQL can support large data volumes very well, but in general, the smaller the table in the database, the faster the queries executed on it. Therefore, when creating a table, in order to get better performance, we can set the width of the fields in the table as small as possible. For example, when defining the zip code field, if you set it to CHAR (255), it obviously adds unnecessary space to the database, even using VARCHAR is superfluous, because CHAR(6) can be very good. Finished the task. Similarly, if possible, we should use MEDIUMINT instead of BIGIN to define an integer field. Another way to improve efficiency is to try to set the field to NOT NULL whenever possible, so that the database does not have to compare NULL values ​​when executing queries in the future. For some text fields, such as "province" or "gender", we can define them as ENUM types. Because in MySQL, ENUM types are treated as numeric data, and numeric data is processed much faster than text types. In this way, we can improve the performance of the database.

### 2\. use the connection (JOIN) instead of sub-query (Sub-Queries)

MySQL supports SQL subqueries starting with 4.1. This technique can use a SELECT statement to create a single-column query result and then use that result as a filter in another query. For example, if we want to delete a customer who does not have any orders in the customer basic information table, we can use the sub-query to first take out all the customer IDs that have placed the order from the sales information table, and then pass the results to the main query, as shown below. :

~~~sql
SELECT  *  FROM  customerinfo

WHERE  customerid  NOT IN (SELECT customerid FROM salesinfo)
~~~

If you use join (JOIN).. to complete this query work, the speed will be much faster. Especially when the CustomerID is indexed in the salesinfo table, the performance will be better, the query is as follows:

~~~sql
SELECT  *  FROM  customerinfo

LEFT  JOIN  salesinfo ON customerinfo.customerid = salesinfo.customerid

WHERE salesinfo.customerid IS NULL
~~~

JOIN: The reason why it is more efficient is that MySQL does not need to create temporary tables in memory to complete this logical two-step query.

### 3\. Use union (UNION) instead of manually created temporary table

MySQL supports union queries starting with version 4.0, which can be used to merge two or more select queries that need to use temporary tables. At the end of the client's query session, the temporary table will be automatically deleted, thus ensuring that the database is neat and efficient. When using union to create a query, we only need to use UNION as a keyword to connect multiple select statements. It should be noted that the number of fields in all select statements should be the same. The following example demonstrates a query using UNION.

~~~sql
SELECT  name,phone FROM client UNION

SELECT name,birthdate FROM  author  UNION

SELECT name,supplier FROM product
~~~

### 4\. Transaction

Although we can use Sub-Queries, JOIN, and UNION to create a variety of queries, not all database operations can be completed with just one or a few SQL statements. of. More often than not, a series of statements are needed to do something. But in this case, when a statement in this statement block runs incorrectly, the operation of the entire statement block becomes undefined. Imagine that you want to insert a piece of data into two associated tables at the same time. It may happen that after a successful update in the first table, the database suddenly has an unexpected condition, causing the operation in the second table to be incomplete. In this way, the data will be incomplete and even destroy the data in the database. To avoid this, you should use a transaction. Its purpose is: either each statement in the statement block succeeds or fails. In other words, it is possible to maintain the consistency and integrity of the data in the database. Things start with the BEGIN keyword and the COMMIT keyword ends. If a SQL operation fails between the two, then the ROLLBACK command will restore the database to the state it was in before BEGIN started.

~~~sql
BEGIN;
  INSERT   INTO   salesinfo   SET   customerid=14;
  UPDATE   inventory   SET   quantity =11   WHERE   item='book';
COMMIT;
~~~

Another important role of a transaction is that when multiple users use the same data source at the same time, it can use the method of locking the database to provide a secure access mode for the user, so as to ensure that the user's operation is not interfered by other users.

### 5\. Lock

&nbsp;

Although transactions are a very good way to maintain database integrity, but because of its exclusivity, sometimes affect the performance of the database, especially in large applications. Since the database will be locked during the execution of the transaction, other user requests can only wait temporarily until the end of the transaction. If a database system has only a few users to use, the impact of the transaction will not become a big problem; but if there are thousands of users accessing a database system at the same time, such as accessing an e-commerce website, it will be generated. More serious response delays. In fact, in some cases we can get better performance by locking the table. The following example uses the method of locking the table to complete the function of the transaction in the previous example.

~~~sql
LOCK TABLE inventory WRITE SELECT quantity  FROM   inventory   WHERE Item='book';
...
UPDATE   inventory   SET   Quantity=11   WHERE  Item='book';UNLOCKTABLES
~~~

&nbsp;

Here, we use a select statement to take the initial data, through some calculations, update the new value to the table with the update statement. The LOCKTABLE statement containing the WRITE keyword ensures that there will be no other accesses to insert, update, or delete the inventory until the UNLOCKTABLES command is executed.