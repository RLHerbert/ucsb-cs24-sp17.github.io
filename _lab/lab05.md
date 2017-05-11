---
layout: lab
num: lab05
ready: true
desc: "Linked lists contd"
assigned: 2017-05-09 09:00:00.00-7
due: 2017-05-12 23:59:00.00-7
---
<div markdown="1">


There will be no new lab. Instead, please use the lab time to work on your pa04.

* You must still come to lab and get checked off by your mentor on the following items:

	1. Create a github repo for this lab and clone it to your account on CSIL
	2. Write a Makefile for pa04. Be sure to compile your code with the -g flag so that you can run gdb on it. Push your latest Makefile to github at the end of the lab.
	3. Complete the implementation of the set_recent() method of the polynomial class.
	4. Complete the implementation of all the methods of the polynomial class that would allow you to pass test1() and test2() of the provided test code in polyexam2.cxx. Use the set_recent() method as appropriate. You must test each method before moving on to the next one - please use GDB! Here is a tutorial that goes over some of the commands I introduced in class (and you probably didn't have time to write out)[GDB tutorial](https://www.cs.umd.edu/~srhuang/teaching/cmsc212/gdb-tutorial-handout.pdf)
	5. Demostrate that you can use gdb on your code, when it is compiled with either of the provided test code: polyexam2.cxx and polytest2.cxx. You should know how to run the tests within polyexam2.cxx within gdb, set break points in ANY file and step into functions that you wrote in the previous step
	6. Pass all the test cases of test1() and make progress with passing the test cases of test2() provided in the polyexam1.cxx file 
	7. Demonstrate that you can run valgrind on your program by generating a valgrind report and uploading it as a text file to your git repo. Here is the command 
	```
	/usr/bin/valgrind --leak-check=full ./polyexam1 7
	```
	Replace polyexam2 by the name of your executable and 7 by the argument to your program (test case number)
	8. Push the latest version of your code to github and submit on submit.cs by typing the following command on the terminal:

```
	~submit/submit -p 724 poly2.cxx
```

Each of the above steps carries 10 points for a total of 80 points for this lab.
