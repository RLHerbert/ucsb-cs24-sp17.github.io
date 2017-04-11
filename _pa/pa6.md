---
layout: pa
num: pa06	
ready: false
desc: "Expression Trees"
assigned: 2017-05-30 09:00:00.00-7
due: 2017-06-05 23:59:00.00-7
---

[http://www.cs.ucsb.edu/~mikec/cs24/assignments/pa6/index.html](http://www.cs.ucsb.edu/~mikec/cs24/assignments/pa6/index.html) 
Worth: 100 points

PA6 can be done either in two-people teams or individually.

If you are working with a partner, be sure that both partners' names are in a comment at the top of the source code file, and that you properly form a group for this project in the submit.cs system.

Copies of express.h and expresstest.cpp either can be downloaded from the links below, or you can access them from your CSIL account by copying both files from the directory named ~cs24/pa6/ of the class account.
Implement class ExpressionTree as it is defined in express.h. Your implementation must be in a new file that you create named express.cpp.
This is a variation of Programming Project 1, pp. 534-535 of the textbook. Read the instructions (and hints) presented there. This variation adds three print methods to the problem presented in the text.
Implement each of the member functions (including both constructors, the destructor and the assignment operator) of class ExpressionTest.
Be sure to #include "express.h" and remember to type your name(s) and the date in the comment at the start.
The print functions must show the expression parts (numbers and operators and parentheses) separated by one space from each other, and there must be one blank space at the end of each printed expression. Print to cout.
Function printPre must print the expression in prefix notation, and printPost must print it in postfix notation. Function printIn must print parentheses surrounding each addition operation, but multiplication operations must not be parenthesized, and of course this function must print the expression in infix notation.
Compile and test your programs at CSIL. You may use expresstest.cpp for that purpose. The program will run one of nine tests, and here are sample results from our solution, showing each of the nine tests being run.
Submit express.cpp for project PA6 at https://submit.cs.ucsb.edu/, or use the following command from a CS terminal:
~submit/submit -p 602 express.cpp
Be sure to wait for the results of all nine tests. If you score 100/100 and you've followed all of the other rules, then you'll earn full credit.
Updated 11/17/2016, by C. Michael Costanzo.
Special thanks to Michael Main, University of Colorado, creator of many parts of this project.
