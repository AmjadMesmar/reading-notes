# Review, Research, and Discussion

## Document the following Vocabulary Terms

- redux toolkit slices:

Redux Toolkit makes it easier to write good Redux applications and speeds up development, by baking in our recommended best practices, providing good default behaviors, catching mistakes, and allowing you to write simpler code. Redux Toolkit is beneficial to all Redux users regardless of skill level or experience.

A Redux Slice is a collection of reducer logic and actions for a single feature of our app. The name “slice” comes from the idea that we're splitting up the root Redux state object into multiple “slices” of slate. ... submissions, and state. topics are each a separate slice of the Redux state.

- namespace:

With Redux, you can use combineReducers to create nested reducers that only operate on a slice of state, but all reducers still respond to all actions. Often this is the point—a component can affect another component just by dispatching an action. But when we started creating multiple instances of the same component, we created a system where every instance responded to action meant for just one.

We began with an initial research pass. In this stage, we took a look at commonly suggested solutions from the community: using local state and three approaches to manual namespacing via action type string.
Local State

One common solution in a case like this is to give each component a local state and to let it handle its own interactions.

However, our current front-end setup uses only functional components—functions that take props and return JSX components; no class ... extends React.Component. This choice made it easier to move to React for folks with less of a Javascript background. We were free from the this keyword and from ES6 class idiosyncrasies. Pure components were simpler to test.

#### References

- making sense of hooks [Read full article](https://medium.com/@dan_abramov/making-sense-of-react-hooks-fdbde8803889)

- the state hook [Read full article](https://reactjs.org/docs/hooks-state.html)

- effects hook [Read full article](https://reactjs.org/docs/hooks-effect.html)

- hooks api [Read full article](https://reactjs.org/docs/hooks-overview.html)

- hooks api reference [Check it out](https://reactjs.org/docs/hooks-reference.html)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
