# Review, Research, and Discussion

- Can a parent component access the state of a child component?
  In React we can access the child's state using Refs. we will assign a Refs for the child component in the parent component. then using Refs we can access the child's state.

- What can be passed along in a prop variable?
- Any data needed, for example some API fetch results.
  
- How can a child component “know” the state of another component?
To pass the state into another component, you can pass it as a prop. Then, inside ExampleComponent  you can access the data as this.

## Document the following Vocabulary Terms

- component props: “Props” is a special keyword in React, which stands for properties and is being used for passing data from one component to another. Furthermore, props data is read-only, which means that data coming from the parent should not be changed by child components.

- component state: What is State? The state is an instance of React Component Class can be defined as an object of a set of observable properties that control the behavior of the component. In other words, the State of a component is an object that holds some information that may change over the lifetime of the component.
  
- application state: Application State is a state management technique. Application State is stored in the memory of the the server and is faster than storing and retrieving information in a database. Session sate is specific for a single user session, but Application State is for all users and sessions.

## react basics recap

The life stages of a component are a little different. Here’s what it looks like:

![image](https://cdn-media-1.freecodecamp.org/images/1*U13Mlxz_ktcajaeJCyYkwg.png)

Let’s break this image down. Each colored horizontal rectangle represents a lifecycle method (except for “React updates DOM and refs”). The columns represent different stages in the components life.

A component can only be in one stage at a time. It starts with mounting and moves onto updating. It stays updating perpetually until it gets removed from the virtual DOM. Then it goes into the unmounting phase and gets removed from the DOM.

The lifecycle methods allow us to run code at specific points in the component’s life or in response to changes in the component’s life.

Let’s go through each stage of the component and the associated methods.

### Mounting

Since class-based components are classes, hence the name, the first method that runs is the constructor method. Typically, the constructor is where you would initialize component state.

Next, the component runs the getDerivedStateFromProps. I’m going to skip this method since it has limited use.

Now we come to the render method which returns your JSX. Now React “mounts” onto the DOM.

Lastly, the componentDidMount method runs. Here is where you would do any asynchronous calls to databases or directly manipulate the DOM if you need. Just like that, our component is born.

### Updating

This phase is triggered every time state or props change. Like in mounting, getDerivedStateFromProps is called (but no constructor this time!).

Next shouldComponentUpdate runs. Here you can compare old props/state with the new set of props/state. You can determine if your component should re-render or not by returning true or false. This can make your web app more efficient by cutting down on extra re-renders. If shouldComponentUpdate returns false, this update cycle ends.

If not, React re-renders and getSnapshotBeforeUpdate runs afterwards. This method has limited use as well. React then runs componentDidUpdate. Like componentDidMount you can use it to make any async calls or manipulate the DOM.

### Unmounting

Our component lived a good life, but all good things must come to an end. The unmounting phase is that last stage of the component lifecycle. When you remove a component from the DOM, React runs componentWillUnmount right before it gets removed. You should use this method to clean up any open connections such as WebSockets or intervals.

## props.children

What even is ‘children’?

The React docs say that you can use props.children on components that represent ‘generic boxes’ and that ‘don’t know their children ahead of time’. For me, that didn’t really clear things up. I’m sure for some, that definition makes perfect sense but it didn’t for me.

A simple example

Here’s an example of a stateless function that is used to create a component. Again, since this is a stateless function, there is no 'this' keyword so just use props.children

        const Picture = (props) => {
        return (
            <div>
            <img src={props.src}/>
            {props.children}
            </div>
        )
        }

A more complex example

Here I am taking the above components and using them in a simple app that keeps track of the ID of a picture when a button is clicked.

        //App.jsimport React, { Component } from 'react';import Picture from './Picture';
        import Button from './Button';class App extends Component {
        constructor(props) {
            super(props);this.state = {
            pictures: [
                {id: 1, src: 'http://via.placeholder.com/200x100'},
                {id: 2, src: 'http://via.placeholder.com/400x200'},
                {id: 3, src: 'http://via.placeholder.com/200x100'}
            ],
            currentPic: null
            };this.setCurrentPic = this.setCurrentPic.bind(this);
        }setCurrentPic(id) {
            this.setState({currentPic: id});
        }render () {
            return (
            <div>
                <div className='squares'>
                {this.state.pictures.map((picture) => {
                    return (
                    <Picture key={picture.id} src={picture.src}>
                        <Button
                        pictureSrc={picture.src}
                        setCurrentPic={this.setCurrentPic}
                        id={picture.id}
                        />
                    </Picture>
                    )
                })}
                </div>
                <div>
                <p>Current selected picture ID is {this.state.currentPic}</p>
                </div>
            </div>
            )
        }
        }export default App;//Picture.jsimport React, { Component } from 'react';const Picture = (props) => {
        return (
            <div className='picture'>
            <img src={props.src} className='picture'/>
            {props.children}
            </div>
        )
        }export default Picture;//Button.jsimport React, { Component } from 'react';class Button extends Component {
        constructor(props) {
            super(props);    this.state = {
            pictureId: null,
            label: null
            };    this.buttonLabel = this.buttonLabel.bind(this);
        }buttonLabel(src) {
            src.includes('200x100')
            ? this.setState({pictureId: this.props.id, label: 'Small'})
            : this.setState({pictureId: this.props.id, label: 'Large'})
        }componentDidMount() {
            this.buttonLabel(this.props.pictureSrc)
        }render() {
            return (
            <div>
                <button
                onClick={() => this.props.setCurrentPic(this.props.id)}
                >
                {this.state.label}
                </button>
            </div>
            )
        }
        }export default Button;

## composition vs inheritance

React has a powerful composition model, and we recommend using composition instead of inheritance to reuse code between components.

In this section, we will consider a few problems where developers new to React often reach for inheritance, and show how we can solve them with composition.

### Containment

Some components don’t know their children ahead of time. This is especially common for components like Sidebar or Dialog that represent generic “boxes”.

We recommend that such components use the special children prop to pass children elements directly into their output:

            function FancyBorder(props) {
            return (
                <div className={'FancyBorder FancyBorder-' + props.color}>
                {props.children}    </div>
            );
            }

This lets other components pass arbitrary children to them by nesting the JSX:

        function WelcomeDialog() {
        return (
            <FancyBorder color="blue">
            <h1 className="Dialog-title">        Welcome      </h1>      <p className="Dialog-message">        Thank you for visiting our spacecraft!      </p>    </FancyBorder>
        );
        }

### So What About Inheritance?

At Facebook, we use React in thousands of components, and we haven’t found any use cases where we would recommend creating component inheritance hierarchies.

Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way. Remember that components may accept arbitrary props, including primitive values, React elements, or functions.

If you want to reuse non-UI functionality between components, we suggest extracting it into a separate JavaScript module. The components may import it and use that function, object, or a class, without extending it.

#### References

- react basics recap [Read full article](https://www.freecodecamp.org/news/these-are-the-concepts-you-should-know-in-react-js-after-you-learn-the-basics-ee1d2f4b8030/)

- props.children [Read full article](https://codeburst.io/a-quick-intro-to-reacts-props-children-cb3d2fce4891)

- composition vs inheritance [Read full article](https://reactjs.org/docs/composition-vs-inheritance.html)

- state and lifecycle [Read full article](https://reactjs.org/docs/state-and-lifecycle.html)

- components and props [Read full article](https://reactjs.org/docs/components-and-props.html)

- react testing library api example [Check it out](https://testing-library.com/docs/react-testing-library/example-intro/)

- react-if component [Check it out](https://www.npmjs.com/package/react-if)

- react-testing-library-async [Check it out](https://testing-library.com/docs/dom-testing-library/api-async/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
