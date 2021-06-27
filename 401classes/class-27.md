# Review, Research, and Discussion

- Why is the Context API useful?
The React Context API is a way for a React app to effectively produce global variables that can be passed around. This is the alternative to "prop drilling" or moving props from grandparent to child to parent, and so on. Context is also touted as an easier, lighter approach to state management using Redux.

- Can a component outside of a provider get its context?
Easy. No need for Context. Provider . This is multiple contexts being used in one component, requiring just two calls to useContext versus wrapping your entire application in two nested contexts, which is what is what you have to do with current Context.

- What are some common use cases for using the Context API?
Context is primarily used when some data needs to be accessible by many components at different nesting levels. Apply it sparingly because it makes component reuse more difficult. If you only want to avoid passing some props through many levels, component composition is often a simpler solution than context.

- Describe “Context Hell”

## What is the React Context hell?

Like the `callback` hell, usual when `jQuery` was used for everything, the React `Context` hell is the nasty code you get taking advantage of the React Context API.

    const App = () => {
    // ... some code
    return (
        <>
        <ReduxProvider value={store}>
        <ThemeProvider value={theme}>
        <OtherProvider value={otherValue}>
            <OtherOtherProvider value={otherOtherValue}>
            {/** ... other providers*/}
                                    <HellProvider value={hell}>
                                    <HelloWorld />
                                    </HellProvider>
            {/** ... other providers*/}
            </OtherOtherProvider>
        </OtherProvider>
        </ThemeProvider>
        </ReduxProvider>
        </>
    )
    }

How to fix it?

To clean up the nasty code you get from taking advantage of React Context API we need a way to nest multiple Context.Provider without passing them as children of each other.

To achieve that we can use the React.cloneElement API.

The cloneElement API

        React.cloneElement(
        element,
        [props],
        [...children]
)

Clone and return a new React element using element as the starting point. The resulting element will have the original element’s props with the new props merged in shallowly. New children will replace existing children. key and ref from the original element will be preserved.

We can use the cloneElement API to reduce a collection of providers, this way we don't have to nest them inside each other.

        return [
        <ReduxProvider value={store} />,
        <ThemeProvider value={theme} />,
        <OtherProvider value={otherValue} />,
        <OtherOtherProvider value={otherOtherValue} />,
        // ...others,
        <HellProvider value={hell} />,
        <HelloWorld />,
        ].reduceRight((prev, provider) => React.cloneElement(provider, {}, prev))

The last element of the array is the content of the app.

Using reduceRight we preserve the nesting to make the HelloWorld element a child of all the providers.

To make it simpler to use we can implement a MultiProvider component.

        import React from 'react'

        const nest = (
        children: React.ReactNode,
        component: React.ReactElement
        ) => React.cloneElement(component, {}, children)

        export type MultiProviderProps = React.PropsWithChildren<{
        providers: React.ReactElement[]
        }>

        const MultiProvider: React.FC<MultiProviderProps> = ({
        children,
        providers
        }) => (
        <React.Fragment>
            {providers.reduceRight(nest, children)}
        </React.Fragment>
        )

        export default MultiProvider

Now we can refactor the example using the MultiProvider.

        const App = () => {
        return (
            <MultiProvider
            providers={[
                <ReduxProvider value={store} />,
                <ThemeProvider value={theme} />,
                <OtherProvider value={otherValue} />,
                <OtherOtherProvider value={otherOtherValue} />,
                // ...others,
                <HellProvider value={hell} />,
            ]}
            >
            <HelloWorld />
            </MultiProvider>
        )
        }

***You can find an implementation of MultiProvider inside the react-pendulum library.***

[react-pendulum](https://github.com/alfredosalzillo/react-pendulum)
[Original topic](https://dev.to/alfredosalzillo/the-react-context-hell-7p4)

## Document the following Vocabulary Terms

- global state: Context provides a way to pass data through the component tree without having to pass props down manually at every level, managing state in multiple components that are not directly connected.

- global context: Context provides a way to pass data through the component tree without having to pass props down manually at every level, managing state in multiple components that are not directly connected.

- provider: The `<Provider>` component makes the `Redux` store available to any nested components that need to access the `Redux` store. Since any React component in a React `Redux` app can be connected to the store, most applications will render a `<Provider>` at the top level, with the entire app's component tree inside of it.

- consumer:

***Context.Consumer***

A React component that subscribes to context changes. Using this component lets you subscribe to a context within a function component. Requires a function as a child. The function receives the current context value and returns a React node.

## what is role based access control?

### Definition of Role-Based Access Control (RBAC)

Role-based access control (RBAC) restricts network access based on a person's role within an organization and has become one of the main methods for advanced access control. The roles in RBAC refer to the levels of access that employees have to the network.

Employees are only allowed to access the information necessary to effectively perform their job duties. Access can be based on several factors, such as authority, responsibility, and job competency. In addition, access to computer resources can be limited to specific tasks such as the ability to view, create, or modify a file.

As a result, lower-level employees usually do not have access to sensitive data if they do not need it to fulfill their responsibilities. This is especially helpful if you have many employees and use third-parties and contractors that make it difficult to closely monitor network access. Using RBAC will help in securing your company’s sensitive data and important applications.

### Examples of Role-Based Access Control

Through RBAC, you can control what end-users can do at both broad and granular levels. You can designate whether the user is an administrator, a specialist user, or an end-user, and align roles and access permissions with your employees’ positions in the organization. Permissions are allocated only with enough access as needed for employees to do their jobs.

What if an end-user's job changes? You may need to manually assign their role to another user, or you can also assign roles to a role group or use a role assignment policy to add or remove members of a role group.

Some of the designations in an RBAC tool can include:

1. Management role scope – it limits what objects the role group is allowed to manage.
2. Management role group – you can add and remove members.
3. Management role – these are the types of tasks that can be performed by a specific role group.
4. Management role assignment – this links a role to a role group.

By adding a user to a role group, the user has access to all the roles in that group. If they are removed, access becomes restricted. Users may also be assigned to multiple groups in the event they need temporary access to certain data or programs and then removed once the project is complete.

Other options for user access may include:

1. Primary – the primary contact for a specific account or role.
2. Billing – access for one end-user to the billing account.
3. Technical – assigned to users that perform technical tasks.
4. Administrative – access for users that perform administrative tasks.

### Benefits of RBAC

Managing and auditing network access is essential to information security. Access can and should be granted on a need-to-know basis. With hundreds or thousands of employees, security is more easily maintained by limiting unnecessary access to sensitive information based on each user’s established role within the organization. Other advantages include:

1. Reducing administrative work and IT support. With RBAC, you can reduce the need for paperwork and password changes when an employee is hired or changes their role. Instead, you can use RBAC to add and switch roles quickly and implement them globally across operating systems, platforms and applications. It also reduces the potential for error when assigning user permissions. This reduction in time spent on administrative tasks is just one of several economic benefits of RBAC. RBAC also helps to more easily integrate third-party users into your network by giving them pre-defined roles.

2. Maximizing operational efficiency. RBAC offers a streamlined approach that is logical in definition. Instead of trying to administer lower-level access control, all the roles can be aligned with the organizational structure of the business and users can do their jobs more efficiently and autonomously.

3. Improving compliance. All organizations are subject to federal, state and local regulations. With an RBAC system in place, companies can more easily meet statutory and regulatory requirements for privacy and confidentiality as IT departments and executives have the ability to manage how data is being accessed and used. This is especially significant for health care and financial institutions, which manage lots of sensitive data such as PHI and PCI data.

### Best Practices for Implementing RBAC

Implementing a RBAC into your organization shouldn’t happen without a great deal of consideration. There are a series of broad steps to bring the team onboard without causing unnecessary confusion and possible workplace irritations. Here are a few things to map out first.

1. Current Status: Create a list of every software, hardware and app that has some sort of security. For most of these things, it will be a password. However, you may also want to list server rooms that are under lock and key. Physical security can be a vital part of data protection. Also, list the status of who has access to all of these programs and areas. This will give you a snapshot of your current data scenario.

2. Current Roles: Even if you do not have a formal roster and list of roles, determining what each individual team member does may only take a little discussion. Try to organize the team in such a way that it doesn’t stifle creativity and the current culture (if enjoyed).

3. Write a Policy: Any changes made need to be written for all current and future employees to see. Even with the use of a RBAC tool, a document clearly articulating your new system will help avoid potential issues.

4. Make Changes: Once the current security status and roles are understood (not to mention a policy is written), it’s time to make the changes.

5. Continually Adapt: It’s likely that the first iteration of RBAC will require some tweaking. Early on, you should evaluate your roles and security status frequently. Assess first, how well the creative/production process is working and secondly, how secure your process happens to be.

A core business function of any organization is protecting data. An RBAC system can ensure the company's information meets privacy and confidentiality regulations. Furthermore, it can secure key business processes, including access to IP, that affect the business from a competitive standpoint.

#### References

- what is role based access control? [Read full article](https://medium.com/@dan_abramov/making-sense-of-react-hooks-fdbde8803889)

- react-cookies component [Check it out](https://www.npmjs.com/package/react-cookies)

- react-cookie library [Check it out](https://www.npmjs.com/package/react-cookie)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
