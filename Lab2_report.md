# Lab Report 2

## Part 1:

**Code for ChatServer:**
  
```java
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
import java.util.List;

class ChatHandler implements URLHandler {
    private final List<String> messages = new ArrayList<>();

    @Override
    public String handleRequest(URI url) {
        // Welcome message for the root path
        if ("/".equals(url.getPath())) {
            return "Welcome to the ChatServer!";
        }
        // Adding a message
        else if ("/add-message".equals(url.getPath())) {
            String query = url.getQuery();
            if (query != null) {
                // Assuming the order and presence of both 's' and 'user' parameters
                String[] params = query.split("&");
                if (params.length == 2) {
                    String[] messageParam = params[0].split("=");
                    String[] userParam = params[1].split("=");
                    if ("s".equals(messageParam[0]) && "user".equals(userParam[0]) && messageParam.length == 2 && userParam.length == 2) {
                        String message = messageParam[1];
                        String user = userParam[1];
                        // Constructing the chat message
                        String chatMessage = user + ": " + message;
                        messages.add(chatMessage);
                        // Building the response with all chat messages
                        StringBuilder response = new StringBuilder();
                        for (String msg : messages) {
                            response.append(msg).append("\n");
                        }
                        return response.toString();
                    }
                }
            }
        }
        // Response for unrecognized paths or missing parameters
        return "404 Not Found!";
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }
        int port = Integer.parseInt(args[0]);
        Server.start(port, new ChatHandler());
    }
}
```

## Request Made: `/add-message?s=Hello&user=jpolitz`

<img width="589" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/c7b3e86e-8824-4c6d-aef6-4757fb64da0e">

### Which methods in your code are called?

- `handleRequest(URI url)`: This method in `ChatHandler` is called whenever a request is made to the server.

### What are the relevant arguments to those methods, and the values of any relevant fields of the class?

- The relevant argument to `handleRequest` is `URI url`, which contains the request URI.
- In this case, `url.getPath()` would be `"/add-message"`, and `url.getQuery()` would be `"s=Hello&user=jpolitz"`.

### How do the values of any relevant fields of the class change from this specific request?

- Before the request, the `messages` list is empty.
- After parsing the query, the method constructs a string `jpolitz: Hello` and adds it to the `messages` list.
- The `messages` list now contains one element: `"jpolitz: Hello"`.

### Response and Class Field Changes:

- The response built by concatenating all messages in the list would be `"jpolitz: Hello\n"`, which is sent back to the client.
- The `messages` list changes by having one new element added to it. Initially, it was empty, and now it contains the string `"jpolitz: Hello"`.


----

## Request Made: `http://localhost:4000/add-message?s=How%20are%20you&user=yash`

<img width="630" alt="image" src="https://github.com/PIPICHANG-QAQ/cse15l-lab_reports/assets/134361847/b19b3f24-f9b3-47de-934b-6761c499ad2a">


### Which methods in your code are called?

- `handleRequest(URI url)`: This method in `ChatHandler` is invoked whenever a request is made to the server.

### What are the relevant arguments to those methods, and the values of any relevant fields of the class?

- The relevant argument to `handleRequest` is `URI url`, which contains the request URI.
- For this request, `url.getPath()` would be `"/add-message"`, and `url.getQuery()` would be `"s=How%20are%20you&user=yash"`.

### How do the values of any relevant fields of the class change from this specific request?

- Before this request, the `messages` list contains one element from the previous interaction: `"jpolitz: Hello"`.
- After parsing the query, the method constructs a new string `yash: How are you` and adds it to the `messages` list.
- The `messages` list now contains two elements: 
  1. `"jpolitz: Hello"`
  2. `"yash: How are you"`

### Response and Class Field Changes:

- The response built by concatenating all messages in the list would now be:
  jpolitz: Hello
  yash: How are you

This string, with each message on a new line, is sent back to the client.
- The `messages` list changes by having an additional new element added to it. Initially, it contained the string `"jpolitz: Hello"` from the first request, and now it additionally contains the string `"yash: How are you"` as a result of the second request.






