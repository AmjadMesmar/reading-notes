
# Review, Research, and Discussion

- Do child components have direct access to props/state from the parent?

To be able to access and update state from the child component, we can add a method that handles updating the state to the parent component and pass the method as a prop to the child component instead of the state itself.

- When a component “wraps” another component, how does the child component’s output get rendered?

Wrapper components are components that surround unknown components and provide a default structure to display the child components. This pattern is useful for creating user interface (UI) elements that are used repeatedly throughout a design, like modals, template pages, and information tiles.

        <Main>
        <Content />
        </Main>

- Can a component, such as ***Content***, which is a child also be used as a standalone component elsewhere in the application?

Yes, using composition.

- What trick can a parent use to share all props with it’s children

Using Inheretence.

## Document the following Vocabulary Terms

- props.children: props. children does is that it is used to display whatever you include between the opening and closing tags when invoking a component. A simple example: Here's an example of a stateless function that is used to create a component.

- composition: React composition is a pattern that can be used to break a complex component down to smaller components, and then composing those smaller components to structure and complete your application.

## Browser router tutorial

React Router v4 is a pure React rewrite of the popular React package. Previous versions of React Router used configuration disguised as pseudo-components and could be difficult to understand. With v4, everything is “just components”.

In this tutorial, we will be building a single-page application website for a local sports team. We will go over all of the basics needed to get our site up and routing. This will include:

1. Choosing our router
2. Creating our routes
3. Navigating between routes using links

Single-page application?

If you are curious about how single-page applications actually work, you can check out my How Single-Page Applications Workblog post.

### The code

Do you just want to see the website in action? Here it is. No fancy styling, just a simple, functional website.

Installation

React Router has been broken into three packages: react-router, react-router-dom, and react-router-native.

You should almost never have to install react-router directly. That package provides the core routing components and functions for React Router applications. The other two provide environment specific (browser and React Native) components, but they both also re-export all of react-router's exports.

We are building a website (something that will be run in browsers), so we will install react-router-dom.

        npm install --save react-router-dom

### The Router

When starting a new project, you need to determine which type of router to use. For browser based projects, there are `BrowserRouter` and `HashRouter` components. The `BrowserRouter` should be used when you have a server that will handle dynamic requests (knows how to respond to any possible URI), while the `HashRouter` should be used for static websites (where the server can only respond to requests for files that it knows about).

Usually it is preferable to use a `BrowserRouter`, but if your website will be hosted on a server that only serves static files, then the `HashRouter` is a good solution.

For our project, we will assume that the website will be backed by a dynamic server, so our router component of choice is the `BrowserRouter`.

### History

Each router creates a history object, which it uses to keep track of the current location 1 and re-render the website whenever that changes. The other components provided by React Router rely on having that history object available through React’s context, so they must be rendered as descendants of a router component. A React Router component that does not have a router as one of its ancestors will fail to work.

### What does the Route render?

Routes have three props that can be used to define what should be rendered when the route’s path matches. Only one should be provided to a `<Route>` element.

component — A React component. When a route with a component prop matches, the route will return a new element whose type is the provided React component (created using React.createElement).
render — A function that returns a React element 5. It will be called when the path matches. This is similar to component, but is useful for inline rendering and passing extra props to the element.
children — A function that returns a React element. Unlike the prior two props, this will always be rendered, regardless of whether the route’s path matches the current location.

        <Route path='/page' component={Page} />
        const extraProps = { color: 'red' }
        <Route path='/page' render={(props) => (
        <Page {...props} data={extraProps}/>
        )}/>
        <Route path='/page' children={(props) => (
        props.match
            ? <Page {...props}/>
            : <EmptyPage {...props}/>
        )}/>

Typically, either the component or render prop should be used. The children prop can be useful occasionally, but typically it is preferable to render nothing when the path does not match. We do not have any extra props to pass to the components, so each of our `<Route>`s will use the component prop.

#### References

- browser router tutorial [Read full article](https://blog.pshrmn.com/simple-react-router-v4-tutorial/)

- browser router api docs [Check it out](https://reactrouter.com/web/api)

- react-if component [Check it out](https://www.npmjs.com/package/react-if)

- react testing library queries [Check it out](https://testing-library.com/docs/queries/about/)

- aria roles [Check it out](https://www.w3.org/TR/html-aria/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
