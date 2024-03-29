## Karthik Srinivasan's CSE 15L Lab 3 Submission

*Part 1 Student's Question*

Hi, I'm trying to create a bash file that finds all the non-bash files with the term "Hello" in them. I have created a bash file but it just causes all the non-bash files in my working directory to be listed as files with the term hello in them. I don't know what the issue is because I am using grep in the find command. Perhaps I should just remove the echo command in find?

I have attached a screenshot of my code output as well as my bash script.

![Image](CSE15LLab5Pic1.png)

![Image](CSE15LLab5Pic2.png)

*Part 2 TA's Response*

Hi! The echo command will be executed on each non-bash file found and then the grep command will be executed. Sounds like there's an issue with ordering here.

*Part 3 Student's Solution*

Hello! Thank you for your message. Looks like re-ordering fixed the issue! I also added a -q modifier to my grep command so that the exact line isn't printed, only the file path that has the term "Hello." Thank you for helping me!
![Image](CSE15LLab5Pic3.png)

![Image](CSE15LLab5Pic6.png)


*Part 4*

I will describe the working directory and the changes in the bash script which fixed the bugs here. The screenshots which show the bash scripts running and their outputs is shown above. The full contents of the files before and after the bug fixing are also shown above.

The working directory is shown below. The only non-bash script file which contains the term "Hello" in it is Hello.java.

![Image](CSE15LLab5Pic4.png)

The issue with find-hello.sh was that it printed out every non-bash script file found by find. The main command in that script is shown below

  find . -type f -not -name "*.sh" -exec echo "Found 'Hello' in: " {} \; -exec grep "Hello" {} \; 

Clearly -exec is called on every non-bash script file found after that the file is checked for "Hello" and the line in which "Hello" is found is printed.

The improved command is as follows

  find . -type f -not -name "*.sh" -exec grep -q "Hello" {} \; -exec echo "Found 'Hello' in: " {} \;

In this command -exec echo is executed on files that return a 1 for grep "Hello". Consequently, only the paths of the non-bash script files that have the term "Hello" in them are printed. This file is Hello.java.

**Reflection**

I learned about jdb this quarter and I found it to be exteremely useful. I use Matlab a lot and I like the debugging tool on there so I'm glad there is a java equivalent. I enjoyed learning bash script in more detail and I think that will be extremely useful. Aside from this, I think the find command is the most useful command I have ever encountered and I'm very glad to have learned it.

