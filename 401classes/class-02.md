# Review, Research, and Discussion

### Name 3 real world use cases where you’d want to change the request with custom middleware:

1. Validation.
2. Logging.
3. Error handling.

### True or false: The route handler is middleware?

- True.

### In what ways can a middleware function end the process and send data to the browser?

It can end with the response variable such as "response.send()".

### At what point in the request lifecycle can you “inject” middleware?

- Any time of the request life cycle

### What can cause express to error with “Request headers sent twice, cannot start a second response”

- When you’re  in the finished state, but some function tried to set a statusCode.

- Middleware: Middleware is software that bridges gaps between other applications, tools, and databases in order to provide unified services to users. It is commonly characterized as the glue that connects different software platforms and devices together.

- Request Object: The Request object retrieves the values that the client browser passed to the server during an HTTP request.

- Response Object: The Response object, which contains a server's response to an HTTP request. Every HTTP request sent returns a response from the server (the Response object) which includes quite a bit of information.

- Application Middleware: Middleware is software that provides common services and capabilities to applications outside of what's offered by the operating system. Data management, application services, messaging, authentication, and API management are all commonly handled by middleware.

- Routing Middleware: The term is composed of 2 words router and middleware. Middleware. It is a piece of code that comes in the middle of request and response . It kind of hijacks your request so that you can do anything that you want with your request or response eg: Modify the data or call the next middleware.

- Test Driven Development: Test-driven development is a process of modifying the code in order to pass a test designed previously. In Software Engineering, It is sometimes known as "Test First Development." TDD includes refactoring a code i.e. changing/adding some amount of code to the existing code without affecting the behavior of the code.

- Behavioral Testing: BLACK BOX TESTING, also known as Behavioral Testing, is a software testing method in which the internal structure/design/implementation of the item being tested is not known to the tester. These tests can be functional or non-functional, though usually functional.

**References:**

## [Main page](https://amjadmesmar.github.io/reading-notes/)
