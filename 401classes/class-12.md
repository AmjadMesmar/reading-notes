# Review, Research, and Discussion

1. What does it mean that web sockets are bidirectional? Why is this useful?

Whereas HTTP relies on a client request to receive a response from the server for every exchange, WebSockets allow for full-duplex bidirectional communication. This enables the server to send real-time updates asynchronously, without requiring the client to submit a request each time.

2. Does socket.io use HTTP? Why?

The premise on which your question seems to be based is that socket.io is a websocket library, which it isn't. ... Even when websockets can be used, the initial connection setup it done over HTTP. Also, a socket.io server will attach to an HTTP server so it can serve its own client code through /socket.io/socket.io.js .

3. What happens when a client emits an event?

The event gets passed to the server through websockets. Its a tcp connection from the browser to the server. The connection is full duplex meaning the server can send real time data to the client and vise versa.
In your frontend code you should have something that looks similar to

        <script src="/socket.io/socket.io.js"></script>
        script>
          var socket = io();
        </script>

This code asks the server for a tcp connection using web sockets. Once the browser is connected to the server through websockets, socket.io can send events to the send through the connection.
The socket that is passed in the connection event is just a reference to whatever socket gets created when the frontend connects. The socket gets a unique id and with this reference you can communicate in real time to the web browser client.

4. What happens when a server emits an event?
All listening clients will execute the handler for that event.

5. What happens if a client “misses” an event?
The event handler wont run,

6. How can we mitigate this?
Message Queue is the solution.

## Document the following Vocabulary Terms

- Socket:
Socket types define the communication properties visible to a user. The Internet family sockets provide access to the TCP/IP transport protocols. Datagram sockets allow processes to use UDP to communicate. ... A datagram socket supports bidirectional flow of messages.

- Web Socket:
The WebSocket API is an advanced technology that makes it possible to open a two-way interactive communication session between the user's browser and a server. With this API, you can send messages to a server and receive event-driven responses without having to poll the server for a reply.

- Socket.io:
Socket.IO enables real-time bidirectional event-based communication. It works on every platform, browser or device, focusing equally on reliability and speed. Socket.IO is built on top of the WebSockets API (Client side) and Node.

- Client:
A client is a computer or a program that, as part of its operation, relies on sending a request to another program or a computer hardware or software that accesses a service made available by a server (which may or may not be located on another computer)

- Server:
A server is a computer program or device that provides a service to another computer program and its user, also known as the client. In a data center, the physical computer that a server program runs on is also frequently referred to as a server.

- OSI Model:
The OSI Model (Open Systems Interconnection Model) is a conceptual framework used to describe the functions of a networking system. The OSI model characterizes computing functions into a universal set of rules and requirements in order to support interoperability between different products and software.

- TCP Model:
The Internet protocol suite is the conceptual model and set of communications protocols used in the Internet and similar computer networks. It is commonly known as TCP/IP because the foundational protocols in the suite are the Transmission Control Protocol and the Internet Protocol.

- TCP:
The Transmission Control Protocol is one of the main protocols of the Internet protocol suite. It originated in the initial network implementation in which it complemented the Internet Protocol. Therefore, the entire suite is commonly referred to as TCP/IP.

- UDP:
In computer networking, the User Datagram Protocol is one of the core members of the Internet protocol suite. With UDP, computer applications can send messages, in this case referred to as datagrams, to other hosts on an Internet Protocol network.

- Packets:
In telecommunications and computer networking, a network packet is a formatted unit of data carried by a packet-switched network. A packet consists of control information and user data; the latter is also known as the payload. Control information provides data for delivering the payload.

**References:**

- Socket.io Chat Example [Check it out](https://socket.io/get-started/chat/)

- Rooms and Namespaces [Check it out](https://socket.io/docs/v3/rooms/index.html)

- Socket.io Emit Cheatsheet [Check it out](https://socket.io/docs/v3/emit-cheatsheet/index.html)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
