# Review, Research, and Discussion

- Does a deployed React application require a server?
  You don't necessarily need a static server in order to run a Create React App project in production. It also works well when integrated into an existing server side app.

- Why do we prefer to test a React application at the behavior rather than the unit level?
  There are a few ways to test React components. Broadly, they divide into two categories:

1. Rendering component trees in a simplified test environment and asserting on their output.
2. Running a complete app in a realistic browser environment (also known as “end-to-end” tests).

- What does npm run build do?
  npm run build ) is also a cli-command predefined to run your custom scripts with the name specified in place of "command-name". So, in this case npm run build is a custom script command with the name "build" and will do anything specified inside it (for instance echo 'hello world' given in below example package. json).

- Describe the actual composition / architecture of a React application
React application is comnposed of a jsx file, html file, a sass file and a yarn file.

## Document the following Vocabulary Terms
  
- BDD: In software engineering, behavior-driven development is an agile software development process that encourages collaboration among developers, quality assurance testers, and customer representatives in a software project.
  
- Acceptance Tests: Acceptance testing is a term used in agile software development methodologies, particularly extreme programming, referring to the functional testing of a user story by the software development team during the implementation phase.
  
- mounting: Mounting is the phase in which our React component mounts on the DOM (i.e., is created and inserted into the DOM). This method is called just before a component mounts on the DOM or the render method is called. After this method, the component gets mounted.
  
- build:
npm run build creates a build directory with a production build of your app. Inside the build/static directory will be your JavaScript and CSS files. Each filename inside of build/static will contain a unique hash of the file contents.

## Understanding React setState

React components can, and often do, have state. State can be anything, but think of things like whether a user is logged in or not and displaying the correct username based on which account is active. Or an array of blog posts. Or if a modal is open or not and which tab within it is active.

React components with state render UI based on that state. When the state of components changes, so does the component UI.

That makes understanding when and how to change the state of your component important. At the end of this tutorial, you should know how setState works, and be able to avoid common pitfalls that many of us hit when when learning React.

### Workings of setState()

setState() is the only legitimate way to update state after the initial state setup. Let’s say we have a search component and want to display the search term a user submits.

Here’s the setup:

        import React, { Component } from 'react'

        class Search extends Component {
        constructor(props) {
            super(props)

            state = {
            searchTerm: ''
            }
        }
        }

We’re passing an empty string as a value and, to update the state of searchTerm, we have to call setState().

        setState({ searchTerm: event.target.value })

Here, we’re passing an object to setState(). The object contains the part of the state we want to update which, in this case, is the value of searchTerm. React takes this value and merges it into the object that needs it. It’s sort of like the Search component asks what it should use for the value of searchTerm and setState() responds with an answer.

![image](https://i1.wp.com/css-tricks.com/wp-content/uploads/2018/04/image_preview-1.jpeg?w=300&ssl=1)

## Handling Events

Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences:

1. React events are named using camelCase, rather than lowercase.
2. With JSX you pass a function as the event handler, rather than a string.

For example, the HTML:

        <button onclick="activateLasers()">
        Activate Lasers
        </button>

is slightly different in React:

        <button onClick={activateLasers}>  Activate Lasers
        </button>

Another difference is that you cannot return false to prevent default behavior in React. You must call preventDefault explicitly. For example, with plain HTML, to prevent the default form behavior of submitting, you can write:

        <form onsubmit="console.log('You clicked submit.'); return false">
        <button type="submit">Submit</button>
        </form>

In React, this could instead be:

        function Form() {
        function handleSubmit(e) {
            e.preventDefault();    console.log('You clicked submit.');
        }

        return (
            <form onSubmit={handleSubmit}>
            <button type="submit">Submit</button>
            </form>
        );
        }

## Forms

HTML form elements work a bit differently from other DOM elements in React, because form elements naturally keep some internal state. For example, this form in plain HTML accepts a single name:

        <form>
        <label>
            Name:
            <input type="text" name="name" />
        </label>
        <input type="submit" value="Submit" />
        </form>

This form has the default HTML form behavior of browsing to a new page when the user submits the form. If you want this behavior in React, it just works. But in most cases, it’s convenient to have a JavaScript function that handles the submission of the form and has access to the data that the user entered into the form. The standard way to achieve this is with a technique called “controlled components”.

### Controlled Components

In HTML, form elements such as ***input***, ***textarea***, and ***select*** typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with setState().

We can combine the two by making the React state be the “single source of truth”. Then the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a “controlled component”.

For example, if we want to make the previous example log the name when it is submitted, we can write the form as a controlled component:

        class NameForm extends React.Component {
        constructor(props) {
            super(props);
            this.state = {value: ''};
            this.handleChange = this.handleChange.bind(this);
            this.handleSubmit = this.handleSubmit.bind(this);
        }

        handleChange(event) {    this.setState({value: event.target.value});  }
        handleSubmit(event) {
            alert('A name was submitted: ' + this.state.value);
            event.preventDefault();
        }

        render() {
            return (
            <form onSubmit={this.handleSubmit}>        <label>
                Name:
                <input type="text" value={this.state.value} onChange={this.handleChange} />        </label>
                <input type="submit" value="Submit" />
            </form>
            );
        }
        }

## State and Lifecycle

Consider the ticking clock example from one of the previous sections. In Rendering Elements, we have only learned one way to update the UI. We call ReactDOM.render() to change the rendered output:

    function tick() {
    const element = (
        <div>
        <h1>Hello, world!</h1>
        <h2>It is {new Date().toLocaleTimeString()}.</h2>
        </div>
    );
    ReactDOM.render(    element,    document.getElementById('root')  );}

    setInterval(tick, 1000);

In this section, we will learn how to make the Clock component truly reusable and encapsulated. It will set up its own timer and update itself every second.

We can start by encapsulating how the clock looks:

        function Clock(props) {
        return (
            <div>      <h1>Hello, world!</h1>      <h2>It is {props.date.toLocaleTimeString()}.</h2>    </div>  );
        }

        function tick() {
        ReactDOM.render(
            <Clock date={new Date()} />,    document.getElementById('root')
        );
        }

        setInterval(tick, 1000);

### Components and Props

Components let you split the UI into independent, reusable pieces, and think about each piece in isolation. This page provides an introduction to the idea of components. You can find a detailed component API reference here.

Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen.
Function and Class Components

The simplest way to define a component is to write a JavaScript function:

        function Welcome(props) {
        return <h1>Hello, {props.name}</h1>;
        }

This function is a valid React component because it accepts a single “props” (which stands for properties) object argument with data and returns a React element. We call such components “function components” because they are literally JavaScript functions.

You can also use an ES6 class to define a component:

        class Welcome extends React.Component {
        render() {
            return <h1>Hello, {this.props.name}</h1>;
        }
        }

The above two components are equivalent from React’s point of view.

Function and Class components both have some additional features that we will discuss in the next sections.

#### References

- setState explained [Read full article](https://css-tricks.com/understanding-react-setstate/)

- handling events [Read full article](https://reactjs.org/docs/handling-events.html)

- forms [Read full article](https://reactjs.org/docs/forms.html)

- state and lifecycle [Read full article](https://reactjs.org/docs/state-and-lifecycle.html)

- components and props [Read full article](https://reactjs.org/docs/components-and-props.html)

- React Testing Library [Read full article](https://testing-library.com/docs/react-testing-library)

- RTL Testing Example[Check it out](https://thomaslombart.com/beginner-guide-testing-react-apps/)

- Roles Reference [Check it out](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques#roles)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
