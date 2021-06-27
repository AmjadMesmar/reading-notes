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

## Socket.io

### Socket.io Chat Example

#### The web framework

The first goal is to set up a simple HTML webpage that serves out a form and a list of messages. We’re going to use the Node.JS web framework express to this end. Make sure Node.JS is installed.

First let’s create a package.json manifest file that describes our project. I recommend you place it in a dedicated empty directory (I’ll call mine chat-example).

    {
      "name": "socket-chat-example",
      "version": "0.0.1",
      "description": "my first socket.io app",
      "dependencies": {}
    }

Now, in order to easily populate the dependencies property with the things we need, we’ll use npm install:

    npm install express@4

Once it’s installed we can create an index.js file that will set up our application.

    const express = require('express');
    const app = express();
    const http = require('http');
    const server = http.createServer(app);

    app.get('/', (req, res) => {
      res.send('<h1>Hello world</h1>');
    });

    server.listen(3000, () => {
      console.log('listening on *:3000');
    });

#### Integrating Socket.IO

Socket.IO is composed of two parts:

1. A server that integrates with (or mounts on) the Node.JS HTTP Server socket.io
2. A client library that loads on the browser side socket.io-client

During development, socket.io serves the client automatically for us, as we’ll see, so for now we only have to install one module:

    npm install socket.io

That will install the module and add the dependency to package.json. Now let’s edit index.js to add it:

    const express = require('express');
    const app = express();
    const http = require('http');
    const server = http.createServer(app);
    const { Server } = require("socket.io");
    const io = new Server(server);

    app.get('/', (req, res) => {
      res.sendFile(__dirname + '/index.html');
    });

    io.on('connection', (socket) => {
      console.log('a user connected');
    });

    server.listen(3000, () => {
      console.log('listening on *:3000');
    });

Notice that I initialize a new instance of socket.io by passing the server (the HTTP server) object. Then I listen on the connection event for incoming sockets and log it to the console.

Now in index.html add the following snippet before the </body> (end body tag):

    <script src="/socket.io/socket.io.js"></script>
    <script>
      var socket = io();
    </script>

That’s all it takes to load the socket.io-client, which exposes an io global (and the endpoint GET /socket.io/socket.io.js), and then connect.

If you would like to use the local version of the client-side JS file, you can find it at node_modules/socket.io/client-dist/socket.io.js.

Notice that I’m not specifying any URL when I call io(), since it defaults to trying to connect to the host that serves the page.

If you now restart the process (by hitting Control+C and running node index.js again) and then refresh the webpage you should see the console print “a user connected”.

## Socket.io Rooms and Namespaces

### Rooms

A room is an arbitrary channel that sockets can join and leave. It can be used to broadcast events to a subset of clients:

![Image](https://socket.io/images/rooms.png)

Please note that rooms are a server-only concept (i.e. the client does not have access to the list of rooms it has joined).
Joining and leaving

You can call join to subscribe the socket to a given channel:

      io.on('connection', socket => {
        socket.join('some room');
      });

And then simply use to or in (they are the same) when broadcasting or emitting:

      io.to('some room').emit('some event');

You can emit to several rooms at the same time:

      io.to('room1').to('room2').to('room3').emit('some event');

In that case, a union is performed: every socket that is at least in one of the rooms will get the event once (even if the socket is in two or more rooms).

You can also broadcast to a room from a given socket:

      io.on('connection', function(socket){
        socket.to('some room').emit('some event');
      });

In that case, every socket in the room excluding the sender will get the event.

![Image](https://socket.io/images/rooms2.png)

#### Disconnection

Upon disconnection, sockets leave all the channels they were part of automatically, and no special teardown is needed on your part.

You can fetch the rooms the Socket was in by listening to the disconnecting event:

    io.on('connection', socket => {
      socket.on('disconnecting', () => {
        console.log(socket.rooms); // the Set contains at least the socket ID
      });

      socket.on('disconnect', () => {
        // socket.rooms.size === 0
      });
    });

#### Room events

Starting with socket.io@3.1.0, the underlying Adapter will emit the following events:

      create-room (argument: room)
      delete-room (argument: room)
      join-room (argument: room, id)
      leave-room (argument: room, id)

Example:

      io.of("/").adapter.on("create-room", (room) => {
        console.log(`room ${room} was created`);
      });

      io.of("/").adapter.on("join-room", (room, id) => {
        console.log(`socket ${id} has joined room ${room}`);
      });

#### References

- Socket.io Chat Example [Check it out](https://socket.io/get-started/chat/)

- Rooms and Namespaces [Check it out](https://socket.io/docs/v3/rooms/index.html)

- Socket.io Emit Cheatsheet [Check it out](https://socket.io/docs/v3/emit-cheatsheet/index.html)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
