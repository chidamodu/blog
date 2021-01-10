---
published: true
---
# Reshaping using Pivot_Table in Pandas


Let’s create a table called a dataframe (typically denoted as df) in pandas comprising students names and their scores in subjects: English, Math, and Physics. 

<img src="http://chidamodu.github.io/blog/images//creating dataframe.png">


Our table looks like this:

<img src="http://chidamodu.github.io/blog/images//a look at the dataframe.png">


The subjects and scores are created as row values. But we would like to take a cohesive look at the students’ performance by pivoting the subjects, from row values to columns. This can be achieved using the pivot_table option in pandas. Thus every row in our resulting dataframe reflects each student’s record.

<img src="http://chidamodu.github.io/blog/images//pd.pivot without fill-value.png">


We can fill the missing values represented as NaN using the fill_value option.

<img src="http://chidamodu.github.io/blog/images//pd.pivot fill value.png">




