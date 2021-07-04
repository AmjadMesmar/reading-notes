# Review, Research, and Discussion

- Why choose Redux instead of the Context API for global state?

Context API prompts a re-render on each update of the state and re-renders all components regardless. Redux however, only re-renders the updated components. This can be monitored on the console as there's a log in each component.

- What is the purpose of a reducer?

A reducer is a function that determines changes to an application's state. It uses the action it receives to determine this change. We have tools, like Redux, that help manage an application's state changes in a single store so that they behave consistently.

- What does an action contain?

Actions are the only source of information for the store as per Redux official documentation. It carries a payload of information from your application to store. const ITEMS_REQUEST = 'ITEMS_REQUEST'; Apart from this type attribute, the structure of an action object is totally up to the developer.

- Why do we need to copy the state in a reducer?

In the documentation of reducers(read it again for details!), redux only requires our reducers to stay pure. If the new state is different, the reducer must create new object, and making a copy is a way to describe the unchanged part.

## Document the following Vocabulary Terms

- Immutable state:
In object-oriented and functional programming, an immutable object (unchangeable object) is an object whose state cannot be modified after it is created. This is in contrast to a mutable object (changeable object), which can be modified after it is created.

- Time travel in redux:
The Redux DevTools records dispatched actions and the state of the Redux store at every point in time. ... This makes it possible to inspect the state and travel back in time to a previous application state without reloading the page or restarting the app.

- Action creator:
An action creator is merely a function that returns an action object. Redux includes a utility function called bindActionCreators for binding one or more action creators to the store's dispatch() function.

- Reducer:
In Redux, a reducer is a pure function that takes an action and the previous state of the application and returns the new state. The action describes what happened and it is the reducer's job to return the new state based on that action.

- Dispatch:
dispatch is a function of the Redux store. You call store. dispatch to dispatch an action. This is the only way to trigger a state change. With React Redux, your components never access the store directly - connect does it for you.

## Redux Docs: Using Combined Reducers

### Core Concepts

The most common state shape for a Redux app is a plain Javascript object containing "slices" of domain-specific data at each top-level key. Similarly, the most common approach to writing reducer logic for that state shape is to have "slice reducer" functions, each with the same (state, action) signature, and each responsible for managing all updates to that specific slice of state. Multiple slice reducers can respond to the same action, independently update their own slice as needed, and the updated slices are combined into the new state object.

Because this pattern is so common, Redux provides the combineReducers utility to implement that behavior. It is an example of a higher-order reducer, which takes an object full of slice reducer functions, and returns a new reducer function.

There are several important ideas to be aware of when using combineReducers:

1. First and foremost, combineReducers is simply a utility function to simplify the most common use case when writing Redux reducers. You are not required to use it in your own application, and it does not handle every possible scenario. It is entirely possible to write reducer logic without using it, and it is quite common to need to write custom reducer logic for cases that combineReducer does not handle. (See Beyond combineReducers for examples and suggestions.)

2. While Redux itself is not opinionated about how your state is organized, combineReducers enforces several rules to help users avoid common errors. (See combineReducers for details.)

3. One frequently asked question is whether Redux "calls all reducers" when dispatching an action. Since there really is only one root reducer function, the default answer is "no, it does not". However, combineReducers has specific behavior that does work that way. In order to assemble the new state tree, combineReducers will call each slice reducer with its current slice of state and the current action, giving the slice reducer a chance to respond and update its slice of state if needed. So, in that sense, using combineReducers does "call all reducers", or at least all of the slice reducers it is wrapping.

4. You can use it at all levels of your reducer structure, not just to create the root reducer. It's very common to have multiple combined reducers in various places, which are composed together to create the root reducer.

### Defining State Shape

There are two ways to define the initial shape and contents of your store's state. First, the `createStore` function can take preloadedState as its second argument. This is primarily intended for initializing the store with state that was previously persisted elsewhere, such as the browser's localStorage. The other way is for the root reducer to return the initial state value when the state argument is undefined. These two approaches are described in more detail in Initializing State, but there are some additional concerns to be aware of when using `combineReducers`.

`combineReducers` takes an object full of slice reducer functions, and creates a function that outputs a corresponding state object with the same keys. This means that if no preloaded state is provided to `createStore`, the naming of the keys in the input slice reducer object will define the naming of the keys in the output state object. The correlation between these names is not always apparent, especially when using ES6 features such as default module exports and object literal shorthands.

Here's an example of how use of ES6 object literal shorthand with `combineReducers` can define the state shape:

        // reducers.js
        export default theDefaultReducer = (state = 0, action) => state

        export const firstNamedReducer = (state = 1, action) => state

        export const secondNamedReducer = (state = 2, action) => state

        // rootReducer.js
        import { combineReducers, createStore } from 'redux'

        import theDefaultReducer, {
        firstNamedReducer,
        secondNamedReducer
        } from './reducers'

        // Use ES6 object literal shorthand syntax to define the object shape
        const rootReducer = combineReducers({
        theDefaultReducer,
        firstNamedReducer,
        secondNamedReducer
        })

        const store = createStore(rootReducer)
        console.log(store.getState())
        // {theDefaultReducer : 0, firstNamedReducer : 1, secondNamedReducer : 2}

Notice that because we used the ES6 shorthand for defining an object literal, the key names in the resulting state are the same as the variable names from the imports. This may not always be the desired behavior, and is often a cause of confusion for those who aren't as familiar with ES6 syntax.

Also, the resulting names are a bit odd. It's generally not a good practice to actually include words like "reducer" in your state key names - the keys should simply reflect the domain or type of data they hold. This means we should either explicitly specify the names of the keys in the slice reducer object to define the keys in the output state object, or carefully rename the variables for the imported slice reducers to set up the keys when using the shorthand object literal syntax.

A better usage might look like:

        import { combineReducers, createStore } from 'redux'

        // Rename the default import to whatever name we want. We can also rename a named import.
        import defaultState, {
        firstNamedReducer,
        secondNamedReducer as secondState
        } from './reducers'

        const rootReducer = combineReducers({
        defaultState, // key name same as the carefully renamed default export
        firstState: firstNamedReducer, // specific key name instead of the variable name
        secondState // key name same as the carefully renamed named export
        })

        const reducerInitializedStore = createStore(rootReducer)
        console.log(reducerInitializedStore.getState())
        // {defaultState : 0, firstState : 1, secondState : 2}

This state shape better reflects the data involved, because we took care to set up the keys we passed to `combineReducers`.

## Redux Docs: Combined Reducer Syntax

As your app grows more complex, you'll want to split your reducing function into separate functions, each managing independent parts of the state.

The combineReducers helper function turns an object whose values are different reducing functions into a single reducing function you can pass to createStore.

The resulting reducer calls every child reducer, and gathers their results into a single state object. The state produced by combineReducers() namespaces the states of each reducer under their keys as passed to combineReducers()

***Example:***

        rootReducer = combineReducers({potato: potatoReducer, tomato: tomatoReducer})
        // This would produce the following state object
        {
        potato: {
            // ... potatoes, and other state managed by the potatoReducer ...
        },
        tomato: {
            // ... tomatoes, and other state managed by the tomatoReducer, maybe some nice sauce? ...
        }
        }

You can control state key names by using different keys for the reducers in the passed object. For example, you may call combineReducers({ todos: myTodosReducer, counter: myCounterReducer }) for the state shape to be { todos, counter }.

A popular convention is to name reducers after the state slices they manage, so you can use ES6 property shorthand notation: combineReducers({ counter, todos }). This is equivalent to writing `combineReducers({ counter: counter, todos: todos })`.

### Arguments

1. `reducers` (Object): An object whose values correspond to different reducing functions that need to be combined into one. See the notes below for some rules every passed reducer must follow.

- Earlier documentation suggested the use of the ES6 import * as `reducers` syntax to obtain the `reducers` object. This was the source of a lot of confusion, which is why we now recommend exporting a single reducer obtained using combine`Reducers()` from `reducers/index.js` instead. An example is included below.

### Returns

(Function): A reducer that invokes every reducer inside the `reducers` object, and constructs a state object with the same shape.

### Notes

This function is mildly opinionated and is skewed towards helping beginners avoid common pitfalls. This is why it attempts to enforce some rules that you don't have to follow if you write the root reducer manually.

Any reducer passed to `combineReducers` must satisfy these rules:

1. For any action that is not recognized, it must `return` the state given to it as the first argument.

2. It must never `return` `undefined`. It is too easy to do this by mistake via an early `return` statement, so `combineReducers` throws if you do that instead of letting the error manifest itself somewhere else.

3. If the state given to it is `undefined`, it must `return` the initial state for this specific reducer. According to the previous rule, the initial state must not be `undefined` either. It is handy to specify it with ES6 optional arguments syntax, but you can also explicitly check the first argument for being `undefined`.

#### References

- Redux Docs: Using Combined Reducers [Read full article](https://redux.js.org/usage/structuring-reducers/using-combinereducers/)

- Redux Docs: Combined Reducer Syntax [Read full article](https://redux.js.org/api/combinereducers/)

- Multiple Reducers Example [Check it out](https://www.youtube.com/watch?v=gBER4Or86hE)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
