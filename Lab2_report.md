# Analyzing the NumberServer.java Code

Analyzing the provided `NumberServer.java` code gives us a clear picture of how the server operates. Here's a breakdown of the key components and functionalities:

## Handler Class:

- Implements the `URLHandler` interface.
- Maintains a single piece of state: an integer `num`, initialized to 0.

## handleRequest Method:

This method processes incoming URI requests. It checks the path of the URI and performs different actions based on the path:

- **Root Path ("/")**: Returns the current value of `num`.
- **Increment Path ("/increment")**: Increments `num` by 1 and returns a confirmation message.
- **Add Path ("/add")**: Extracts a query parameter, adds its value to `num`, and returns a message showing the amount added and the new value of `num`. This path expects a query in the format `/add?count=<number>`.
- If the URI path does not match any of the above, it returns a "404 Not Found!" message.

## NumberServer Class:

- Contains the `main` method, the entry point of the program.
- Checks if a port number is provided in the command line arguments; if not, it prints an error message and exits.
- Parses the provided port number and starts the server on that port using the `Server.start` method and an instance of the `Handler` class.

## Error Handling and Edge Cases:

- The code lacks explicit error handling for invalid input. For example, if a non-integer value is passed as a port number or as a parameter to the `/add` path, the program will likely throw an exception.
- There is no check for integer overflow in the `Handler` class. Continuously incrementing or adding large numbers could lead to unexpected behavior when `num` exceeds the range of an integer.

## Possible Questions and Considerations:

1. How does the server handle concurrent requests, especially when they modify `num` simultaneously?
2. Are there any security concerns, such as SQL injection or Cross-Site Scripting (XSS), with the way parameters are handled?
3. How can the program be extended or modified to handle more complex operations or maintain more state?
4. What happens if the `num` variable overflows, and how can this be mitigated?
5. How could error handling be improved, for example, by catching exceptions related to number parsing?

# Experimenting with URLs

Based on `NumberServer.java`, try different URL paths and queries:

## Increment Path
- **Description**: Add `/increment` to your server's URL. This path will increase the number and display a confirmation message.
- **Example**: `https://0-0-0-0-4000-1jo5p80mhaciis28q86varuo8k.us.edusercontent.com/increment`
  <img width="1217" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/45aadeaa-180d-456a-bbb2-a10873297f0e">


## Add Path
- **Description**: Use `/add` with a query, like `/add?count=2`. This adds a specific number to the total.
- **Example**: `https://0-0-0-0-4000-1jo5p80mhaciis28q86varuo8k.us.edusercontent.com/add?count=2`
  <img width="1220" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/2cb1f448-6d91-4bce-94f6-5c851f18f715">


## Root Path
- **Description**: Accessing the root path (just the server URL) should show the current number.
- **Example**: `https://0-0-0-0-4000-1jo5p80mhaciis28q86varuo8k.us.edusercontent.com/`
  <img width="947" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/4966aa13-6756-48ff-84bd-9f6788244cf0">


## Error Handling
- **Description**: Try an undefined path to see the "404 Not Found!" response.
- **Example**: `https://0-0-0-0-4000-1jo5p80mhaciis28q86varuo8k.us.edusercontent.com/123`
  <img width="840" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/20cb85a3-34d9-49a5-9bc4-00a4a4c1dd59">

## Differences between `/add` and `/increment` Paths in `NumberServer.java`

## `/increment` Path
- **Functionality**: Increments the `num` variable by 1 each time the path is accessed.
- **Usage**: No additional parameters required. Simply append `/increment` to the server's URL.
- **Example**: Accessing `http://localhost:4000/increment` will increase `num` by 1.

## `/add` Path
- **Functionality**: Allows incrementing the `num` variable by a specific amount, specified as a query parameter.
- **Usage**: Requires a query parameter (e.g., `count`) with the value to add to `num`.
- **Example**: To increase `num` by 2, access `http://localhost:4000/add?count=2`. The server parses the request, extracts the value `2` from `count`, and adds it to `num`.

In summary, `/increment` is for a fixed increment of 1, while `/add` allows specifying the increment amount.

# Run the Server
<img width="913" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/4a655e07-1be2-4dab-855e-43bccf8de472">

# Brainstorming Web Server Applications

## Ideas for Server Applications

**Objective:** To brainstorm applications that can be developed using a Java-based web server.

**Potential Applications:**

1. **Online Survey Platform:** 
   - Create a web server to host and manage online surveys or quizzes.
   - Handle user responses, store results, and provide statistical analysis.

2. **Event Management System:** 
   - Develop a system for event registrations, ticketing, and attendee information.
   - Include features like event creation, attendee tracking, and email notifications.

3. **Educational Content Repository:** 
   - Build a platform for educators to upload and organize educational resources.
   - Allow students to access and download materials like notes, assignments, and readings.

**Additional Tools/Knowledge Needed:**

- **Database Integration:** Familiarity with databases (e.g., MySQL, MongoDB).
- **Front-End Development:** Basic knowledge of HTML, CSS, and JavaScript.
- **Security Measures:** Understanding of web security practices.

## Code Synchronization Issue on ieng6

### Understanding Code Discrepancy

**Objective:** Determine why personalized code edits are not reflected on the ieng6 server.

**Problem Statement:** Custom edits, such as displaying "[Your Name] : <number>", made in the local environment are not appearing on ieng6.

### Discussion Points

**Possible Causes:**

- The updated code has not been deployed to ieng6.
- Version control issues with different code versions on local and ieng6 server.

### Possible Solutions

**Using GitHub for Code Synchronization:**

- **Step 1:** Push the updated code to a new GitHub repository from your local environment.
- **Step 2:** On ieng6, pull the latest code from the GitHub repository.
- **Step 3:** Verify the changes by running the server again on ieng6.

## Accessing URLs from the Command Line with curl
<img width="1451" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/acb10a05-1e1e-4e1b-9195-8a3276281b8e">

# Search Engine
<img width="1274" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/96278342-74ed-4d4f-95ba-140279614e62">
<img width="1067" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/b81cd3db-8c5a-48b2-8c8a-4eaffab2516f">

## Understanding Data Storage

### Storage Location
- **Where It's Stored**: The list of strings is stored in the server's memory.
- **Management**: This list is managed by the `SearchHandler` class within the `SearchEngine.java` program.

### Lifespan of Data
- **Persistence**: The data exists only as long as the server process is running.
- **Data Loss**: Once the server is stopped, the data in the list is lost.

### Implications
- **Non-Persistent Data**: The list is not persistent across server restarts.
- **Server Restart Behavior**: If the server restarts, the list starts empty again.

