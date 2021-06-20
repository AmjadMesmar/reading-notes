# Review, Research, and Discussion

- Name 5 Javascript UI Frameworks (other than React).

1. Ext JS by Sencha.

2. Angular.

3. Vue.

4. Ember.

5. Svelte 3.

- What’s the difference between a framework and a library?

The major difference between frameworks and libraries is complexity. Libraries offer fewer complexities, and frameworks are the opposite. A library is a collection of packages that performs specific operations. On the other hand, frameworks contain the basic flow and architecture of the application.

## Document the following Vocabulary Terms

- Rendering: Rendering or image synthesis is the process of generating a photorealistic or non-photorealistic image from a 2D or 3D model by means of a computer program. The resulting image is referred to as the render.

- Templates: A template is a pre-created document that already has some formatting. Rather than starting from scratch to format a document, you can use the formatting of a template to save yourself a lot of time. You can use a template that comes with Word, download one from the internet, or create your own.

- State:

1. In object-oriented programming, the state of an object is the combination of the original values in the object plus any modifications made to them.

2. The current or last-known status, or condition, of a process, transaction or setting. "Maintaining state" or "managing state" means keeping track of the process. This is an issue on the Web, because the HTTP protocol does not maintain state between one page request and the next. A website needs to keep track of customers that fill a shopping cart with an item, wander off to another page and then come back to complete the order. Likewise, Webmasters like to analyze the routes users take when visiting their sites. In order to maintain state in a stateless environment, cookie files and server protocols such as NSAPI and ISAPI are used.

## Introducing JSX

Consider this variable declaration:

        const element = <h1>Hello, world!</h1>;

This funny tag syntax is neither a string nor HTML.

It is called JSX, and it is a syntax extension to JavaScript. We recommend using it with React to describe what the UI should look like. JSX may remind you of a template language, but it comes with the full power of JavaScript.

JSX produces React “elements”. We will explore rendering them to the DOM in the next section. Below, you can find the basics of JSX necessary to get you started.

### Why JSX?

React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.

Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both. We will come back to components in a further section, but if you’re not yet comfortable putting markup in JS, this talk might convince you otherwise.

React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.

### Embedding Expressions in JSX

In the example below, we declare a variable called name and then use it inside JSX by wrapping it in curly braces:

        const name = 'Josh Perez';const element = <h1>Hello, {name}</h1>;
        ReactDOM.render(
        element,
        document.getElementById('root')
        );

You can put any valid JavaScript expression inside the curly braces in JSX. For example, 2 + 2, user.firstName, or formatName(user) are all valid JavaScript expressions.

In the example below, we embed the result of calling a JavaScript function, formatName(user), into an ***h1*** element.

        function formatName(user) {
        return user.firstName + ' ' + user.lastName;
        }

        const user = {
        firstName: 'Harper',
        lastName: 'Perez'
        };

        const element = (
        <h1>
            Hello, {formatName(user)}!  </h1>
        );

        ReactDOM.render(
        element,
        document.getElementById('root')
        );

## Rendering Elements

An element describes what you want to see on the screen:

        const element = <h1>Hello, world</h1>;

Unlike browser DOM elements, React elements are plain objects, and are cheap to create. React DOM takes care of updating the DOM to match the React elements.

Rendering an Element into the DOM

Let’s say there is a ***div*** somewhere in your HTML file:

        <div id="root"></div>

We call this a “root” DOM node because everything inside it will be managed by React DOM.

Applications built with just React usually have a single root DOM node. If you are integrating React into an existing app, you may have as many isolated root DOM nodes as you like.

To render a React element into a root DOM node, pass both to ReactDOM.render():

        const element = <h1>Hello, world</h1>;
        ReactDOM.render(element, document.getElementById('root'));

### Updating the Rendered Element

React elements are immutable. Once you create an element, you can’t change its children or attributes. An element is like a single frame in a movie: it represents the UI at a certain point in time.

With our knowledge so far, the only way to update the UI is to create a new element, and pass it to ***ReactDOM.render()***.

Consider this ticking clock example:

        function tick() {
        const element = (
            <div>
            <h1>Hello, world!</h1>
            <h2>It is {new Date().toLocaleTimeString()}.</h2>
            </div>
        );
        ReactDOM.render(element, document.getElementById('root'));}

        setInterval(tick, 1000);

**References:**

- react hello world [Read full article](https://reactjs.org/docs/hello-world.html)

- introducing JSX [Read full article](https://medium.com/awesome-cloud/aws-difference-between-sqs-and-sns-61a397bf76c5)

-rendering elements [Read full article](https://reactjs.org/docs/rendering-elements.html)

- sass cheatsheet [Check it out](https://devhints.io/sass)

- react cheatsheet [Check it out](https://devhints.io/react)

- another react cheatsheet [Check it out](https://reactcheatsheet.com/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
