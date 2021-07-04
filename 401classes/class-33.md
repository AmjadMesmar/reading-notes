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

### Interactive examples

This introduction lets you get started immediately in your browser with interactive examples like this one:

        import React from 'react';
        import { Text, View } from 'react-native';

        const YourApp = () => {
        return (
            <View style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
            <Text>
                Try editing me! 🎉
            </Text>
            </View>
        );
        }

        export default YourApp;

## react native basics (

### Learn the Basics

React Native is like React, but it uses native components instead of web components as building blocks. So to understand the basic structure of a React Native app, you need to understand some of the basic React concepts, like JSX, components, state, and props. If you already know React, you still need to learn some React-Native-specific stuff, like the native components. This tutorial is aimed at all audiences, whether you have React experience or not.

Let's do this thing.

### Hello World

In accordance with the ancient traditions of our people, we must first build an app that does nothing except say "Hello, world!". Here it is:

        import React from 'react';
        import { Text, View } from 'react-native';

        const HelloWorldApp = () => {
        return (
            <View
            style={{
                flex: 1,
                justifyContent: "center",
                alignItems: "center"
            }}>
            <Text>Hello, world!</Text>
            </View>
        )
        }
        export default HelloWorldApp;

If you are feeling curious, you can play around with sample code directly in the web simulators. You can also paste it into your App.js file to create a real app on your local machine.

### What's going on here?

1. First of all, we need to import React to be able to use JSX, which will then be transformed to the native components of each platform.
2. On line 2, we import the Text and View components from react-native

Then we find the HelloWorldApp function, which is a functional component and behaves in the same way as in React for the web. This function returns a View component with some styles and aText as its child.

The Text component allows us to render a text, while the View component renders a container. This container has several styles applied, let's analyze what each one is doing.

The first style that we find is flex: 1, the flex prop will define how your items are going to "fill" over the available space along your main axis. Since we only have one container, it will take all the available space of the parent component. In this case, it is the only component, so it will take all the available screen space.

The following style is justifyContent: "center". This aligns children of a container in the center of the container's main axis. Finally, we have alignItems: "center", which aligns children of a container in the center of the container's cross axis.

Some of the things in here might not look like JavaScript to you. Don't panic. This is the future.

First of all, ES2015 (also known as ES6) is a set of improvements to JavaScript that is now part of the official standard, but not yet supported by all browsers, so often it isn't used yet in web development. React Native ships with ES2015 support, so you can use this stuff without worrying about compatibility. import, export, const and from in the example above are all ES2015 features. If you aren't familiar with ES2015, you can probably pick it up by reading through sample code like this tutorial has. If you want, this page has a good overview of ES2015 features.

The other unusual thing in this code example is `<View>``<Text>`Hello world!`</Text>``</View>`. This is JSX - a syntax for embedding XML within JavaScript. Many frameworks use a specialized templating language which lets you embed code inside markup language. In React, this is reversed. JSX lets you write your markup language inside code. It looks like HTML on the web, except instead of web things like `<div>` or `<span>`, you use React components. In this case, `<Text>` is a Core Component that displays some text and View is like the `<div>` or`<span>`.

## ejecting

### Ejecting to ExpoKit

    ExpoKit is deprecated and will no longer be supported after SDK 38. If you need to make customizations to your Expo project, we recommend using the bare workflow instead.

ExpoKit is an Objective-C and Java library that allows you to use the Expo platform and your existing Expo project as part of a larger standard native project -- one that you would normally create using Xcode, Android Studio, or react-native init.

### What is this for?

If you created an Expo project and you want a way to add custom native modules, this guide will explain how to use ExpoKit for that purpose.

Normally, Expo apps are written in pure JS and never "drop down" to the native iOS or Android layer. This is core to the Expo philosophy and it's part of what makes Expo fast and powerful to use.

However, there are some cases where advanced developers need native capabilities outside of what Expo offers out-of-the-box. The most common situation is when a project requires a specific Native Module which is not supported by React Native Core or the Expo SDK.

In this case, Expo allows you to eject your pure-JS project from the Expo iOS/Android clients, providing you with native projects that can be opened and built with Xcode and Android Studio. Those projects will have dependencies on ExpoKit, so everything you already built will keep working as it did before.

We call this "ejecting" because you still depend on the Expo SDK, but your project no longer lives inside Expo Go. You control the native projects, including configuring and building them yourself.

### Should I eject to ExpoKit?

You might want to eject if:

- Your Expo project needs a native module that Expo doesn't currently support. We're always expanding the Expo SDK, so we hope this is never the case. But it happens, especially if your app has very specific and uncommon native demands.

You should not eject if:

1. All you need is to distribute your app in the iTunes Store or Google Play. Expo can build binaries for you in that case. If you eject, we can't automatically build for you any more.

2. You are uncomfortable writing native code. Ejected apps will require you to manage Xcode and Android Studio projects.

3. You enjoy the painless React Native upgrades that come with Expo. After your app is ejected, breaking changes in React Native will affect your project differently, and you may need to figure them out for your particular situation.

4. You require Expo's push notification services. After ejecting, since Expo no longer manages your push credentials, you'll need to manage your own push notification pipeline.

5. You rely on asking for help in the Expo community. In your native Xcode and Android Studio projects, you may encounter questions which are no longer within the realm of Expo.

#### References

- getting started with react native [Read full article](https://reactnative.dev/docs/getting-started)

- react native basics [Read full article](https://reactnative.dev/docs/tutorial)

- ejecting [Read full article](https://docs.expo.io/expokit/eject/?redirected)

- react native [Check it out](https://reactnative.dev/)

- expo [Check it out](https://expo.io/)

- expo snack [Check it out](https://snack.expo.io/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
