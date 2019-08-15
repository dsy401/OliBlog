---
layout: post_layout
title: Database index
date: 2019-06-27 00:00:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

### Index concept

An index is a data structure that sorts the values ​​of one or more columns in a database table. Indexes provide quick access to specific information in database tables. One of the main purposes of the index is to speed up the retrieval of data in the table, which is to assist the information searcher to find the auxiliary data structure of the record ID that meets the constraint as soon as possible.

### Index usage scenario

Often need to search on the column. On the column as the primary key. Often used on connected columns, these columns are mainly foreign keys, which can speed up the connection. It is often necessary to search on a column based on the range. Often need to sort on the column. Not suitable for columns that are rarely used in queries. Not suitable for columns with few data values. For example, the gender column of the personnel table, the column of the boolean data type. Not suitable for columns that are defined as text, image, and a large amount of data. Not suitable for use when the performance requirements for modification are much greater than search performance. Because when you increase the index, it will improve the search performance, but will reduce the performance of the modification. Not suitable for containing NULL values, as long as there is a column with a NULL value in the composite index, then this column is invalid for this composite index. It is not suitable to use like "%aaa%" for index fields, and index can be used if non-use is not "aaa%". Not suitable for calculations on columns, which may result in index invalidation. Not suitable for use with NOT IN and &lt;&gt; operations.

### Advantages of index

Speed ​​up the retrieval of data. &nbsp; &nbsp; &nbsp; In the information retrieval process, if the grouping and sorting clauses are used, the indexing can effectively reduce the grouping and sorting time required in the retrieval process, and improve the retrieval efficiency. &nbsp; &nbsp; &nbsp; By using an index, you can use the optimization hider to improve system performance during the query.

### The disadvantage of index

Creating an index and maintaining an index takes time, and this time increases as the amount of data increases, such as INSERT, UPDATE, and DELETE on the table. In fact, the index is also a table, which holds the primary key and the index field. The index needs to occupy the physical space.

### Create an index

1. CREATE INDEX 'Index Name' On 'table Name' (simple index)
2. CREATE UNIQUE INDEX 'Index Name' On 'table Name' (UNIQUE index)
3. CREATE INDEX 'index name' ON 'Table Name'&nbsp; (Combined index)
4. CREATE INDEX 'index name' ON 'Table Name'&nbsp; (Descending index)

Note when using a composite index: Only the first field can appear in the query condition. Therefore, placing a frequently applied field in front of the composite index will make the system use this index as much as possible and play the role of indexing.