---
published: true
---
# Difference between View and Table

A table is a database object that can physically store data. So a table can be updated, deleted, and even changed by adding more records.

A view can be thought of as a select statement that can be built on multiple tables. If indexed, the view gets saved in the database. But a view doesn’t store any data. A view cannot be updated, but it reflects any changes happen in the source tables.


**But why we need a view?**

Let’s say we have a complex query involving multiple tables calculating commission for our sales representatives every month. Instead of querying from the database every month, we could save a view and query from it whenever we need to calculate the commission. 


**Benefits**

1.Saving space comes as an inherent advantage as views cannot store any data.

2.It can act as a layer of abstraction and therefore provides a simple and easy usage to end-users hiding the complexities of underlying tables in a database.

3.Can be used to maintain security by allowing the users to access only non-sensitive information, in the views, thereby protecting sensitive data in the tables.

 


