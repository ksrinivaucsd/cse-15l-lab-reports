**Karthik Srinivasan's CSE 15L Lab 4 Submission**

**Step 4**

I logged into ieng6 by pressing the keys 

~~~
ssh cs15lfa23dg@ieng6.ucsd.edu<Enter>
~~~

I already had the public key set up so I did not have to press more keys to enter the passcode.

![Image](CSE15LLab4Pic1.png)

**Step 5**

I pressed 

~~~
<Alt> + <tab>
~~~

Then I pressed 
~~~
<ctrl> + <c>
~~~

to copy the url from github which contains the ssh URL for the GitHub repo.

I then pressed the keys below to paste the ssh URL for the GitHub repo and clone the repository.

~~~
<Alt> + <tab> git clone <ctrl> + <v> <Enter>
~~~

![Image](CSE15LLab4Pic2.png)

**Step 6**

I pressed the following keys to enter the cloned repository.

~~~
cd cs <Tab> <Enter>
~~~

I pressed the following keys to run the tests and they failed.

~~~
*bash test.sh*<Enter>
~~~

![Image](CSE15LLab4Pic3.png)

![Image](CSE15LLab4Pic4.png)

**Step 7**

I typed in the following to enter ListExamples.java.

~~~
vim L<Tab> <.> <Tab> <Enter> 
~~~

I then pressed the down key 41 times and the right key 11 times

~~~
<down>(x41)<right>(x11)
~~~

I then pressed 

~~~
xi2
~~~

This changed ListExamples.java to the right file.

![Image](CSE15LLab4Pic5.png)

**Step 8**

I pressed the following to run test.sh again. The tests ran successfully.
~~~
<up>(x2)<Enter>
~~~

![Image](CSE15LLab4Pic6.png)

**Step 9**

I typed the following to push the changes to GitHub.

~~~
git add --all <Enter>
git commit -m "changes lab4" <Enter>
*git push* <Enter>
~~~

There was nothing to commit as I had made these changes during lab and forgot to take a screenshot.

![Image](CSE15LLab4Pic7.png)
