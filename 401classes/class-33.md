# Review, Research, and Discussion

- Compare and Contrast Redux Toolkit with Redux “Ducks”

Ducks is a modular pattern that collocates actions, action types and reducers.

According to the Ducks proposal:

A module…

1. MUST export default a function called reducer()

2. MUST export its action creators as functions

3. MUST have action types in the form npm-module-or-app/reducer/ACTION_TYPE

4. MAY export its action types as UPPER_SNAKE_CASE, if an external reducer needs to listen for them, or if it is a published reusable library

- What is the principle advantage of Redux Toolkit

Redux Toolkit makes it easier to write good Redux applications and speeds up development, by baking in our recommended best practices, providing good default behaviors, catching mistakes, and allowing you to write simpler code. Redux Toolkit is beneficial to all Redux users regardless of skill level or experience.

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

## getting started with react native

Welcome to the very start of your React Native journey! If you're looking for environment setup instructions, they've moved to their own section. Continue reading for an introduction to the documentation, Native Components, React, and more!

Many different kinds of people use React Native: from advanced iOS developers to React beginners, to people getting started programming for the first time in their career. These docs were written for all learners, no matter their experience level or background.

### How to use these docs

You can start here and read through these docs linearly like a book; or you can read the specific sections you need. Already familiar with React? You can skip that section—or read it for a light refresher.

### Prerequisites

To work with React Native, you will need to have an understanding of JavaScript fundamentals. If you’re new to JavaScript or need a refresher, you can dive in or brush up at Mozilla Developer Network.

While we do our best to assume no prior knowledge of React, Android, or iOS development, these are valuable topics of study for the aspiring React Native developer. Where sensible, we have linked to resources and articles that go more in depth.

#### References

- getting started with react native [Read full article](https://reactnative.dev/docs/getting-started)

- the state hook [Read full article](https://reactjs.org/docs/hooks-state.html)

- effects hook [Read full article](https://reactjs.org/docs/hooks-effect.html)

- hooks api [Read full article](https://reactjs.org/docs/hooks-overview.html)

- hooks api reference [Check it out](https://reactjs.org/docs/hooks-reference.html)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
