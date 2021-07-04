# Review, Research, and Discussion

- What’s the best practice for “pre-loading” data into the store (on application start) in a Redux application?

The most 'redux-like' way of handling the pre-loading of data would be to fire off the asynchronous action in the lifecycle method (probably componentWillMount) of a Higher Order Component that wraps your app. However, you will not use the results of the API call directly in that component - it needs to be handled with a reducer that puts it into your app store. This will require you to use some sort of a thunk middleware to handle the asynchronous action. Then you will use mapStateToProps to simply pass it down to the component that renders the data.

- When using a thunk/async action that dispatches the actual action, which do you export from your reducer?

Redux Thunk is a middleware that lets you call action creators that return a function instead of an action object. That function receives the store's dispatch method, which is then used to dispatch regular synchronous actions inside the function's body once the asynchronous operations have been completed.

## Document the following Vocabulary Terms

- Middleware: Image result for redux middleware definition
Redux middleware provides a third-party extension point between dispatching an action, and the moment it reaches the reducer. People use Redux middleware for logging, crash reporting, talking to an asynchronous API, routing, and more.

- Thunk:Redux Thunk is middleware that allows you to return functions, rather than just actions, within Redux. This allows for delayed actions, including working with promises. One of the main use cases for this middleware is for handling actions that might not be synchronous, for example, using axios to send a GET request.

## Redux Toolkit Tutorial

### Redux Toolkit Quick Starts

The Redux Toolkit Quick Start tutorial briefly shows how to add and use Redux Toolkit in a React application.

If you just want the fastest way to get a basic example running, read the Quick Start tutorial.

We also have a TypeScript Quick Start tutorial that briefly shows how to set up and use TypeScript with Redux Toolkit and React-Redux.

### Redux Essentials: A Real-World Example

The Redux Essentials tutorial teaches you "how to use Redux the right way", using Redux Toolkit as the standard approach for writing Redux logic.

It shows how to build a "real world"-style example application, and teaches Redux concepts along the way.

If you've never used Redux before, and just want to know "how do I use this to build something useful?", start with the Redux Essentials tutorial.

### Redux Fundamentals: Redux from the Ground Up

The Redux Fundamentals tutorial teaches "how Redux works, from the bottom up", by showing how to write Redux code by hand and why standard usage patterns exist. It then shows how Redux Toolkit simplifies those Redux usage patterns.

Since Redux Toolkit is an abstraction layer that wraps around the Redux core, it's helpful to know what RTK's APIs are actually doing for you under the hood. If you want to understand how Redux really works and why RTK is the recommended approach, read the Redux Fundamentals tutorial.

## MobX

 MobX is a simple, scalable and battle tested state management solution. This tutorial will teach you all the important concepts of MobX in ten minutes. MobX is a standalone library, but most people are using it with React and this tutorial focuses on that combination.

### The core idea

State is the heart of each application and there is no quicker way to create buggy, unmanageable applications than by producing an inconsistent state or state that is out-of-sync with local variables that linger around. Hence many state management solutions try to restrict the ways in which you can modify state, for example by making state immutable. But this introduces new problems; data needs to be normalized, referential integrity can no longer be guaranteed and it becomes next to impossible to use powerful concepts like classes in case you fancy those.

MobX makes state management simple again by addressing the root issue: it makes it impossible to produce an inconsistent state. The strategy to achieve that is simple: Make sure that everything that can be derived from the application state, will be derived. Automatically.

Conceptually MobX treats your application like a spreadsheet.

![Image](https://mobx.js.org/assets/getting-started-assets/overview.png)

1. First of all, there is the application state. Graphs of objects, arrays, primitives, references that forms the model of your application. These values are the “data cells” of your application.

2. Secondly there are derivations. Basically, any value that can be computed automatically from the state of your application. These derivations, or computed values, can range from simple values, like the number of unfinished todos, to complex stuff like a visual HTML representation of your todos. In spreadsheet terms: these are the formulas and charts of your application.

3. Reactions are very similar to derivations. The main difference is these functions don't produce a value. Instead, they run automatically to perform some task. Usually this is I/O related. They make sure that the DOM is updated or that network requests are made automatically at the right time.

4. Finally there are actions. Actions are all the things that alter the state. MobX will make sure that all changes to the application state caused by your actions are automatically processed by all derivations and reactions. Synchronously and glitch-free.

#### References

- Redux Toolkit Tutorial [Read full article](https://redux-toolkit.js.org/tutorials/overview)

- MobX [Read full article](https://mobx.js.org/getting-started.html)

- HookState [Check it out](https://hookstate.js.org/)

- Redux Toolkit (RTK) [Check it out](https://redux-toolkit.js.org/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
