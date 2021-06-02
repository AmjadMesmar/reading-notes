# Review, Research, and Discussion

1. What’s the difference between a FIFO and a standard queue?
Standard queues guarantee that a message is delivered at least once and duplicates can be introduced into the queue. FIFO queues ensure a message is delivered exactly once and remains available until a consumer processes and deletes it; duplicates are not introduced into the queue.

2. How can the server be assured a message was properly received?
By excpecting to recieve an emitted event, and by using Message Queue.

3. What classic design pattern is best represented by event driven programming?
In computer programming, event-driven programming is a programming paradigm in which the flow of the program is determined by events such as user actions (mouse clicks, key presses), sensor outputs, or message passing from other programs or threads. Event-driven programming is the dominant paradigm used in graphical user interfaces and other applications (e.g., JavaScript web applications) that are centered on performing certain actions in response to user input. This is also true of programming for device drivers (e.g., P in USB device driver stacks).

In an event-driven application, there is generally a main loop that listens for events and then triggers a callback function when one of those events is detected. In embedded systems, the same may be achieved using hardware interrupts instead of a constantly running main loop. Event-driven programs can be written in any programming language, although the task is easier in languages that provide high-level abstractions, such as await and closures.

Virtually all object-oriented and visual languages support event-driven programming. Visual Basic, Visual C++ and Java are examples of such languages. A visual programming IDE such as VB.Net provides much of the code for detecting events automatically when a new application is created.

4. How do you test an event driven system?
We use Unit testing.Unit tests are the most basic tests you will write. The SUT in this case is typically an individual class. Let’s say, the Payment Service needs to apply a sales tax, based on the customer’s location. You would likely have a TaxCalculator class with a calculate() method, that accepts an Order argument and returns a double value representing the tax that needs to be applied to the total. Your unit test will interact with this class directly, passing various Order values to it, and verifying the tax has been calculated properly. At the unit level, the differences between a point-to-point and an event-driven system are insignificant, so we will not go deeper into it.

![Image](https://miro.medium.com/max/700/1*NdiTTk_s6-ignfVB0fBKLw.jpeg)

## Document the following Vocabulary Terms

- FIFO Queue:
FIFO is an abbreviation for first in, first out. It is a method for handling data structures where the first element is processed first and the newest element is processed last.

- Pub/Sub:
In software architecture, publish–subscribe is a messaging pattern where senders of messages, called publishers, do not program the messages to be sent directly to specific receivers, called subscribers, but instead categorize published messages into classes without knowledge of which subscribers, if any, there may be. Similarly, subscribers express interest in one or more classes and only receive messages that are of interest, without knowledge of which publishers, if any, there are.

Publish–subscribe is a sibling of the message queue paradigm, and is typically one part of a larger message-oriented middleware system. Most messaging systems support both the pub/sub and message queue models in their API; e.g., Java Message Service (JMS).

This pattern provides greater network scalability and a more dynamic network topology, with a resulting decreased flexibility to modify the publisher and the structure of the published data.

***Topologies***

In many pub/sub systems, publishers post messages to an intermediary message broker or event bus, and subscribers register subscriptions with that broker, letting the broker perform the filtering. The broker normally performs a store and forward function to route messages from publishers to subscribers. In addition, the broker may prioritize messages in a queue before routing.

Subscribers may register for specific messages at build time, initialization time or runtime. In GUI systems, subscribers can be coded to handle user commands (e.g., click of a button), which corresponds to build time registration. Some frameworks and software products use XML configuration files to register subscribers. These configuration files are read at initialization time. The most sophisticated alternative is when subscribers can be added or removed at runtime. This latter approach is used, for example, in database triggers, mailing lists, and RSS.

The Data Distribution Service (DDS) middleware does not use a broker in the middle. Instead, each publisher and subscriber in the pub/sub system shares meta-data about each other via IP multicast. The publisher and the subscribers cache this information locally and route messages based on the discovery of each other in the shared cognizance. In effect, brokerless architectures require publish/subscribe system to construct an overlay network which allows efficient decentralized routing from publishers to subscribers. It was shown by Jon Kleinberg that efficient decentralised routing requires Navigable Small-World topologies. Such Small-World topologies are usually implemented by decentralized or federated publish/subscribe systems.[1] Locality-aware publish/subscribe systems[2] construct Small-World topologies that route subscriptions through short-distance and low-cost links thereby reducing subscription delivery times.

**References:**

- AWS SNS and SQS[Check it out](https://www.youtube.com/watch?v=mXk0MNjlO7A)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
