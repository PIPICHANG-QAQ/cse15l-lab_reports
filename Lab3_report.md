## Lab Report 3
### Part 1
#### Failure-Inducing Input
The provided JUnit test correctly identifies a failure-inducing input for the buggy program. The test attempts to reverse an array `[1, 2, 3]` and expects the result `[3, 2, 1]`.
```java
@Test
public void testReversedFailure() {
    int[] input = {1, 2, 3};
    assertArrayEquals("The array is not properly reversed", new int[]{3, 2, 1}, ArrayExamples.reversed(input));
}
```

#### Input That Doesn't Induce a Failure
An input that doesn't induce a failure is not explicitly provided, but we can infer that any test case which does not check the content of the returned array might pass, such as checking the length of the array instead of its content.
```java
@Test
    @Test
    public void testReversedNoFailure() {
        int[] input = {0,0,0};
        assertArrayEquals("The array is not properly reversed", new int[]{0,0,0}, ArrayExamples.reversed(input));
    }

```
#### The Symptom
<img width="1280" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/1b6d7cf0-f730-4a60-b050-93da9016750c">


#### Before Debug:
```java
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
#### After Debug:
```java
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
#### Why the Fix Addresses the Issue
The fix addresses the issue by correctly filling the `newArray` with elements from `arr` in reverse order. The original code mistakenly attempted to modify the input array `arr` instead of using it to populate `newArray`. As a result, the corrected version returns a new array that is the reverse of the input, as expected, without modifying the original array.

### Part 2
#### `-i` Option
**Example1:**
- ```bash
  chang@MacBook-Pro-4 Lab_report3 % grep -i "example" ./technical/documentation.txt

  example
  ```
This command searches for the word "example" in the `documentation.txt` file, ignoring case. It's useful for finding text without worrying about the exact case used.

**Example2:**
- ```bash
  chang@MacBook-Pro-4 Lab_report3 % grep -i "config" ./technical/config/settings.conf

  config
  ```
This command searches for "config" in the `settings.conf` file, ignoring case differences. It helps in locating configuration settings regardless of their capitalization.

#### `r` Option
**Example1:**
- ```bash
  chang@MacBook-Pro-4 Lab_report3 % grep -r "function" ./technical
  
  ./technical/code/sample.js:function myFunction() {
  ./technical/code/utils.js:export function helperFunction() {
  ./technical/libraries/math.js:function add(a, b) {
  ```
This command recursively searches for the word `function` in all files under the `./technical` directory. It's beneficial for finding occurrences of `function` across multiple files.

**Example2:**
- ```bash
  chang@MacBook-Pro-4 Lab_report3 % grep -r "TODO" ./technical/
  ./technical/planning/todo.txt:TODO: Refactor login system
  ./technical/scripts/deploy.sh:# TODO: Add more error checks
  ```
This searches for "TODO" comments recursively in all files under the `./technical` directory. It's useful for identifying all pending tasks marked as "TODO" in the project.

#### `-v` Option
**Example1:**
- ```bash
  chang@MacBook-Pro-4 Lab_report3 % grep -v "deprecated" ./technical/documentation.txt
  This is the main function.
  It's recommended to use the new API.
  ```
This command shows all lines in `documentation.txt` that do not contain the word "deprecated". It's useful for filtering out lines that mention deprecated features.

**Example2:**
- ```bash
  chang@MacBook-Pro-4 Lab_report3 % grep -v "^#" ./technical/config/settings.conf
  
  username=admin
  password=secret
  ```
This command filters out comments (lines starting with #) in the `settings.conf` file. It helps in viewing the configuration file without the distraction of comment lines.

#### `-n` Option
**Example1:**
- ```bash
  chang@MacBook-Pro-4 Lab_report3 % grep -n "error" ./technical/logs/error_log.txt

  3:Error: Invalid user input
  15:Error: Failed to connect to database

  ```

This command searches for "error" in `error_log.txt` and displays the line numbers. It's particularly useful for pinpointing the exact location of errors in log files.

**Example2:**
- ```bash
  chang@MacBook-Pro-4 Lab_report3 % grep -n "function" ./technical/src/main.js

  2:function setup() {
  7:function initializeUI() {
  ```

This command finds "function" in `main.js` and includes line numbers in the output. It aids in quickly navigating to the function definitions or calls in the source code.

#### Sources:
- GNU Grep Manual:
  [https://www.gnu.org/software/grep/manual/grep.html]
- Linux `man` pages online:
  [https://man7.org/linux/man-pages/man1/grep.1.html]

