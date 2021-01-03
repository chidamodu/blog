---
published: false
---
# Break Vs. Continue in a for loop


## Use of 'break' statement

The Python 'break' statement immediately terminates a loop entirely. Program execution proceeds to the first statement following the loop body.

Lets consider a simulating situation where we draw numbers from a range until the limit 5000. When it reaches the limit,the program execution gets out of the loop in this context as we have the values iterated as the limit in the if statement.

<img src="http://chidamodu.github.io/blog/images//break statement in a for loop.png">



## Use of 'continue' statement

The Python 'continue' statement immediately terminates the current loop iteration. Execution jumps to the top of the loop and the controlling expression is re-evaluated to determine whether the loop will execute again or terminate.

Lets just say we ought to avoid printing "i" from a word "string". Here the continue statement has skipped the rest of the code inside the loop for the iteration where the if statement is true, i.e., if val=='i'. The loop then continues with the rest of the characters in "string".

<img src="http://chidamodu.github.io/blog/images//continue statement in a for loop.png">



