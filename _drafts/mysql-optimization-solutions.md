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

&nbsp;

MySQL supports SQL subqueries starting with 4.1. This technique can use a SELECT statement to create a single-column query result and then use that result as a filter in another query. For example, if we want to delete a customer who does not have any orders in the customer basic information table, we can use the sub-query to first take out all the customer IDs that have placed the order from the sales information table, and then pass the results to the main query, as shown below. :

```sql
SELECT  *  FROM  customerinfo
 
WHERE  customerid  NOT IN (SELECT customerid FROM salesinfo)
```
```sql
SELECT  *  FROM  customerinfo
 
LEFT  JOIN  salesinfo ON customerinfo.customerid = salesinfo.customerid
 
WHERE salesinfo.customerid IS NULL
```
```sql
SELECT  name,phone FROM client UNION
 
SELECT name,birthdate FROM  author  UNION
 
SELECT name,supplier FROM product
```
