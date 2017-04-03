---
layout: lab
num: lab06
ready: false
desc: "Implementing a queue"
assigned: 2017-05-16 09:00:00.00-7
due: 2017-05-16 11:59:00.00-7
---

# Goals for this lab

By the time you have completed this lab, you should be able to

* Implement a queue using an array
* Implement a queue using a linked list
* Appreciate the differences between the two types of implementations

# Step by Step Instructions

Step 1: Create a lab07 directory (in the first pilot's account)

First get together with your lab partner. If your regular partner is more than 5 minutes late, ask the TA to pair you with someone else for this week.

Select a pilot, log in, create a ~/cs24/lab07 directory, and make it your current directory.

Step 2: Get a copy of all the program files

There are six files to copy from the class account this week. You can copy them all at once using the Unix wildcard character '*' and then verify you got them all as follows:

-bash-4.3$ cp ~cs24/labs/lab07/* ~/cs24/lab07/
-bash-4.3$ ls
arrayQ.cpp  arrayQ.h  listQ.cpp  listQ.h  Makefile  testQ.cpp
Step 3: Learn two ways to implement a queue

Recall that a queue is a "first-in first-out" (FIFO) data structure. Similar to a stack, it has very few operations, as new entries are always added to the rear of the queue, and entries are only ever removed from the front. More queue ADT specifications, as well as ways that queues are applied, are topics covered in lectures and the textbook. Today's lab is all about implementing a queue two ways.

The first way discussed uses a static array, and so it has a fixed capacity. The second way uses singly-linked list nodes, so it can hold many more items.

Way A: How to use an array, with "circular" indexing

See the private section of arrayQ.h. The data items will be stored in the array named data. The number of items currently stored will be recorded in the size variable. The indices of the items at the front and rear of the queue are recorded in the front and rear variables. You will have to decide what indices to store in front and rear. Here is a suggestion from C++ Plus Data Structures, a 2013 textbook written by Nell Dale:


The beginning of the array becomes logically empty as front is incremented, so it is prudent to circle back around to reuse that portion of the array for later items:


As you can see, rear is incremented on every enqueue, and front is incremented on every dequeue. But increment does not simply mean ++ in this situation, because when the result of ++ equals the array size, then the index should increment to 0. You can either use an if/else structure to find the right value, or use the modulus operator, %, as follows:

incrementedIndex = (currentIndex + 1) % CAPACITY
The methods in the public section of arrayQ.h can be implemented as follows:

Queue()
Initialize front, rear and size to appropriate values.
enqueue(int n)
Assuming the queue is not full, the following three things must occur - but their order and exact details depend on how you are treating the front and rear indices: set the appropriate array element to n; increment rear; and increment size.
dequeue()
Assuming the queue is not empty, the following three things must occur - but order/details again depend on your approach: increment front; decrement size; and return the data item at the front of the queue.
clear()
Reset front, rear and size to their initial values.
isEmpty(), isFull() and getSize()
The size variable makes it very easy to implement these three methods.
Way B: How to use a linked list

See the private section of listQ.h. The data items will be stored in list nodes. The number of items currently stored will be recorded in the size variable. The front of the list should be the first node in the list, and the rear of the list should be the last node (think about why). The front and rear pointer variables are used to point at these nodes:


Both front and rear would point at the same node if there is only one item on the queue, and both would point at 0 (NULL) if the queue is empty.

Since memory for the nodes is dynamically allocated, this version requires a destructor at least (ignore for now that copying such a queue is unwise). Otherwise the class's interface is exactly the same as the array version. The methods are implemented as follows:

Queue()
Initialize front, rear and size to appropriate values.
~Queue()
Delete all the nodes, one at a time in a sensible order.
enqueue(int n)
No need to consider a full queue. Create a new node to store n. Append this node to the end of the list by using the rear pointer, and then point rear at this new node (also point front at it if it is the only item), and increment size. Here is an image of the operation from the Dale text: 
dequeue()
Assuming the queue is not empty, there are several things to do. Store the value of the item at the front to return at the end. Also store a copy of the front pointer to be able to delete this front node later. Point front at the next item. Delete the old front node. Decrement size. If the queue is now empty, then set rear to 0 (NULL). Finally, return the value that was at the front. Here is a Dale text image of the operation: 
clear()
Delete all the nodes. Also reset front, rear and size to their initial values.
isEmpty() and getSize()
The size variable makes it very easy to implement these methods. And isFull() is already implemented inline in listQ.h so don't redefine that method.
Step 4: Implement a queue both ways, and test your implementations

Select Way A or Way B to accomplish first; then do it the other way after you are sure your first way is working. Do not split this work with your lab partner - instead use your pair programming skills to work on your implementations together in sequence. We want each of you to experience implementing a queue both ways.

Edit arrayQ.cpp when you accomplish Way A,
And edit listQ.cpp when you do Way B.
In both cases, type your name(s) and the date at the top of the files you are editing, and then implement the methods as specified by the comments in these files (and their associated header files).
Pick a good time to switch roles between pilot and navigator - preferably before either of you gets tired, bored or frustrated.

If you have your textbook with you, please wait at least 15 minutes before trying to look up the solutions. One reason is we want you to be able to figure out the problems by yourself. Another reason is the textbook's techniques do not mesh exactly with the structure of this lab's problem, and that could confuse you.

Use the Makefile to compile, and use testQ.cpp to test your implementations. The use of both of these files differs depending on the implementation you are testing.

Way A (array implementation). Do not change testQ.cpp at all, and compile it by simply typing "make" at the command line:
-bash-4.3$ make
g++ -std=c++11 -o testQ testQ.cpp arrayQ.cpp
Way B (list implementation). First edit testQ.cpp to include the correct header file. Notice the 4th line of the original file is `#include "arrayQ.h"` but that must become `#include "listQ.h"` (or you can just turn that line into a comment, and uncomment the 5th line). Then use the "testlist" target in the Makefile as follows:
-bash-4.3$ make testlist
g++ -std=c++11 -o testQ testQ.cpp listQ.cpp
Except for one small difference, both implementations should produce the following results when you run testQ:

-bash-4.3$ ./testQ
beginning state
    size = 0, full = false, empty = true
enqueue first 8 multiples of 7
    size = 8, full = false, empty = false
dequeue two items: 7 14
    size = 6, full = false, empty = false
enqueue next 4 multiples of 7
    size = 10, full = true, empty = false
dequeue all items: 21 28 35 42 49 56 63 70 77 84
    size = 0, full = false, empty = true
enqueue 5, then 10
    size = 2, full = false, empty = false
clear
    size = 0, full = false, empty = true
Those results are from our arrayQ solution. The one difference is that the listQ solution would have "full = false" when the size is 10 items.

Step 5: Submit arrayQ.cpp and listQ.cpp

Submit Lab07 at https://submit.cs.ucsb.edu/, or use the following command from a CS terminal:

~submit/submit -p 594 arrayQ.cpp listQ.cpp
If you are working with a partner, be sure that both partners' names are in a comment at the top of the source code files, and be sure to properly form a group for this project in the submit.cs system.

50/50 is a perfect score.

Evaluation and Grading

Each student must accomplish the following to earn full credit [50 total points] for this lab:

[25 points] arrayQ.cpp is saved, it has your name(s) in a comment at the top, it compiles and executes properly, and scores 25 on the submit.cs system tests.
[25 points] listQ.cpp is saved, it has your name(s) in a comment at the top, it compiles and executes properly, and scores 25 on the submit.cs system tests.
[-0 to -50 points, at the TA's discretion] The student arrived on time to their lab session, and worked diligently on CS24-related material until dismissed.
This lab is due by 11:59 pm Friday night.
Optional Extra Challenge

Add an appropriate copy constructor and an assignment operator to the listQ version, to achieve the usual value semantics for objects of the class.

If you still have some time, why not adapt an STL vector<int> to solve the problem? Create a new version of the class definition, vectorQ.h, to define the private data. You shouldn't need a size variable, because the vector will keep track of its own size. Then write vectorQ.cpp to implement it. Look up the vector methods at http://www.sgi.com/tech/stl/Vector.html.

Just for fun, why not try to adapt a version of testQ.cpp to test the STL queue class? Does the test program require many changes?

Prepared by Michael Costanzo.