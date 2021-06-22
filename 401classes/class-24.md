# Review, Research, and Discussion

- Why do we not need more .html pages in a multi-page React app?

React takes advantage of HTML's popularity and strength as the most popular programming language, by letting you use a very similar syntax to HTML to build interfaces and add dynamic features to it using JavaScript.

- If we wanted a component to show up on every page, where would we put it and why?

We put it inside the `<Route>`, Simply because React Router is a standard library for routing in React. It enables the navigation among views of various components in a React Application, allows changing the browser URL, and keeps the UI in sync with the URL.

        Outside the <BrowserRouter/>
        Inside the <BrowserRouter />, outside a <Route />
        Inside a <Route />

- What does props.children contain?
All the elements, values of the component, it's useful if we need to render multiple components dynamically depending on the data needed to be rendeed.

## Document the following Vocabulary Terms

Composition: In React, composition is a natural pattern of the component model. It's how we build components from other components, of varying complexity and specialization through props. Depending on how generalized these components are, they can be used in building many other components.

Children / Child Components: Children allow you to pass components as data to other components, just like any other prop you use. The special thing about children is that React provides support through its ReactElement API and JSX.

Hash Routing: It uses URL hash, it puts no limitations on supported browsers or web server. Server-side routing is independent from client-side routing. Backward-compatible single-page application can use it as example.com/#/react/route.

- For react we use `react-hash-router` ***NPM package*** to use hash routing.

Link Routing:

## Making sense of hooks

[Watch](https://www.youtube.com/watch?v=dpw9EHDh2bM)

### Why Hooks?

We know that components and top-down data flow help us organize a large UI into small, independent, reusable pieces. However, we often can’t break complex components down any further because the logic is stateful and can’t be extracted to a function or another component. Sometimes that’s what people mean when they say React doesn’t let them “separate concerns.”

These cases are very common and include animations, form handling, connecting to external data sources, and many other things we want to do from our components. When we try to solve these use cases with components alone, we usually end up with:

1. Huge components that are hard to refactor and test.
2. Duplicated logic between different components and lifecycle methods.
3. Complex patterns like render props and higher-order components.

Hooks apply the React philosophy (explicit data flow and composition) inside a component, rather than just between the components. That’s why I feel that Hooks are a natural fit for the React component model.

Unlike patterns like render props or higher-order components, Hooks don’t introduce unnecessary nesting into your component tree. They also don’t suffer from the drawbacks of mixins.

Even if you have a visceral first reaction (as I did at first!), I encourage you to give this proposal a fair try and play with it. I think you’ll like it.
Do Hooks Make React Bloated?

Before we look at Hooks in detail, you might be worried that we’re just adding more concepts to React with Hooks. That’s a fair criticism. I think that while there is definitely going to be a short-term cognitive cost to learning them, the end result will be the opposite.

If the React community embraces the Hooks proposal, it will reduce the number of concepts you need to juggle when writing React applications. Hooks let you always use functions instead of having to constantly switch between functions, classes, higher-order components, and render props.

In terms of the implementation size, the Hooks support increases React only by ~1.5kB (min+gzip). While this isn’t much, it’s also likely that adopting Hooks could reduce your bundle size because code using Hooks tends to minify better than equivalent code using classes.

## The state hook

Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.

The introduction page used this example to get familiar with Hooks:

        import React, { useState } from 'react';

        function Example() {
        // Declare a new state variable, which we'll call "count"  const [count, setCount] = useState(0);
        return (
            <div>
            <p>You clicked {count} times</p>
            <button onClick={() => setCount(count + 1)}>
                Click me
            </button>
            </div>
        );
        }

We’ll start learning about Hooks by comparing this code to an equivalent class example.

Equivalent Class Example

If you used classes in React before, this code should look familiar:

        class Example extends React.Component {
        constructor(props) {
            super(props);
            this.state = {
            count: 0
            };
        }

        render() {
            return (
            <div>
                <p>You clicked {this.state.count} times</p>
                <button onClick={() => this.setState({ count: this.state.count + 1 })}>
                Click me
                </button>
            </div>
            );
        }
        }

- The state starts as { count: 0 }, and we increment state.count when the user clicks a button by calling this.setState().

***Note***: You might be wondering why we’re using a counter here instead of a more realistic example. This is to help us focus on the API while we’re still making our first steps with Hooks.

## Hooks api

### State Hook

This example renders a counter. When you click the button, it increments the value:

        import React, { useState } from 'react';
        function Example() {
        // Declare a new state variable, which we'll call "count"  const [count, setCount] = useState(0);
        return (
            <div>
            <p>You clicked {count} times</p>
            <button onClick={() => setCount(count + 1)}>
                Click me
            </button>
            </div>
        );
        }

Here, useState is a Hook (we’ll talk about what this means in a moment). We call it inside a function component to add some local state to it. React will preserve this state between re-renders. useState returns a pair: the current state value and a function that lets you update it. You can call this function from an event handler or somewhere else. It’s similar to this.setState in a class, except it doesn’t merge the old and new state together. (We’ll show an example comparing useState to this.state in Using the State Hook.)

The only argument to useState is the initial state. In the example above, it is 0 because our counter starts from zero. Note that unlike this.state, the state here doesn’t have to be an object — although it can be if you want. The initial state argument is only used during the first render.
Declaring multiple state variables

You can use the State Hook more than once in a single component:

        function ExampleWithManyStates() {
        // Declare multiple state variables!
        const [age, setAge] = useState(42);
        const [fruit, setFruit] = useState('banana');
        const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
        // ...
        }

The array destructuring syntax lets us give different names to the state variables we declared by calling useState. These names aren’t a part of the useState API. Instead, React assumes that if you call useState many times, you do it in the same order during every render.

### But what is a Hook?

Hooks are functions that let you “hook into” React state and lifecycle features from function components. Hooks don’t work inside classes — they let you use React without classes. (We don’t recommend rewriting your existing components overnight but you can start using Hooks in the new ones if you’d like.)

React provides a few built-in Hooks like useState. You can also create your own Hooks to reuse stateful behavior between different components. We’ll look at the built-in Hooks first.

## Effects hook

The Effect Hook lets you perform side effects in function components:

        import React, { useState, useEffect } from 'react';
        function Example() {
        const [count, setCount] = useState(0);

        // Similar to componentDidMount and componentDidUpdate:  useEffect(() => {    // Update the document title using the browser API    document.title = `You clicked ${count} times`;  });
        return (
            <div>
            <p>You clicked {count} times</p>
            <button onClick={() => setCount(count + 1)}>
                Click me
            </button>
            </div>
        );
        }

This snippet is based on the counter example from the previous page, but we added a new feature to it: we set the document title to a custom message including the number of clicks.

Data fetching, setting up a subscription, and manually changing the DOM in React components are all examples of side effects. Whether or not you’re used to calling these operations “side effects” (or just “effects”), you’ve likely performed them in your components before.

***Tip***: If you’re familiar with React class lifecycle methods, you can think of useEffect Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined.

There are two common kinds of side effects in React components: those that don’t require cleanup, and those that do. Let’s look at this distinction in more detail.
Effects Without Cleanup

Sometimes, we want to run some additional code after React has updated the DOM. Network requests, manual DOM mutations, and logging are common examples of effects that don’t require a cleanup. We say that because we can run them and immediately forget about them. Let’s compare how classes and Hooks let us express such side effects.

**References:**

- making sense of hooks [Read full article](https://medium.com/@dan_abramov/making-sense-of-react-hooks-fdbde8803889)

- the state hook [Read full article](https://reactjs.org/docs/hooks-state.html)

- effects hook [Read full article](https://reactjs.org/docs/hooks-effect.html)

- hooks api [Read full article](https://reactjs.org/docs/hooks-overview.html)

- hooks api reference [Check it out](https://reactjs.org/docs/hooks-reference.html)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
