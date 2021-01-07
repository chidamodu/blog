---
published: false
---
# RANK functions in SQL

**ROW_NUMBER()** 
This assigns a unique number to each row incremented by 1 from one row to the next one. It’s a window function and so it is used with the mandatory OVER() clause to specify which rows within a column or field the function will affect in simplest terms. For advanced specifications, one can use ORDER BY, to control the order in which the rows appear, within the OVER() clause. 

Why do we have the need to enumerate rows with unique numbers?
We love to categorize, order, and laud the best performance. When we ought to zoom in especially with regards to the top-performing products, the best departments measured in terms of productivity, the significant items sold, on an online shopping site, in each category, the top 10 pop records on Pandora for a year, and so on. ROW_NUMBER comes in handy to handle these situations.

Typically, ROW_NUMBER is used in the SELECT statement with OVER(). As mentioned above, we usually pair it with ORDER BY in the OVER() clause. Let’s see an example:

Table Exam has three fields: Studentname, Subject, and Marks.



The outcome of the above statement looks like this:



Because we are ordering by Marks, it sorts the Marks column in the default ascending order and assigns unique numbers to each resulting row starting from 1. Therefore, Kim and Clark with the same 90 marks, although for different subjects, get different RowNumber. 

But we would like to get a list of the top performers based on the Marks scored by them. We just add DESC keyword, for descending order, with ORDER BY as follows:


RANK
It specifies a rank that’s unique for each row. Sounds pretty similar to ROW_NUMBER! What’s the difference?

Let’s demonstrate that using the same Exam table: We are interested in pulling out the records of all the high scorers. 

The outcome of RANK looks like the following:



Thus RANK gives Kim and Clark the same ranks based on their scores, but ROW_NUMBER gives different numbers because the focus is on assigning unique values to the rows.


DENSE_RANK
It also specifies rank for each row, but it operates slightly differently than the RANK. Let’s again check out the top performers:


The outcome of DENSE_RANK looks like this:



Like RANK, DENSE_RANK also assigns the same rank for the same values, but it doesn’t skip the following rank. Notice how RANK skipped rank 3 after assigning the same rank 2 to Kim and Clark. DENSE_RANK is intuitive and is what we follow as a standard when designating ranks.

Most often we would like to group people or products, per se, in every department or category that are performing significantly higher. In the context of our example, that translates to finding the top scorers per each subject. We can do that using PARTITION BY. Let’s consider more rows in the Exam table for a better demonstration.

The output of PARTITION BY looks like this:




DENSE_RANKS initiates ranks for each subject, because of PARTITION BY, and doesn’t skip the following rank as showcased by assigning the same rank 3 to Fiona and Clark for Physics consequently followed by 4 without skipping ranks.
