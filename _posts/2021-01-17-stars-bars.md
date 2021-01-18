---
published: false
---
# Stars and Bars - a combinatorial problem

It’s a combinatorial counting technique that has gotten its fancy name by graphically representing certain combinatorial theorems. Let’s define the theorem first and then see how it can be applied practically to solve a counting problem implemented in python. 


**The theorem**

We ought to place n available balls into k distinct buckets. To be more fitting to the name of the combinatorial technique, ‘Stars and Bars’, let’s consider the balls as stars * and consider a bar '|' like a wall between each of the k buckets. There are n stars and logically, there could only be k-1 bars in order to separate the balls into k distinct buckets. Adding the stars and bars, we get n+k-1 positions available (n are stars and k-1 are bars). According to the theorem, the number of ways to place n balls into k buckets is equivalent to choosing n positions in the available space of n+k-1 positions. 

This is denoted as:

<img src="http://chidamodu.github.io/blog/images//pic1_combinatorial.png">

Remember for k buckets and in a space of n balls, there can only be k-1 bars. So having n balls is analogous to having k-1 bars. Therefore the above term can be written as:

<img src="http://chidamodu.github.io/blog/images//pic2_combinatorial.png">

As per the combination formula, we have:

<img src="http://chidamodu.github.io/blog/images//pic3_combinatorial.png">

Applying the combination formula to our context of n+k-1 positions and k-1 bars, we have:

<img src="http://chidamodu.github.io/blog/images//pic4_combinatorial.png">

Reducing the above formula further we get:

<img src="http://chidamodu.github.io/blog/images//pic5_combinatorial.png">



Now, let’s apply the above formula and solve the **Count Sorted Vowel Strings** problem on Leetcode.



**The problem statement**

Given an integer n, return the number of strings of length n that consist only of vowels (a, e, i, o, u) and are lexicographically sorted. A string s is lexicographically sorted if for all valid i, s[i] is the same as or comes before s[i+1] in the alphabet. 

Example 1:
Input: n = 1
Output: 5
Explanation: The 5 sorted strings that consist of vowels only are ["a","e","i","o","u"].

Example 2:
Input: n = 2
Output: 15
Explanation: The 15 sorted strings that consist of vowels only are
["aa","ae","ai","ao","au","ee","ei","eo","eu","ii","io","iu","oo","ou","uu"].
Note that "ea" is not a valid string since 'e' comes after 'a' in the alphabet.

Example 3:
Input: n = 33
Output: 66045



**Solution**

The trick is to recognize that this problem can be solved using our transformed combinatorial formula above. Let’s use the analogy comprising balls, buckets, and bars, from above, to look at the problem. The problem asks to find n-length strings consisting vowels only from this: {‘a’, ‘e’, ‘i’, ‘o’, ‘u’}. If there are only 5 buckets, there can be only 4 bars. Likewise, in the problem there are only 5 vowels and thus there can be only 4 bars. So n represents the n-length strings we have to find in the problem using the 5 vowels. Thus k represents the 5 vowels. Our combinatorial formula becomes:

<img src="http://chidamodu.github.io/blog/images//pic6_combinatorial.png">


**Python implementation**

<img src="http://chidamodu.github.io/blog/images//python implementation.png">

We want our solution in integer format, so we use the division operator //. This divides the number on its left by the number on its right, rounds down the answer, and returns a whole number.



**Point to remember**

The combinatorial formula worked for the problem because of the constraint provided in the second line in the problem statement:

A string s is lexicographically sorted if for all valid i, s[i] is the same as or comes before s[i+1] in the alphabet. 

This line means that there can’t be formations in reverse order or cyclic manner. The following strings are invalid:
1. Reverse order: ‘ea’
2. Cyclic manner: ‘ua’





