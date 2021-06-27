# Review, Research, and Discussion

- What does a component’s lifecycle refer to?

Every React Component has a lifecycle of its own, lifecycle of a component can be defined as the series of methods that are invoked in different stages of the component's existence. ... Mounting: Mounting is the stage of rendering the JSX returned by the render method itself.

- Why do you sometimes need to “wrap” functions in useCallback when called from within useEffect

`useCallback` will help in avoiding regeneration of functions when the functional component re-renders. However there isn't much of a performance difference caused by recreation of functions.

Using `useCallback` should be preferred in the following cases

1. If you are passing the function on to child component as props and the child component doesn't often need re-rendering except when a certain prop change then `useCallback` might prevent certain re-renders. However if you state is complex and you need multiple such functions to be passed on to children as props, it better to shift to useReducer instead of useState and pass on the dispatch method to child components

2. You are specifying a function as a dependency to useEffect. In such as case you must ensure that the function in not recreated on every render or the useEffect will be triggered on every render.

Overall a decision to use `useCallback` must be made judiciously instead of blindly since you might just overdo the advantage offered by `useCallback` and end up degrading the performance since `useCallback` will also memoize the functions and a frequently changing dependency might anyways need to recreate the function.
Share

- Why are functional components preferred over class components?

There are mainly two components in React:

1. Functional Components
2. Class Components

***Functional Components***

1. Functional components are basic JavaScript functions. These are typically arrow functions but can also be created with the regular function keyword.

2. Sometimes referred to as “dumb” or “stateless” components as they simply accept data and display them in some form; that is they are mainly responsible for rendering UI.

3. React lifecycle methods (for example, componentDidMount) cannot be used in functional components.

4. There is no render method used in functional components.

5. These are mainly responsible for UI and are typically presentational only (For example, a Button component).

6. Functional components can accept and use props.

7. Functional components should be favored if you do not need to make use of React state.

***Example***
        import React from "react";

        const Person = props => (
        <div>
            <h1>Hello, {props.name}</h1>
        </div>
        );
        export default Person;

***Class Components***

1. Class components make use of ES6 class and extend the Component class in React.

2. Sometimes called “smart” or “stateful” components as they tend to implement logic and state.

3. React lifecycle methods can be used inside class components (for example, componentDidMount).

4. You pass props down to class components and access them with this.props

***Example***

        import React, { Component } from "react";

        class Person extends Component {
        constructor(props){
            super(props);
            this.state = {
            myState: true;
            }
        }
        
        render() {
            return (
            <div>
                <h1>Hello Person</h1>
            </div>
            );
        }
        }

export default Person;

- What is wrong with the following code?

        import React, {useState, useEffect} from 'react';

        function MyComponent(props) {
        const [count, setCount] = useState(0);

        function changeCount(e) {
            setCount(e.target.value);
        }

        let renderedItems = []

        for (let i = 0; i < count; i++) {
            useEffect( () => {
            console.log('component mount/update');
            }, [count]);

            renderedItems.push(<div key={i}>Item</div>);
        }

        return (<div>
            <input type='number' value={count} onChange={changeCount}/>
            {renderedItems}
            </div>);
        }

## Document the following Vocabulary Terms

- State hook: A Hook is a special function that lets you “hook into” React features. For example, useState is a Hook that lets you add React state to function components.

- Effect hook: The Effect Hook, useEffect , adds the ability to perform side effects from a function component. It serves the same purpose as componentDidMount , componentDidUpdate , and componentWillUnmount in React classes, but unified into a single API.

- Reducer hook: The useReducer is a hook I use sometimes to manage the state of the application. ... It acts as an alternate hook to the useState hook to manage complex state in your application. The useReducer hook uses the same concept as the reducers in Redux. It is basically a pure function, with no side-effects.

## custom hooks

Hooks are just functions! Anything that is a function can become a Hook. I feel that the documentation on the ReactJS docs site is not simple enough. This is no knock on them, I just felt if I could try to explain it in even simpler terms, more people could benefit. So here is my stab at this one!

### Creating a Custom Hook

I really liked something that was tweeted out recently by Adam Rackis: "Hooks unleash a level of composition well above and beyond anything we've seen." What I would have you understand about Hooks is that all of the great changes that we have seen with Classes and how we have so many options for composition, well that's all available in Hooks now. This means that now our hands are not tied when it comes to the composition of functional components in React. And this is a huge advancement for React developers.

Custom Hooks are JavaScript functions whose names are prefixed with the word use. A custom Hook is a normal function but we hold them to a different standard. By adding the word use to the beginning, it lets us know that this function follows the rules of Hooks.

With a better understanding of Hooks, let's take what we know to be a simple piece of code, our document title update, and create a simple custom Hook.

It seems like something we may want to do on several pages or inside numerous different functional components in our app. When information changes we want to update the document title with some type of string. Additionally, we don't want to repeat this logic inside every functional component. We will start by extracting this code into a Hook locally on the same page, and then see how the same Hook can be imported into many components and co-located. Pretty simple right?

So we know that a Hook can call a Hook. And if that is true then our custom Hook can also call one of the React Core Basic Hooks, like `useEffect`. Let's review a functional component that updates the document title one more time. The code below can also be seen in this StackBlitz example.

    import React, { Component, useState, useEffect } from 'react';

    function Counter() {
      const [count, setCount] = useState(0);
      const incrementCount = () => setCount(count + 1);
      useEffect(() => {
        document.title = `You clicked ${count} times`
      });

      return (
        <div>
          <p>You clicked {count} times</p>
          <button onClick={incrementCount}>Click me</button>
        </div>
      )
    }

    export default Counter;

So what we would like to do here is to create a custom Hook that we pass a piece of text into and the Hook updates the document title for us. Let's first look just at the code required to create this custom Hook:

    const useDocumentTitle = (title) => {
      useEffect(() => {
        document.title = title;
      }, [title])
    }

Above you see that all we need this Hook to take as an argument is a string of text which we will call title. Inside the Hook we call React Core's basic useEffect Hook and set the title so long as the title has changed. The second argument to useEffect will perform that check for us and only update the title if its local state is different than what we are passing in. You mean, creating a custom Hook is as easy as creating a function? Yes, it's that easy at the core, and that function can reference any other Hook. Hot damn... Creating custom Hooks is easier than we thought!

### Building Your Own Hooks

Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.

Building your own Hooks lets you extract component logic into reusable functions.

When we were learning about using the Effect Hook, we saw this component from a chat application that displays a message indicating whether a friend is online or offline:

        import React, { useState, useEffect } from 'react';

        function FriendStatus(props) {
        const [isOnline, setIsOnline] = useState(null);  useEffect(() => {    function handleStatusChange(status) {      setIsOnline(status.isOnline);    }    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);    return () => {      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);    };  });
        if (isOnline === null) {
            return 'Loading...';
        }
        return isOnline ? 'Online' : 'Offline';
        }

Now let’s say that our chat application also has a contact list, and we want to render names of online users with a green color. We could copy and paste similar logic above into our `FriendListItem` component but it wouldn’t be ideal:

        import React, { useState, useEffect } from 'react';

        function FriendListItem(props) {
        const [isOnline, setIsOnline] = useState(null);  useEffect(() => {    function handleStatusChange(status) {      setIsOnline(status.isOnline);    }    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);    return () => {      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);    };  });
        return (
            <li style={{ color: isOnline ? 'green' : 'black' }}>
            {props.friend.name}
            </li>
        );
        }

Instead, we’d like to share this logic between `FriendStatus` and `FriendListItem`.

Traditionally in React, we’ve had two popular ways to share stateful logic between components: render props and higher-order components. We will now look at how Hooks solve many of the same problems without forcing you to add more components to the tree.

## async hooks

Picture this, You have text box which can give list books from google store based on what you type on it. If no book available on that particular search query than show 'No Book Found'. By default, it will always show 'Search for Books'.

Scenario's :

1) No Search : 'Search for Books'.
2) No Result : 'No Book Found'.
3) Found Books : 'Show list of books'.

In above scenarios', we want our result to update after searching the topic on Google API's. This clearly shows that we need to use promises or 'Async-await' to achieve the results. But here we want to make our custom hook which search for books when we hit the search button and show the results.

Now the question is Why we want hooks in this case. Answer is very simple, because we want to make our code cleaner and single liner on final usage. It must be not redundant i.e DRY(Don't Repeat Yourself).

        function App() {
        const [search, setSearch] = React.useState("");
        const [query, setQuery] = React.useState("");
        return (
            <div className="App">
            <h1>Search for Books on any Topic</h1>
            <form
                onSubmit={e => {
                e.preventDefault();
                setQuery(search);
                }}
            >
                <label>Search : </label>
                <input type="text" onChange={e => setSearch(e.target.value)} />
                <input type="submit" value="search" />
            </form>

            <h1>List Result on {query}</h1>
            </div>
        );

Till now this is our simple code for getting the final search value in state 'query'. Now we make our custom Async hook to search on google Api's.

function useAsyncHook(searchBook) {
  const [result, setResult] = React.useState([]);
  const [loading, setLoading] = React.useState("false");

        React.useEffect(() => {
            async function fetchBookList() {
            try {
                setLoading("true");
                const response = await fetch(
                `https://www.googleapis.com/books/v1/volumes?q=${searchBook}`
                );

        const json = await response.json();
        // console.log(json);
        setResult(
          json.items.map(item => {
            console.log(item.volumeInfo.title);
            return item.volumeInfo.title;
          })
        );
      } catch (error) {
        setLoading("null");
      }
    }

    if (searchBook !== "") {
      fetchBookList();
    }
        }, [searchBook]);

        return [result, loading];
        }

    We cannot use 'async' keyword with 'useEffect' callback method. It will result in race conditions.

We are fetching our books from google api and then updating our 'setResult' state with book title. React.useEffect method will only run when our 'searchBook' got change.

        //Updated App Component
        function App() {
        const [search, setSearch] = React.useState("");
        const [query, setQuery] = React.useState("");
        const [result, loading] = useAsyncHook(query);
        return (
            <div className="App">
            <h1>Search for Books on any Topic</h1>
            <form
                onSubmit={e => {
                e.preventDefault();
                setQuery(search);
                }}
            >
                <label>Search : </label>
                <input type="text" onChange={e => setSearch(e.target.value)} />
                <input type="submit" value="search" />
            </form>

            {loading === "false" ? (
                <h1>Search for Books</h1>
            ) : loading === "null" ? (
                <h1>No Book Found</h1>
            ) : (
                result.map(item => {
                return <p>Book Title : {item}</p>;
                })
            )}
            </div>
        );
        }

## useReducer Hook

        const [state, dispatch] = useReducer(reducer, initialArg, init);

An alternative to useState. Accepts a reducer of type (state, action) => newState, and returns the current state paired with a dispatch method. (If you’re familiar with Redux, you already know how this works.)

useReducer is usually preferable to useState when you have complex state logic that involves multiple sub-values or when the next state depends on the previous one. useReducer also lets you optimize performance for components that trigger deep updates because you can pass dispatch down instead of callbacks.

Here’s the counter example from the useState section, rewritten to use a reducer:

        const initialState = {count: 0};

        function reducer(state, action) {
        switch (action.type) {
            case 'increment':
            return {count: state.count + 1};
            case 'decrement':
            return {count: state.count - 1};
            default:
            throw new Error();
        }
        }

        function Counter() {
        const [state, dispatch] = useReducer(reducer, initialState);
        return (
            <>
            Count: {state.count}
            <button onClick={() => dispatch({type: 'decrement'})}>-</button>
            <button onClick={() => dispatch({type: 'increment'})}>+</button>
            </>
        );
        }

- Note: React guarantees that dispatch function identity is stable and won’t change on re-renders. This is why it’s safe to omit from the useEffect or useCallback dependency list.

## use hooks

### useToggle

Basically, what this hook does is that, it takes a parameter with value true or false and toggles that value to opposite. It's useful when we want to take some action into it's opposite action, for example: show and hide modal, show more/show less text, open/close side menu.

        import { useCallback, useState } from 'react';


        // Usage
        function App() {
            // Call the hook which returns, current value and the toggler function
            const [isTextChanged, setIsTextChanged] = useToggle();
            
            return (
                <button onClick={setIsTextChanged}>{isTextChanged ? 'Toggled' : 'Click to Toggle'}</button>
            );
        }

        // Hook
        // Parameter is the boolean, with default "false" value
        const useToggle = (initialState = false) => {
            // Initialize the state
            const [state, setState] = useState(initialState);
            
        // Define and memorize toggler function in case we pass down the comopnent,
        // This function change the boolean value to it's opposite value
        const toggle = useCallback(() => setState(state => !state), []);
        
        return [state, toggle]
    }

**References:**

- custom hooks - all you need to know[Read full article](https://www.telerik.com/blogs/everything-you-need-to-create-a-custom-react-hook)

- async hooks [Read full article](https://dev.to/vinodchauhan7/react-hooks-with-async-await-1n9g)

- useReducer Hook [Read full article](https://reactjs.org/docs/hooks-reference.html#usereducer)

- react custom hooks [Read full article](https://reactjs.org/docs/hooks-custom.html)

- use hooks [Check it out](https://usehooks.com/)

- hooks list [Check it out](https://github.com/rehooks/awesome-react-hooks)

- 10 essential react hooks [Check it out](https://blog.bitsrc.io/10-react-custom-hooks-you-should-have-in-your-toolbox-aa27d3f5564d)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
