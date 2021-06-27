# Socket.io

## Review, Research, and Discussion

1. What is the benefit of transforming data into packets?
Packets are intended to transfer data reliably and efficiently. Instead of transferring a large file as a single block of data, sending smaller packets helps ensure each section is transmitted successfully.

2. UDP is often refereed to as a connectionless protocol. Why is this?
UDP is a connectionless protocol. It is known as a datagram protocol because it is analogous to sending a letter where you don't acknowledge receipt. Examples of applications that use connectionless transport services are broadcasting and tftp .

3. Can a socket server application have multiple socket connections?
Indeed, more specifically there is a special type of socket called a "listening" socket.
Normally a socket is associated with a combination of local IP, local port, remote IP and remote port.
A listening socket is different. It is not associated with any specific remote IP and port. It is associated with a specific local port. It may or may not be associated with a specific local IP.

4. Can a socket connection application be connected to multiple socket servers?
A server socket listens on a single port. ... Multiple connections on the same server can share the same server-side IP/Port pair as long as they are associated with different client-side IP/Port pairs, and the server would be able to handle as many clients as available system resources allow it to.

5. Can an application be both a socket server and a socket connection?

Yes, you definitely can.

You will have to use threads. I have implemented this in C++ by spawning a thread for a server and another thread for a client.

And here, one thing to notice that client host will be a localhost as both lie on the same machine and you are just creating two different socket with help of two different threads for sending and listening. (server being the listener, and client being the sender).

If you are using TCP, you might have to add a delay in connecting a client after a server thread is spawned, reason being the server socket need to be ready and listening when a client is trying to connect. And if it does not find an active server to connect to, the connection might fail.

## Document the following Vocabulary Terms

- Observer Pattern: The observer pattern is a software design pattern in which an object, named the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods.

- Listener: About 13,200,000 results (0.52 seconds)
An event listener is a procedure or function in a computer program that waits for an event to occur. ... The listener is programmed to react to an input or signal by calling the event's handler. The term event listener is often specific to Java and JavaScript.

- Event Handler: Image result for Event Handler in programming
In computer programming, an event handler is a callback subroutine that handles inputs received in a program (called a listener in Java and JavaScript). Each event is a piece of application-level information from the underlying framework, typically the GUI toolkit.

- Event Driven Programming: In computer programming, event-driven programming is a programming paradigm in which the flow of the program is determined by events such as user actions, sensor outputs, or message passing from other programs or threads.

- Event Loop: In computer science, the event loop is a programming construct or design pattern that waits for and dispatches events or messages in a program. ... When the event loop forms the central control flow construct of a program, as it often does, it may be termed the main loop or main event loop.

- Event Queue: Recall that the operating system interacts with the run-time support for the programming language to pass on events such as keystrokes and mouse movements. These are automatically resolved into high level events in terms of the components being manipulated by the program, such as buttons, etc.

- Call Stack: In computer science, a call stack is a stack data structure that stores information about the active subroutines of a computer program. This kind of stack is also known as an execution stack, program stack, control stack, run-time stack, or machine stack, and is often shortened to just "the stack".

- Emit/Raise/Trigger: js an event can be described simply as a string with a corresponding callback. An event can be "emitted" (or in other words, the corresponding callback be called) multiple times or you can choose to only listen for the first time it is emitted. This demonstates all the basic functionality of an EventEmitter .

- Subscribe: Subscription is a connection between Subscriber and Publisher. Basically, Publisher will create a subscription for every Subscriber which will try to subscribe to it, and this subscription will handle requests from the subscriber. Publisher act as the storage of data and subscription will obtain data from it. I propose to you to go through [this link](http://www.reactive-streams.org/).

Although, in my opinion, you can start [here](http://reactivex.io/documentation/observable.html). This is a better explanation of reactive data handling.

- Database: A database is a repository of information managed by a database engine which ensures integrity of data and fast access to the data. ... To users, the information in a database can be accessed by using Structured Query Language (SQL) a database language common to most databases.

## WebSocket

WebSocket is a computer communications protocol, providing full-duplex communication channels over a single TCP connection. The WebSocket protocol was standardized by the IETF as RFC 6455 in 2011, and the WebSocket API in Web IDL is being standardized by the W3C.

WebSocket is distinct from HTTP. Both protocols are located at layer 7 in the OSI model and depend on TCP at layer 4. Although they are different, RFC 6455 states that WebSocket "is designed to work over HTTP ports 443 and 80 as well as to support HTTP proxies and intermediaries," thus making it compatible with HTTP. To achieve compatibility, the WebSocket handshake uses the HTTP Upgrade header to change from the HTTP protocol to the WebSocket protocol.

The WebSocket protocol enables interaction between a web browser (or other client application) and a web server with lower overhead than half-duplex alternatives such as HTTP polling, facilitating real-time data transfer from and to the server. This is made possible by providing a standardized way for the server to send content to the client without being first requested by the client, and allowing messages to be passed back and forth while keeping the connection open. In this way, a two-way ongoing conversation can take place between the client and the server. The communications are usually done over TCP port number 443 (or 80 in the case of unsecured connections), which is beneficial for environments that block non-web Internet connections using a firewall. Similar two-way browser-server communications have been achieved in non-standardized ways using stopgap technologies such as Comet.

#### Web server implementation

Nginx has supported WebSockets since 2013, implemented in version 1.3.13 [28] including acting as a reverse proxy and load balancer of WebSocket applications.[29]

Apache HTTP Server has supported WebSockets since July, 2013, implemented in version 2.4.5.

Internet Information Services added support for WebSockets in version 8 which was released with Windows Server 2012.

lighttpd has supported WebSockets since 2017, implemented in version 1.4.46. lighttpd mod_proxy can act as a reverse proxy and load balancer of WebSocket applications. lighttpd mod_wstunnel can facilitate a WebSocket tunnel, allowing a client to employ WebSockets to tunnel a simpler protocol, such as JSON, to a backend application.

## Socket.io vs Web Sockets

### Difference Between WebSocket and Socket.io

WebSocket is the communication Protocol that provides bidirectional communication between the Client and the Server over a TCP connection; WebSocket remains open all the time, so they allow real-time data transfer. When clients trigger the request to the server, it does not close the connection on receiving the response; it rather persists and waits for the Client or server to terminate the request.

Socket.IO is a library that enables real-time and full-duplex communication between the Client and the Web servers. It uses the WebSocket protocol to provide the interface. Generally, it is divided into two parts; both WebSocket vs Socket.io are event-driven libraries.

1. Client-Side: it is the library that runs inside the browser
2. Server Side: It is the library for Node.js

### WebSocket

Below are the features:

Key features of WebSocket:

1. WebSocket helps in real-time communication between the Client and the webserver.

2. This protocol helps in transforming to cross-platform in a real-time world between the server and the client.

3. This also enables the business worldwide for a real-time web application to enhance and increase the feasibility.

4. The major advantage it stands over an HTTP connection that it provides full-duplex communication.

#### References

- OSI Model Explained [Check it out](https://www.youtube.com/watch?v=vv4y_uOneC0)

- TCP Handshakes Explained [Check it out](https://www.youtube.com/watch?v=xMtP5ZB3wSk)

- WebSocket [Read the full article here](https://en.wikipedia.org/wiki/WebSocket)

- Socket.io Tutorial [Check it out](https://www.tutorialspoint.com/socket.io/)

- Socket.io vs Web Sockets [Read the full article here](https://www.educba.com/websocket-vs-socket-io/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
