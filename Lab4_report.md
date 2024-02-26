## Lab Report 4
### Step 4: Log into ieng6
**Screenshot**:\
<img width="827" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/a31fab4a-54e1-4ea3-b8dd-059339af926d">

`ssh tiw036@ieng6.ucsd.edu<enter>`\
I used this command to log into the ieng6. I do not need to type the password.

### Step 5: Clone my fork of the repository from my Github account (using the SHH URL)\
**Screenshot**:\
<img width="818" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/5aea12e0-c05b-4780-afbc-f841d910f414">

`git clone git@github.com:PIPICHANG-QAQ/lab7.git<enter>`\
I used the SSH url to clone my fork of the repository form my GitHub account

### Step 6: Run the tests, demonstrating that they fail

**Screenshot**:\
<img width="814" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/4121474c-a4cb-404c-978c-b5a6ce621c9d">

`cd lab7<enter>`\
I changed to lab 7 directory

`bash test.sh<enter>`\
I'm telling the Bash shell to execute the commands written inside the test.sh script file.


**In the `test.sh`:**\
`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java`\
It compiles all Java source files in the current directory, making sure that any changes I've made to the source code are included in the tests I'm about to run.\
`java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests`\
After compilation, it invokes JUnit to run the specified test class (`ListExamplesTests`). JUnit then executes each test method found in the class.


### Step 7: Edit the code file to fix the failing test
**Screenshot**:\
<img width="828" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/f1f6cf1c-5a09-4312-b700-8d26913da725">
<img width="815" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/84df2920-8827-456b-815c-418490acf631">

`ls<enter>`\
I used this command to see the files in the lab7 directory

`vim ListExamples.java<enter>`\
I used this command to open the file ListExamples.java in vim

`/index1<enter>nnnnnnnnnce index2<esc>:wq<enter>`\
I used this command to first search pattern
“index1” in the file. Then I pressed n for 9 times to find the index1 which needed to be modified. I
pressed ce to delete the index1 and typed index2 to insert. I typed ESC to exit the insert mode. Finally,
I typed :wq to save and exit Vim.

`cat ListExamples.java`\
 I used this command to print the content of the file and check whether the
modification was successful.

### Step 8: Run the tests, demonstrating that they now succeed
**Screenshot**:\
<img width="839" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/4836e8e9-0c08-4a0a-aca3-24e0ef8208fe">

`<up><up><up><up><up><up><enter>`\
The `bash test.sh` command was up in the seatch history, so I used up arrow to access it. This run the testing script.

### Step 9: Commit and push the resulting change to my GitHub account
**Screenshot**:\
<img width="629" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/4e2a4008-b53a-4892-bb88-527471698833">

`git add ListExamples.java<enter>`\
 I used this command to stage the change I have made for ListExamples.java.

`git commit -m "Update the ListExamples.java"<enter>`\
I used this command to commit the changewith a message describing what changes I have made.

`git push<enter>`\
I used this command to push my commit to GitHub



