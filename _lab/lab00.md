---
layout: lab
num: lab00	
ready: false
desc: "Getting started with C++ functions and github's web interface"
assigned: 2017-04-03 14:00:00.00-7
due: 2017-04-07 11:59:00.00-7
---

# Introduction

Your first lab for this week is an introduction to programming on CSIL and in the Computer Science lab. You will write your first C++ program that will print a specific text out on your computer display. This lab must be completed INDIVIDUALLY. In the subsequent labs you are encouraged to work with a programming partner.

For this first lab, you will do the following:


* [Create a College of Engineering computer account if you don't have one already.](#step1){: data-ajax="false"}
* [Learn how to open a terminal on a lab or personal computer.](#step2){: data-ajax="false"}
* [Learn basic unix commands and create your lab00 directory.](#step3){: data-ajax="false"}
* [Learn how to edit a text file used for writing programming code.](#step4){: data-ajax="false"}
* [Write an actual program in C++.](#step5){: data-ajax="false"}
* [Compile your program and see if it runs.](#step6){: data-ajax="false"}
* [Submit your program for grading.](#step7){: data-ajax="false"}
* [Check Submission Results](#step8){: data-ajax="false"}
* [Create a github account and explore its web interface](#step9){: data-ajax="false"}
* [Perform basic git configurations](#step10)



## Step 1: Create an Engineering (CoE) Account <a name="step1"></a>

To log in to the machines in the Computer Science labs, or to connect remotely, you will need a **College of Engineering account**.

At this point, please go to [THIS LINK](https://ucsb.box.com/s/px12flf8g41m8g0gq4n6zqbbc9phkfrs) and view the important presentation from Engineering Computing Infrastructure on the College of Engineering accounts and computer labs.

You can create an account online at <a href="https://accounts.engr.ucsb.edu/create" target="_blank">https://accounts.engr.ucsb.edu/create</a>.

If you are enrolled in <i>any</i> CoE course this quarter (including CS24), you can create your account immediately. If you are not, you will need to contact the ECI Help Desk at <a href="mailto:help@engineering.ucsb.edu">help@engineering.ucsb.edu</a>.

<hr>

## Step 2: Open a Terminal <a name="step2"></a>

The first step in every assignment will be to open a <b>terminal window</b>, which will be the environment you use to write, compile, and run your programs.

If you are working on your laptop, whether Windows, Mac or Linux, you must remotely connect to `csil.cs.ucsb.edu`. For now its okay to connect to that server, however in the future please connect to one of the following machines:

* `csil-01.cs.ucsb.edu`
* `csil-02.cs.ucsb.edu`, etc. 
* etc.
* through `csil-48.cs.ucsb.edu`

You'll get much better performance on those individual machines, because they are much less heavily loaded and have newer hardware, as compared to `csil.cs.ucsb.edu`.



## Step 3: Create cs24 and lab00 directories<a name="step3"></a>

Now that your environment is set up, you next will need to create a directory (a folder is also called <i>directory</i> in Linux) that will contain all your work for the course. Then, inside that directory, you will need to create another directory to contain your work for this assignment.

To create your CS24 directory, use the <b>mkdir</b> command. Type the following in the terminal and press enter:

```
$ mkdir cs24
```

The <b>$</b> represents the terminal prompt; <i>you won't type this character</i>. Whenever you see it, that means that the following command is intended to be typed into the terminal window and run by pressing enter.

You can see list of files and directories in the current directory with <b>ls</b> command. Type the following in the terminal and press enter:

```
$ ls
```

You should be able to see the directory you just created i.e. **cs16** 

Now move into that new CS16 directory with the <b>cd</b> command as follows:

```
$ cd cs24
```

And create and move into a lab00 directory:

```
$ mkdir lab00
$ cd lab00   
```

At any time, you can check what directory you are current in with the command **pwd**. It will output the full path of the current directory. For example, if you are inside your <b>lab00</b> directory, you might see:

```
/cs/student/yourcsilname/cs24/lab00
```

Knowing how to navigate a UNIX environment and issue UNIX commands is VERY valuable to computer scientists and engineers. To learn more UNIX commands, there are lot of cool Web resources and books on the topic. This is one website I found that's a good introductory page: [Useful unix commands](http://mally.stanford.edu/~sr/computing/basic-unix.html)
<!--This link doesn't seem to work anymore
<a href="https://www.tjhsst.edu/~dhyatt/superap/unixcmd.html" target="_blank">https://www.tjhsst.edu/~dhyatt/superap/unixcmd.html</a>.
-->

<!--
<h3>Step 4: Create a C++ File</h3>

<p>Now that we have a directory to contain our work for the assignment, let's start writing our code. Create a file called <b>hello.cpp</b> with the <b>touch</b> command:</p>
<pre>$ touch hello.cpp</pre>

<p><span class="code">hello.cpp</span> is now a completely empty file that you will use throughout the rest of the assignment to write your C++ code.</p> -->

<hr>

## Step 5: Create and edit a file containing a C++ program <a name="step5"></a>

Now it's time to write a simple C++ program! Choose a text editor that you are comfortable: either vim or emacs. You may refer to these hint pages when using either editor [emacs hints](emacs_hints/) and some [vim hints](vim_hints/).

Create a new file named hello.cpp (using yoru favorite editor)

Type a comment at the top with your name and the date you are doing this lab. Note: this is IMPORTANT, and you should make it a habit to include such a comment at the top of every program you ever write - especially for this class - from now on. Remember that a C++ comment begins with two slashes (//).
Then type (or copy/paste) the following two lines after your header comment:
#include <iostream>
using namespace std;
Define a main function:
int main() { ... }
Inside main, use cout and its insertion operator to print exactly the following message:
Hello!
CS24 is fun.
Be sure the message is shown on two separate lines, and that a newline is printed after the second line too. There must not be any spaces before or after the text on either line. Make sure it matches the sample exactly.
Save the file, and quit the editor.

Use make to compile your program (later you will learn other ways to compile, but make is good enough for this lab). Then run it to make sure everything works. Here is a test of our solution (again, user input is bold):

-bash-4.3$ make hello
g++     hello.cpp   -o hello
-bash-4.3$ ./hello
Hello!
CS24 is fun.
If errors occur: (a) don't panic, and (b) don't immediately ask the TA for help! Instead, take a deep breath, and then actually read the message that comes up. It will often give a line number, and some hint as to what might be wrong.

Then, look at your program, around that line, and also immediately before that line. Often, if the error is reported on, say, line 15, it is because of a missing semicolon, on line 13 or 14, for example.

If you've really looked, and are still stumped after two or three tries, then you might ask the TA for help. But try to fix it on your own first.

When you are satisfied it works, proceed to the next step



## Step 7: Submit your program for grading <a name="step7"></a>

Once you are satisfied that your program is correct, then it's time to submit it.

<strong>Please remember that you must submit the program to obtain any credit for the assignment; just completing the program is not enough.</strong>

In this course we will use the <a href="https://submit.cs.ucsb.edu/" target="_blank">submit.cs.ucsb.edu</a> system. You can make a submission from either the command line on any CS machine, or from a Web browser.

If you don't have a submit.cs account, you will first need to create one. This can be done at 
<a href="https://submit.cs.ucsb.edu/form/user" target="_blank">https://submit.cs.ucsb.edu/form/user</a>.

Once you have an account created, login at <a href="https://submit.cs.ucsb.edu/session" target="_blank">https://submit.cs.ucsb.edu/session</a>.

Next, you need to join the CS24 course. Look for the "Join Class" link at the top of the page. It is in the top bar, as seen below:

<img src="submit-topbar.png" width="542" alt="submit.cs Top Bar" />

Once you see the list of all courses, click on the <b>"Join CS24_Mirza_s17"</b> button. You should then see CS24 appear on your homepage when logging in to the submit.cs system. 

Submit your code from the command line (i.e. in the terminal) on any CS machine, including the Phelps lab machines or the CSIL server. You can also use this method when logged in remotely. To submit the the <b>hello.cpp</b> file to this assignment by running the command:

	$ ~submit/submit -p 625 hello.cpp

The program will ask you to login <b>with your submit.cs username and password</b>. The password will not be printed to the terminal, but what you type will be used. It will also offer the option to save your credentials, so that you do not have login next time you submit. You may choose to do this or not. After the submission succeeds, you should see the program output something like:

	Results will be available at: https://submit.cs.ucsb.edu/submission/xxxxx

You can copy this URL and paste into a Web browser to reach the same submission result page as described above.

<hr>

## Step 8: Check Submission Results <a name="step8"></a>

After the 1 minute delay, the submit system will show your score and give you feedback on your submission. <em>Refresh the webpage after a minute to see this information.</em> This usually takes one of three forms:

<p>A correct submission with a score of 100. This means that your program passed all the tests for this assignment. Once you get to this point, you are finished with the assignment and will receive full credit. This case will look like this:</p>
<img src="correct-submission.png" width="233" alt="Correct Submission." />

<p>An incorrect submission with a score of 0 to 99. This means that your program failed 1 or more of the tests. For this assignment, the system will show both the expected output and the output your program generated side-by-side so that you can see what went wrong. You will need to fix your program, and then do Step 7 again to re-submit. This case will look like this:</p>
<img src="incorrect-submission.png" width="706" alt="Incorrect Submission." />

<p>Or a submission for which compilation failed. This means that your program caused compilation errors when the system tried to compile it. You will need to interpret the compiler output and fix the errors. The system will show you the compilation command that failed along with the full error message. This case will look like this:</p>
<img src="compilation-failure.png" width="499" alt="Compilation Failure." />

<p>You may submit your program multiple times before the deadline. You should really only submit after local compilation does not produce any errors and runs as expected - that's the most efficient and preferred way to do things. The score of the last submission uploaded before the deadline will be used as your assignment grade.</p>

<hr>


## Step 9: Create a github account and explore its web interface <a name="step9"></a>

If you have made it to this step, then you have successfully created a C++ program, tested it on a remote server (csil.cs.ucsb.edu) and made a successful submission. We would however like you to do one more step to get familiarized with git and github. Here is some motivation: When developing large programs, it is very useful to save working versions of your code that you can always revert to. Trying to do this manually often leads to total chaos!! That's why professional programmers use some kind of version control system (VCS). We will use a popular VCS called Git. With Git all versions of your code will be available to you and your collaborators (in later labs this would be your pair-programming partner) anytime, anywhere! It will also help the course staff view your progress as you work on the assignments.

1. Before we begin, read this article to get an overview of git: [https://ucsb-cs56-pconrad.github.io/topics/git_overview/](https://ucsb-cs56-pconrad.github.io/topics/git_overview/)

2. Create a github account. You can sign up for a free account on [Github](https://github.com/). Use your official ucsb email when signing up. Sign into github with your github account. 

3. Now that you have a github account you can create a git repo. The concept of a repo was explained in the article that you just read. New projects always start with this step. Since Github promotes "open source" projects, repos created under your default github account are *public*. This means that they are visible to everyone on the internet. However, for this class your assignments have to be "closed source", and not open to your classmates and others on the internet. This requires that you create *private* repos. These are repos that are only visible to you, your pair-partner and the instructional staff. You can only create private repos within our class organization on github: ucsb-cs16-wi17. So, the next step is to join our class organization.

4. To join our organization, follow these easy steps:

4a. click on this link:[ https://ucsb-cs24-sp17-signup.herokuapp.com/]( https://ucsb-cs16-wi17-signup.herokuapp.com/). You should see the following welcome message, click on the blue "sign in with Github" button:

![welcome](/lab/lab00/enter-org/pic1.png){:height="500px"}

4b. The next screen asks you to authorize our app to add you to our class organization. Click on the green "authorize application" button.

![authorize](/lab/lab00/enter-org/pic2.png){:height="500px"}

4c. Enter your github and you should see the following screen that shows you were successfully added to our class organization:

![success](/lab/lab00/enter-org/pic4.png){:height="500px"}


5. Read this article on [creating a github repo under an organization](https://ucsb-cs16.github.io/topics/github_com_create_private_repo_under_org/). Open a browser and navigate to our class organization on github: [ucsb-cs16-wi17](https://github.com/orgs/ucsb-cs16-wi17/dashboard). Click on the green button that says "New repository", and follow the steps from the ["creating a github repo under an organization"](https://ucsb-cs16.github.io/topics/github_com_create_private_repo_under_org/) article, to create a PRIVATE repo containing only a README.md and a .gitignore. See screenshot below:

![new-repo](/lab/lab00/enter-org/pic5.png){:height="500px"}



Your repo name should be lab00_your-github-username. For example if your github username is jgaucho, you should name your repo as lab00_jgaucho. Make sure you select the PRIVATE option when creating your repo.

6. Check to see if you have the files: README.txt and .gitignore in your repo. If you don't see these files, contact an instructor or ask for help on Piazza. To learn more about the .gitignore, read this article: [About gitignore](https://ucsb-cs56-pconrad.github.io/topics/git_gitignore/)

7. Use github's web interface to upload your hello.cpp file. We recommend that you be physically present on a lab machine where you have access to a web browser and a local copy of your hello.cpp program. On your web browser, navigate to your repo on github. If your repo name is lab00_jgaucho, the link to the repo is: [https://github.com/ucsb-cs16-wi17/lab00_jgaucho](https://github.com/ucsb-cs16-wi17/lab00_jgaucho). Click on the "Upload files" button as shown below. 

![git-file-upload](/lab/lab00/git-repo-pic_ink-upload.jpg){:height="500px"}

<p>You should see the following screen:</p>

![git-upload-hello](/lab/lab00/upload-hello-cpp.png){:height="500px"}

8. Now either drag and drop the "hello.cpp" file from your machine or use the "Choose your files" option to browse through your local directory and upload the file. Then press the green "Commit new files" button. Navigate back to your repo to see that the hello.cpp file is correctly listed along with the other files. Click on it and you should see your code on github's web interface. For more practice and fun upload a picture of yourself. Use your name as the file name. Continue to explore the web interface of your github repo. For example, try clicking on the "commits" link in your repo. What does that show you and what do you think it means? 

Congratulations on completing your introductory exercise to github. We will continue to explore git in the subsequent assignments.


## Step 10: Done!

<p>You can continue to make submissions on submit.cs until your submission receives a score of 100/100. If you have a perfect score and  have also successfully uploaded your code and picture to your github repo, you are done with this assignment. We will be grading the git part of this assignment manually on github. Congratulations on completing your first C++ program!</p>

<p>If you are in the Phelps lab or in CSIL, <b>make sure to log out of the machine before you leave</b>. Also, make sure to close all open programs before you log out. Some programs will not work next time if they are not closed. Remember to save all your open files before you close your text editor.</p>

<p>If you are logged in remotely, you can log out using the <b>exit</b> command in UNIX:</p>
<pre>$ exit</pre>
