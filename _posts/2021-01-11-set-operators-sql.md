---
published: true
---
# SET Operators in SQL


There are a group of operators in SQL that we use to operate on the results of two or more queries/SELECT statements to achieve a new result. Let’s assume an Etsy-style marketplace to explain the operators. Say, we have two tables: customers and sellers where the table customers have both customers that have only bought items on Etsy (i.e, buyers) and customers that have also sold items on the website.


**UNION**

It helps to combine the results of two or more queries and has an added advantage of not returning duplicate rows in the result. The point to note is that the resulting queries do not have to be from, two or more, separate tables. We would like to take a look at both the number of customers and sellers in the past 30 days. Because the customers could also be sellers, we would like to avoid duplicates. UNION comes in handy in this situation.

Assuming today’s date: January 27, 2020, we would like to see the results, mentioned above, in the past 30 days. The query to achieve this:


<img src="http://chidamodu.github.io/blog/images//union.png">


We have used distinct because there could be more than one record per customer_id as well as per seller_id.


**UNION ALL**

It combines the results of two or more SELECT statements or queries and allows duplicate values. Say, we want to get a count per customer_id from both tables: customers and sellers. Here, customers that are only buyers will have a single count value (as we are selecting distinct customers and sellers in both the SELECT statements) and those that are both buyers and sellers will have two counts value.


<img src="http://chidamodu.github.io/blog/images//union_all.png">


**INTERSECT**

Now we task ourselves to create a table of unique customers that are both buyers and sellers. This can be achieved using INTERSECT. 


<img src="http://chidamodu.github.io/blog/images//intersect.png">


**EXCEPT (or MINUS)**

It returns the rows that exist in one, but not in the results of both the queries, say we are comparing two queries. We ought to take a look only at the customers that are buyers, but not sellers.

<img src="http://chidamodu.github.io/blog/images//except.png">



