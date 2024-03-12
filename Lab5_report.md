## Lab Report 5 - Putting it All Together (Week 9)

### Part 1 - Debugging Scenario

**Original Post on Edstem**

**Title:** Issue with Java Program Output - Need Debugging

**Content:**

Dear TA,

I am currently working on the Java program `MyProgram.java`. I also ran this Java file by using a
bash script called `run.sh`. This Java program will read a text file, and print each line numbered.
However, there is an odd output. The programming omits some lines on the display.

Here’s a screenshot of my terminal after running `./run.sh`:\
<img width="372" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/dbffbdfe-1081-4d60-a10b-9d0e8a1345be">

Here's the code of my java file:
```java
import java.io.*;
public class MyProgram {
    public static void main(String[] args) throws IOException {
      BufferedReader reader = new BufferedReader(new FileReader("inputFile.txt"));
      String line;
      int lineNum = 1;
      while ((line = reader.readLine()) != null) {
        System.out.println(lineNum + ": " + line);
        line = reader.readLine();
        lineNum++;
      }
      reader.close();
  }
}
```
It seems like the bug might be related to how the program reads the file or processes the lines.
I’m a bit stuck on what could be causing this. Any suggestions on how to debug this would be
really helpful!

**Response from TA:**

Hi there,

Thank you for sharing the input.txt and java code. Based on what you said it could probably be a
problem of how your program reads lines up on the file. Many lines might go unnoticed by this
program. You could try to insert a print-statement inside your loop just before the value of line.
Using this method is possible to find out whether all the lines could be printed. You could add
like this:
```java
while ((line = reader.readLine()) != null) {
    System.out.println("Reading line: " + line);
    // rest of your code
}
```
**Follow-Up Post from Student:**

Thanks for the suggestion! Here's output after adding the code:\
<img width="219" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/677d89a0-1c70-448a-ae31-b0814292ab8f">

I compared this with my program’s output and noticed that indeed my program is skipping lines.
Here’s the bug: `readLine()` is erroneously called twice in the loop, during each loop iteration that
ought to read each individual line in the file and subsequently print it respectively. An incoming
line is read by the first `readLine()`. Nevertheless, another unexpected `readLine()` execution occurs
before the loop begins yet another iteration. This second call will read the next line but do
nothing with it; then, when the loop iterates, this line in the output will be skipped.

**Setup Info:**
- File & Directory Structure:
  - labreport5
    - MyProgram.java
    - run.sh
    - inputFile.txt
- Contents of MyProgram.java (before debugging):
```java
import java.io.*;
public class MyProgram {
    public static void main(String[] args) throws IOException {
      BufferedReader reader = new BufferedReader(new FileReader("inputFile.txt"));
      String line;
      int lineNum = 1;
      while ((line = reader.readLine()) != null) {
        System.out.println(lineNum + ": " + line);
        line = reader.readLine();
        lineNum++;
      }
      reader.close();
  }
}
```
- Contents of run.sh
```bash
javac MyProgram.java
java MyProgram
```
- Contents of inputFile.txt:
```txt
Hello
world
This
is
the
last
lab
report
```
- Command Line to Trigger the Bug:
```bash
./run.sh
```
- Fix:
  - Remove the second call to reader.readLine() inside teh while loop in MyProgram.java
 
### Part 2 - Reflection

During the latter part of this quarter, I had a really enlightening experience where I learned how to use Vim effectively. At first, I was a bit overwhelmed by Vim’s mode-based editing. As I started getting more hands-on during our labs I was amazed by how efficient it is for editing a single file. I
picked up some tricks like navigating quickly within a file using keyboard shortcuts for editing and
executing commands like search and replace. These techniques have significantly sped up my
coding process. It has given me a newfound appreciation for command-line tools, in software
development. Overall it has boosted my productivity too.

