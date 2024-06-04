# **LAB REPORT 5**
## Original post from student
![Screenshot of symptom](labreport_5_symptom2.png)
When I run my grader script on a student submission that has no bugs, it fails my tests. I have two tests in my TestListExamples.java that I know works because I used it to test my own ListExamples. Could the student submission be buggy? But I am using the repo that has the bugs corrected.

## TA response
Is there a way to see the exact output from compiling and running the files in your script?

## Follow up student post
I saved my compiling and running output in a file. Here is what it contains after another run of my script.
![Screenshot of results.txt](labreport_5_catresults.png)
It looks like it can't find my TestListExamples class because I have it running TestListExamples.java in my script. The tests it's running are not my tests. I think I need to check my script a little closer.

## Setup information
Structure of working directory:\
![Screenshot of directory](labreport_5_directree.png)
Contents of grade.sh:\
![Screenshot of grade.sh](labreport_5_script.png)
Contents of TestListExamples:\
![Screenshot of TestListExamples](labreport_5_test.png)


## Part 2 - Reflection
I never realized how easy it was to quickly manipulate files straight from the terminal. Being able to create a script that compiles and runs a java program, capture the output of the program and use it elsewhere. The potential for automation from the terminal is almost limitless, and I am glad this class gave a good introduction to these concepts.


