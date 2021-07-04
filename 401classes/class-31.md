# Review, Research, and Discussion

- How granular should your reducers be?

In order to tell whether actions A and B are really one or two actions, you need to ask yourself: “If I change how some reducers react to A, will I also need to change how they react to B?”

When the handlers change together in the reducer code, it’s likely they should be a single action. When their changes may not affect each other, or if many reducers handle just one of them but not the other, they should probably stay separate.

- Pro or Con – multiple reducers can “fire” when a commonly named action is dispatched

Dispatching an action within a reducer is an anti-pattern. Your reducer should be without side effects, simply digesting the action payload and returning a new state object. Adding listeners and dispatching actions within the reducer can lead to chained actions and other side effects.

- Name a strategy for preventing the above

There are two very popular middleware libraries that allow for side effects and asynchronous actions: `Redux Thunk` and `Redux Saga`. In this post, you will explore `Redux Thunk`.

## Document the following Vocabulary Terms

- Store: A store is an immutable object tree in Redux. A store is a state container which holds the application's state. Redux can have only a single store in your application. Whenever a store is created in Redux, you need to specify the reducer.

- Combined reducers: The most common state shape for a Redux app is a plain Javascript object containing "slices" of domain-specific data at each top-level key. ... First and foremost, combineReducers is simply a utility function to simplify the most common use case when writing Redux reducers.

## async actions

### Introduction

In Part 5: UI and React, we saw how to use the React-Redux library to let our React components interact with a Redux store, including calling useSelector to read Redux state, calling useDispatch to give us access to the dispatch function, and wrapping our app in a `<Provider>` component to give those hooks access to the store.

So far, all the data we've worked with has been directly inside of our React+Redux client application. However, most real applications need to work with data from a server, by making HTTP API calls to fetch and save items.

In this section, we'll update our todo app to fetch the todos from an API, and add new todos by saving them to the API.
Example REST API and Client#

To keep the example project isolated but realistic, the initial project setup already included a fake in-memory REST API for our data (configured using the Mirage.js mock API tool). The API uses /fakeApi as the base URL for the endpoints, and supports the typical GET/POST/PUT/DELETE HTTP methods for /fakeApi/todos. It's defined in src/api/server.js.

The project also includes a small HTTP API client object that exposes client.get() and client.post() methods, similar to popular HTTP libraries like axios. It's defined in src/api/client.js.

We'll use the client object to make HTTP calls to our in-memory fake REST API for this section.
Redux Middleware and Side Effects#

By itself, a Redux store doesn't know anything about async logic. It only knows how to synchronously dispatch actions, update the state by calling the root reducer function, and notify the UI that something has changed. Any asynchronicity has to happen outside the store.

Earlier, we said that Redux reducers must never contain "side effects". A "side effect" is any change to state or behavior that can be seen outside of returning a value from a function. Some common kinds of side effects are things like:

1. Logging a value to the console
2. Saving a file
3. Setting an async timer
4. Making an AJAX HTTP request
5. Modifying some state that exists outside of a function, or mutating arguments to a function
6. Generating random numbers or unique random IDs (such as Math.random() or Date.now())

### Using Middleware to Enable Async Logic

Let's look at a couple examples of how middleware can enable us to write some kind of async logic that interacts with the Redux store.

One possibility is writing a middleware that looks for specific action types, and runs async logic when it sees those actions, like these examples:

        import { client } from '../api/client'

        const delayedActionMiddleware = storeAPI => next => action => {
        if (action.type === 'todos/todoAdded') {
            setTimeout(() => {
            // Delay this action by one second
            next(action)
            }, 1000)
            return
        }

        return next(action)
        }

        const fetchTodosMiddleware = storeAPI => next => action => {
        if (action.type === 'todos/fetchTodos') {
            // Make an API call to fetch todos from the server
            client.get('todos').then(todos => {
            // Dispatch an action with the todos we received
            storeAPI.dispatch({ type: 'todos/todosLoaded', payload: todos })
            })
        }

        return next(action)
        }

## redux thunk

### Redux thunk Introduction

By default, Redux’s actions are dispatched synchronously, which is a problem for any non-trivial app that needs to communicate with an external API or perform side effects. Redux also allows for middleware that sits between an action being dispatched and the action reaching the reducers.

There are two very popular middleware libraries that allow for side effects and asynchronous actions: Redux Thunk and Redux Saga. In this post, you will explore Redux Thunk.

Thunk is a programming concept where a function is used to delay the evaluation/calculation of an operation.

Redux Thunk is a middleware that lets you call action creators that return a function instead of an action object. That function receives the store’s dispatch method, which is then used to dispatch regular synchronous actions inside the function’s body once the asynchronous operations have been completed.

In this article, you will learn how to add Redux Thunk and how it can fit in a hypothetical Todo application.

### Prerequisites

This post assumes you have some basic knowledge of React and Redux. You can refer to this post if you’re getting started with Redux.

This tutorial builds off of a hypothetical Todo application that tracks tasks that need to be accomplished and have been completed. We can presume that create-react-app was used to generate a new React application, and redux, react-redux, and axios have already been installed.

The finer details on how to build a Todo application from scratch are not explained here. It is presented as a conceptual setting for highlighting Redux Thunk.

### Adding redux-thunk

First, use the terminal to navigate to the project directory and install the redux-thunk package in your project:

        npm install redux-thunk@2.3.0

Note: Redux Thunk is only 14 lines of code. Check out the source here to learn about how a Redux middleware works under the hood.

Now apply the middleware when creating your app’s store using Redux’s applyMiddleware. Given a React application with redux and react-redux, your index.js file might look like this:
src/index.js

        import React from 'react';
        import ReactDOM from 'react-dom';
        import { Provider } from 'react-redux';
        import { createStore, applyMiddleware } from 'redux';
        import thunk from 'redux-thunk';
        import './index.css';
        import rootReducer from './reducers';
        import App from './App';
        import * as serviceWorker from './serviceWorker';

        // use applyMiddleware to add the thunk middleware to the store
        const store = createStore(rootReducer, applyMiddleware(thunk));

        ReactDOM.render(
        <Provider store={store}>
            <App />
        </Provider>,
        document.getElementById('root')
        );

Now, Redux Thunk is imported and applied in your application.

#### References

- async actions  [Read full article](https://redux.js.org/tutorials/fundamentals/part-6-async-logic)

- redux thunk [Read full article](https://www.digitalocean.com/community/tutorials/redux-redux-thunk)

- thunk middleware [Check it out](https://github.com/reduxjs/redux-thunk)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
