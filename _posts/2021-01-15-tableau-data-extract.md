---
published: false
---
# Tableau Data Extract (TDE)

It is a technique where a snapshot of required data is taken from the original data source, stored on disk, and loaded into a memory to render visualizations on Tableau. It is stored in .tde file format and it is referred to as TDE in the tableau community.

**What’s special about this?**

It is chiefly a column store. What is it? 

Consider we have a table with fields: Id, Store, Product, Customer, and Price.

The traditional row stores in most RDBMS tables look like this:

<img src="http://chidamodu.github.io/blog/images//row store.png">


But a column store looks like this:

<img src="http://chidamodu.github.io/blog/images//column store.png">


**Benefits of a column store**

1. Only reads the columns that are needed in a query.
2. Aggregating functionalities work faster with column data.
3. Helps with faster data compression and loading data faster.
4. Enables disk/CPU efficiency.

Tableau structures the data extract in that it creates a separate file (.tde file format) for every column in the underlying data source. As it retrieves data, it sorts, compresses, and adds the values for each column to its respective file. The individual column files, thus created, are in turn memory-mapped files. They are further combined with metadata to form a single memory-mapped file. 

When Tableau requests data from a TDE, the data in form of memory-mapped files is loaded directly into the memory by the operating system. This enables to query data, on Tableau, that is bigger than the available RAM and further allows speedy access to the data.



