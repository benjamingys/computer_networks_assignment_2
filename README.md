# computer_networks_assignment_2
Assignment 2: HTTP Client and HTTP Server using Java Sockets
The goal of this assignment is to gain experience in application layer network programming through Java Sockets [1] and get familiarized with the basics of distributed programming. Specifically, this assignment will help to understand the Hypertext Transfer Protocol (HTTP), which is one of the widely used protocols on the Internet.
Assignment Description
The assignment consists of two parts to develop a program in the classic client/server paradigm, such as a chat application. In the first part, you will implement a chat user, an HTTP client that can request and give information (e.g., web pages) from and to an HTTP server. In the second part of the assignment, you will build a server, an HTTP server that can hold and serve information, such as hosting a web page.
A real world example of a client/server scenario is Messenger Bots on Facebook1 that basically take and give input and output based on user messages. Here, the user is a chat client that speaks to a server which also acts as the bot.
In this assignment, you will approximate this through users that interact with the server/bot which can store text and provide web pages.
This exercise illustrates that correctly following protocol standards allows your programs (i.e., user and server) to interact with each other but also with other people’s programs using application layer networking concepts.
1) Chat User - HTTP Client
In the first part, you will build a chat user as an HTTP client that communicates with a HTTP server that serves information such as web pages for end users. The HTTP client program should support HTTP version 1.1. For your assignment, you should implement a HTTP client, which accepts the following arguments in the command line as follows:
CommandLine$ ChatClient HTTPCommand URI Port
In the above line, the ChatClient denotes the name of your java executable. The HTTPCommand refers to HEAD, GET, PUT or POST. You can use any URI’s such as http://www.example.com or http://www.google.com to test your client implementation. And, the default port number of 80 should be used to connect with the server.
After each request, your client should display the response received from the HTTP server on the terminal and also store the response in an HTML file locally. When you retrieve a webpage from the server, you should scan the HTML file
1 See https://developers.facebook.com/docs/messenger-platform/getting-started/sample-apps for some fun examples. If you need medical aid, this one might help: https://www.messenger.com/t/HealthTap
￼￼￼￼￼
and check for embedded objects such as images. If you find an embedded object in the HTML file, you should use the GET command to retrieve those objects as well. In order to reduce the complexity, we do not expect you to retrieve all types of embedded objects. During the demonstration, you should at least retrieve image files from a HTTP server. The retrieved images should be stored locally.
For PUT and POST commands, your user should read a string from an interactive command prompt and send that onwards. These two commands will be tested with your HTTP server program.
For debugging purposes, we strongly recommend to use “telnet” [6]. Telnet enables you to connect to a remote server and issue HTTP commands through your terminal, where you can view the HTTP response of the server. An example is shown below:
￼2) Bot - HTTP Server
The bot program, or HTTP server, should host a simple web page on your local machine. This server should be multi-threaded to support multiple clients at the same time. The server should support the following client operations: HEAD, GET, PUT and POST.
A user should be able to retrieve the web page hosted on your server. The user can either be your HTTP Client program or any third party clients such as Firefox or Chrome. If you have followed the protocol standards correctly, any user will be able to interact with your server.
For the demonstration, we expect your bot to host a web page that can be retrieved using your HTTP Client program. If your HTTP Client program
retrieved the web page and the associated embedded objects correctly, then any third party clients such as Firefox or Chrome should be able to render it.
In the case of PUT and POST commands, your bot should store the data received from clients in a text file.
For the PUT command, the user input should be stored in a new text file on the server.
For the POST command, the user input should be appended to an existing file on the server. If the file does not exist, then the file should be created.
As your server/bot needs to support HTTP version 1.1, it should use persistent connections and support the if-modified-since HTTP header. Note that the host header field is mandatory for HTTP version 1.1.
Finally, you should at least support the following status codes on your server:
• 200 OK
• 404 Not Found
• 400 Bad Request
• 500 Server Error
• 304 Not Modified
Along with the status codes, the server should send the date, content type and content length headers to the client.
The server should respond with the “400: Bad Request” status code when the HTTP Client does not include the host header in its request for HTTP version 1.1.
General Guidelines
• You implement this assignment in Java but should mainly use the Sockets package to complete the assignment.
o You are not allowed to use the HTTPURLConnection package for this assignment.
o URI parsing may be done using the URI library of Java. However, you should not use the URL library to connect to a HTTP server. It is sufficient to support the URI of the format www.example.com instead of http://www.example.com.
o You can choose any parser to scan the HTML files, but you are not allowed to use any API’s from the parser library to retrieve the embedded objects. The parser should be used only to detect the embedded object tags and the associated URIs. You should use GET method to retrieve the embedded objects from the HTTP server.
• You should document your code. During the evaluation, we will go through your code and may ask you to explain how a certain method works in your code or to demonstrate certain functions.
• You should know the difference between HTTP 1.0 and HTTP 1.1 and be familiar with the HTTP protocol.Questions can be asked about this.
• For HTTP/1.0, a new connection should be made for each embedded objects.
• For HTTP/1.1, both the HTML content and the embedded objects should
￼
be received using the same connection.
• Your HTTP Server should handle multiple clients at the same time. Create
multiple tabs in your web browser to test this with your HTTP server.
• Telnet2 can be used to test and understand the HTTP commands. You can use telnet as a debugging tool during your implementation. For more information, see section 1.
• You can use the following URI’s to test your client program:
o www.example.com
o www.tcpipguide.com o www.jmarshall.com o www.tldp.org
o www.tinyos.net
o www.linux-ip.net
• The exercises and what your program must be able to do are explained while
leaving some room for interpretation. As such, creativity beyond the basic exercise is appreciated but the most important things are demonstrating working code supported by a good design and documentation. When choices are made, you should be able to motivate your choice.
Practical Information
• You should either work alone or in groups of two. You should email your group details i.e. names and student numbers to sven.akkermans@cs.kuleuven.be and stefanos.peros@cs.kuleuven.be on or before 10-03-2018. The subject of this email should be CN:HTTP.
• You have 2 weeks to complete the assignment. In the third week, you should demonstrate your assignment to the teaching assistants. You will be marked based on your performance in the demonstration.
• For students working in groups, both the students should be prepared to demonstrate the assignment. If you cannot explain your code, we will assume that you did not write it.
• The third session is only meant for marking your assignment. Therefore, you should be ready to demonstrate your code at the start of the third practical session. You will only be marked in your assigned session.
Marking Specifications
The following specifications will be used during the marking session.
HTTP Client Marking (worth 8 out of 20 marks)
1 If you are having issues, try https://stackoverflow.com/questions/16619080/cant-get-the- http-response-using-telnet-from-the-command-line
￼￼￼￼￼￼￼￼￼Mark
Expected Functionality
￼￼￼￼￼￼￼￼￼￼Below 2
Client is not functional or sufficiently demonstrated.
￼￼￼￼￼￼￼￼￼￼
￼￼￼￼￼2-3
Client works only with certain web pages.
￼￼￼￼￼￼￼3-4
Client works with all the web pages supporting HTTP 1.1, but not storing the web page and images correctly.
￼￼￼￼￼￼￼￼￼5-7
Client works correctly with HTTP 1.1 and the student has understood the protocol clearly.
￼￼￼￼￼￼￼￼￼8
As (B) with documented code and elegant design.
￼￼￼￼￼￼￼￼￼HTTP Server Marking (worth 12 out of 20 marks)
￼￼￼￼Mark
￼￼￼￼￼Expected Functionality
￼￼￼￼￼Below 5
￼￼￼Server is not functional or sufficiently demonstrated.
￼￼￼￼￼5-6
￼￼￼￼￼￼Server handles only one client.
￼￼￼￼￼6-7
￼￼￼￼Server supports HTTP 1.1, but has threading problems.
￼￼￼￼￼7-9
￼￼￼￼As above with the correct use of threading and proper support for status codes.
￼￼￼￼￼9-11
￼￼￼As above, server successfully serves the web page retrieved using your HTTP client program.
￼￼￼￼￼12
￼￼￼￼￼￼￼￼As above with documented code and elegant design.
￼￼￼￼￼
References:
1. Java Sockets. Link:
https://docs.oracle.com/javase/tutorial/networking/sockets/index.html
2. HTTP made really easy [Strongly recommended]. Link: http://www.jmarshall.com/easy/http/
3. The HTTP Specification: HTTP 1.0 (RFC 1945).
4. The HTTP Specification: HTTP 1.1 (RFC 2616).
5. The definition of embedded objects or MIME types (RFC 1521).
6. https://en.wikipedia.org/wiki/Telnet
￼￼