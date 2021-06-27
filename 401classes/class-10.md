
# Review, Research, and Discussion

1. Why is access control important?
Access controls limit access to information and information processing systems. When implemented effectively, they mitigate the risk of information being accessed without the appropriate authorisation, unlawfully and the risk of a data breach.

2. Describe an application that would need access control.
For example, Security Enhanced Linux (SELinux) is an implementation of MAC on the Linux OS. Discretionary access control (DAC). This is an access control method in which owners or administrators of the protected system, data or resource set the policies defining who or what is authorized to access the resource.

3. What is a role used for?
An organization assigns a role-based access control role to every employee; the role determines which permissions the system grants to the user. For example, you can designate whether a user is an administrator, a specialist, or an end-user, and limit access to specific resources or tasks.

4. Why is role based access control more scalable than discretionary or mandatory access control?
With hundreds or thousands of employees, security is more easily maintained by limiting unnecessary access to sensitive information based on each user's established role within the organization. Other advantages include: Reducing administrative work and IT support.

## Document the following Vocabulary Terms

1. Authorization: Authorization in system security is the process of giving the user permission to access a specific resource or function. This term is often used interchangeably with access control or client privilege.

2. Role Based Access Control: In computer systems security, role-based access control or role-based security is an approach to restricting system access to authorized users. It is used by the majority of enterprises with more than 500 employees, and can implement mandatory access control or discretionary access control.

3. Capabilities: Capabilities are used to control access to system resources. In modern programming languages that execute code with different levels of trust in the same process, the propagation of such capabilities must be controlled so that they cannot unintentionally be obtained by unauthorised code.

## Event Driven Programming

Event-Driven Programming is a logical pattern that we can choose to confine our programming within to avoid issues of complexity and collision. In this article we’re going to go over how Event-Driven Programming works and how we can make the best use of it in our Node.js projects.

Most developers are introduced to concepts of Event-Driven Programming early on in their study of programming yet they might not fully realize it until a bit later. You’ll find that the concept is rather ubiquitous. Check any major framework or software out there and odds are you’ll find evidence of Event-Driven Programming.

### Overview

For the most recognizable example of Event-Driven Programming for people at any level of programming skill, we’ll turn to our old friend The Web Browser.

Every time you interact with a webpage through it’s user interface, an event is happening. When you click a button a click event is triggered. When you press a key a keydown event is triggered. These events have associated functions that, when triggered, are executed to make a change to the user interface in some way.

### EventEmitter

Node.js natively provides us with a useful module called EventEmitter that allows us to get started incorporating Event-Driven Programming in our project right away. Of course, creating our own version of EventEmitter wouldn’t be much of a challange, and in fact there are several modules published on npm such as EventEmitter2 and EventEmitter3 which promise a faster performance than the native EventEmitter.

Those are both worth checking out if your project needs to run faster than EventEmitter will allow. They are both built to allow for syntax that is almost identical to what we’ll use for EventEmitter so learning one will make it easy to work with all of them.

We access the EventEmitter class through the events module. Once imported we’ll need to create a new object from the class to start using it.

        const EventEmitter = require('events').EventEmitter;
        const myEventEmitter = new EventEmitter;

Now we can get started with Event-Driven Programming in Node.

Imagine we’re creating a chat room. We want to alert everyone when a new user joins the chat room. We’ll need an event listener for a userJoined event. First, we’ll write a function that will act as our event listener, then we can use EventEmitters on method to set the listener.

        const EventEmitter = require('events').EventEmitter;
        const chatRoomEvents = new EventEmitter;

        function userJoined(username){
        // Assuming we already have a function to alert all users.
        alertAllUsers('User ' + username + ' has joined the chat.');
        }

        // Run the userJoined function when a 'userJoined' event is triggered.
        chatRoomEvents.on('userJoined', userJoined);

The next step would be to make sure that our chat room triggers a userJoined event whenever someone logs in so that our event handler is called. EventEmitter has an emit method that we we use to trigger the event. We would want to trigger this event from within a login function inside of our chatroom module.

        function login(username){
        chatRoomEvents.emit('userJoined', username);
        }

We could expand further by creating events for when a user logs out, when a message is sent, when a message is received, or any other event we could possibly need for our chat room to be as dynamic as we want it.

***Event-Driven Programming makes use of the following concepts:***

- An Event Handler is a callback function that will be called when an event is triggered.
- A Main Loop listens for event triggers and calls the associated event handler for that event.

#### References

- Event Driven Programming [Read the full article here](https://www.digitalocean.com/community/tutorials/nodejs-event-driven-programming)

- Node docs: events [Check it out](https://nodejs.org/api/events.html)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
