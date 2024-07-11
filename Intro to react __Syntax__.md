## general format

```tsx
const JSX = (
  <div>
    <h1>This is a block of JSX</h1>
    <p>Here's a subtitle</p>
  </div>
);
```

## why use Div

One important thing to know about nested JSX is that it must return a single element.

This one parent element would wrap all of the other levels of nested elements.

For instance, several JSX elements written as siblings with no parent wrapper element will not transpile.

```tsx
Valid JSX:

<div>
  <p>Paragraph One</p>
  <p>Paragraph Two</p>
  <p>Paragraph Three</p>
</div>

Invalid JSX:

<p>Paragraph One</p>
<p>Paragraph Two</p>
<p>Paragraph Three</p>
```

## comments

To put comments inside JSX, you use the syntax `{/* */}` to wrap around the comment text.

```tsx
const JSX = (
  <div>
    <h1>This is a block of JSX</h1>
    <p>Here's a subtitle</p>
    {/*my first comment */}
  </div>
);
```

## paths

When importing modules or components from a file path in JavaScript or TypeScript, the prefixes `./` and `../` indicate different paths relative to the current file's location:

1. **`./` Prefix**:
    
    - The `./` prefix refers to the current directory.
    - When you import using `./`, you are specifying that the file you want to import is located in the same directory as the current file.
    
    ```jsx
    javascriptCopy code
    import MyComponent from './MyComponent'; // Importing from the current directory
    ```
    
2. **`../` Prefix**:
    
    - The `../` prefix refers to the parent directory.
    - When you import using `../`, you are specifying that the file you want to import is located in the parent directory of the current file.
    
    ```jsx
    javascriptCopy code
    import MyComponent from '../components/MyComponent'; // Importing from the parent directory's "components" directory
    ```
    

## **Render HTML Elements to the DOM**

<aside> 💡 [DOM](https://www.youtube.com/watch?v=BYbgopx44vo) refers to the Document Object Model that represents the content of XML or HTML documents as a tree structure so that the programs can be read, accessed and changed in the document structure, style, and content. Table of Content. Prerequisites.

i.e. react itself doesnt render the output in the browser, that’s where reactDom comes

</aside>

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/67edefdb-f5fa-4129-984d-b5c27a8de082/c48e5ac3-f976-4b49-93c2-3d7d46ef8a8f/Untitled.png)

With React, we can render this JSX directly to the HTML DOM using React's rendering API known as **ReactDOM**.

**ReactDOM** offers a simple method to render React elements to the DOM which looks like this: `ReactDOM.render(componentToRender, targetNode)`, where the first argument is the React element or component that you want to render, and the second argument is the DOM node that you want to render the component to.

As you would expect, `ReactDOM.render()` must be called after the JSX element declarations, just like how you must declare variables before using them.

**Example**

The code editor has a simple JSX component. Use the `ReactDOM.render()` method to render this component to the page. You can pass defined JSX elements directly in as the first argument and use `document.getElementById()` to select the DOM node to render them to. There is a `div` with `id='challenge-node'` available for you to use. Make sure you don't change the `JSX` constant.

```tsx
const JSX = (
  <div>
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);

ReactDOM.render(JSX,document.getElementById('challenge-node'))
```

## **Defining an HTML Class in JSX**

<aside> 💡 Classes: used to define styles once and then use them on several different elements

</aside>

One key difference in JSX is that you can no longer use the word `class` to define HTML classes. This is because `class` is a reserved word in JavaScript. Instead, JSX uses `className`.

<aside> 💡 In fact, the naming convention for all HTML attributes and event references in JSX become camelCase. For example, a click event in JSX is `onClick`, instead of `onclick`. Likewise, `onchange` becomes `onChange`. While this is a subtle difference, it is an important one to keep in mind moving forward.

</aside>

```tsx
const JSX = (
  <div className="myDiv">
    <h1>Add a class to this div</h1>
  </div>
);
```

## **Self-Closing JSX Tags**

In HTML, almost all tags have both an opening and closing tag: `<div></div>`; the closing tag always has a forward slash before the tag name that you are closing. However, there are special instances in HTML called “self-closing tags”, or tags that don’t require both an opening and closing tag before another tag can start.

In JSX, the rules are a little different. Any JSX element can be written with a self-closing tag, and every element must be closed. The line-break tag, for example, must always be written as `<br />` in order to be valid JSX that can be transpiled. A `<div>`, on the other hand, can be written as `<div />` or `<div></div>`. The difference is that in the first syntax version there is no way to include anything in the `<div />`. You will see in later challenges that this syntax is useful when rendering React components.

```tsx
const JSX = (
  <div>
    <h2>Welcome to React!</h2> <br />
    <p>Be sure to close all tags!</p>
    <hr />
  </div>
);
```

# **Functional Components***
this part is obsolete 

## **Stateless Functional Component** (obsolete)

<aside> 💡 A _stateless functional component_ is any function you write which accepts props and returns JSX. A _stateless component_, on the other hand, is a class that extends `React.Component`, but does not use internal state. Finally, a _stateful component_ is a class component that does maintain its own internal state. You may see stateful components referred to simply as components or React components. A common pattern is to try to minimize statefulness and to create stateless functional components wherever possible. This helps contain your state management to a specific area of your application. In turn, this improves development and maintenance of your app by making it easier to follow how changes to state affect its behavior. stateful is usually used through classes

</aside>

Components are the core of React. Everything in React is a component and here you will learn how to create one.

There are two ways to create a React component. The first way is to use a JavaScript function. Defining a component in this way creates a _stateless functional component_. For now, think of a stateless component as one that can receive data and render it, but does not manage or track changes to that data.

To create a component with a function, you simply write a JavaScript function that returns either JSX or `null`. One important thing to note is that React requires your function name to begin with a capital letter. Here's an example of a stateless functional component that assigns an HTML class in JSX:

```tsx
const DemoComponent = function() {
  return (
    <div className='customClass' />
  );
};
```

After being transpiled, the `<div>` will have a CSS class of `customClass`.

Because a JSX component represents HTML, you could put several components together to create a more complex HTML page. This is one of the key advantages of the component architecture React provides. It allows you to compose your UI from many separate, isolated components. This makes it easier to build and maintain complex user interfaces.

## **Creating a React Component** (obsolete)

The other way to define a React component is with the ES6 `class` syntax. In the following example, `Kitten` extends `React.Component`:

```tsx
class Kitten extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <h1>Hi</h1>
    );
  }
}
```

This creates an ES6 class `Kitten` which extends the `React.Component` class. So the `Kitten` class now has access to many useful React features, such as local state and lifecycle hooks.

Also notice the `Kitten` class has a `constructor` defined within it that calls `super()`. It uses `super()` to call the constructor of the parent class, in this case `React.Component`. The constructor is a special method used during the initialization of objects that are created with the `class` keyword. It is best practice to call a component's `constructor` with `super`, and pass `props` to both. This makes sure the component is initialized properly. For now, know that it is standard for this code to be included. Soon you will see other uses for the constructor as well as `props`.

## **Creating a Component with Composition**

Now we will look at how we can compose multiple React components together. Imagine you are building an app and have created three components: a `Navbar`, `Dashboard`, and `Footer`.

To compose these components together, you could create an `App` _parent_ component which renders each of these three components as _children_. To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX. For example, in the `render` method you could write:

```tsx
return (
 <App>
  <Navbar />
  <Dashboard />
  <Footer />
 </App>
)
```

When React encounters a custom HTML tag that references another component (a component name wrapped in `< />` like in this example), it renders the markup for that component in the location of the tag. This should illustrate the parent/child relationship between the `App` component and the `Navbar`, `Dashboard`, and `Footer`.

example

```tsx
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};

class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        { /* Change code below this line */ }
        <ChildComponent />
        { /* Change code above this line */ }
      </div>
    );
  }
};
```

## **Rendering Nested Components**

there are many different ways you can compose components with React. (last heading is an example)

Component composition is one of React's powerful features. When you work with React, it is important to start thinking about your user interface in terms of components like the App example in the last challenge. You break down your UI into its basic building blocks, and those pieces become the components. This helps to separate the code responsible for the UI from the code responsible for handling your application logic. It can greatly simplify the development and maintenance of complex projects.

- example
    
    ```tsx
    const TypesOfFruit = () => {
      return (
        <div>
          <h2>Fruits:</h2>
          <ul>
            <li>Apples</li>
            <li>Blueberries</li>
            <li>Strawberries</li>
            <li>Bananas</li>
          </ul>
        </div>
      );
    };
    
    const Fruits = () => {
      return (
        <div>
          
          <TypesOfFruit />
          
        </div>
      );
    };
    
    class TypesOfFood extends React.Component {
      constructor(props) {
        super(props);
      }
    
      render() {
        return (
          <div>
            <h1>Types of Food:</h1>
            
            <Fruits />
            
          </div>
        );
      }
    };
    ```
    

## **Render a Class Component to the DOM**

The process for rendering React components will look very similar to using the ReactDOM API.

React components are passed into `ReactDOM.render()` a little differently than JSX elements. For JSX elements, you pass in the name of the element that you want to render. However, for React components, you need to use the same syntax as if you were rendering a nested component, for example `ReactDOM.render(<ComponentToRender />, targetNode)`. You use this syntax for both ES6 class components and functional components.

```tsx
ReactDOM.render(<TypesOfFood />, document.getElementById('challenge-node'))
```

# Props

## **Passing Props to a Stateless Functional Component**

**props**. In React, you can pass props, or properties, to child components. Say you have an `App` component which renders a child component called `Welcome` which is a stateless functional component. You can pass `Welcome` a `user` property by writing:

```tsx
<App>
  <Welcome user='Mark' />
</App>
```

You use **custom HTML attributes** created by you and supported by React to be passed to the component. In this case, the created property `user` is passed to the component `Welcome`. Since `Welcome` is a stateless functional component, it has access to this value like so:

```tsx
const Welcome = (props) => <h1>Hello, {props.user}!</h1>
```

It is standard to call this value `props` and when dealing with stateless functional components, you basically consider it as an argument to a function which returns JSX. You can access the value of the argument in the function body. With class components, you will see this is a little different.

- example
    
    There are `Calendar` and `CurrentDate` components in the code editor. When rendering `CurrentDate` from the `Calendar` component, pass in a property of `date` assigned to the current date from JavaScript's `Date` object. Then access this `prop` in the `CurrentDate` component, showing its value within the `p` tags. Note that for `prop` values to be evaluated as JavaScript, they must be enclosed in curly brackets, for instance `date={Date()}`.
    
    ```tsx
    const CurrentDate = (props) => {
      return (
        <div>
          { /* Change code below this line */ }
          <p>The current date is: {props.date}</p>
          { /* Change code above this line */ }
        </div>
      );
    };
    
    class Calendar extends React.Component {
      constructor(props) {
        super(props);
      }
      render() {
        return (
          <div>
            <h3>What date is it?</h3>
            { /* Change code below this line */ }
            <CurrentDate date={Date()} />
            { /* Change code above this line */ }
          </div>
        );
      }
    };
    ```
    
    **Output**
    
    ### What date is it?
    
    The current date is: Sat Jun 15 2024 16:23:07 GMT+0300 (Eastern European Summer Time)
    

## **Passing an Array as Props** 

To pass an array to a JSX element, it must be treated as JavaScript and wrapped in curly braces.

```tsx
<ParentComponent>
  <ChildComponent colors={["green", "blue", "red"]} />
</ParentComponent>
```

The child component then has access to the array property `colors`. Array methods such as `join()` can be used when accessing the property.

```tsx
const ChildComponent = (props) => <p>{props.colors.join(', ')}</p>
```

This will join all `colors` array items into a comma separated string and produce: `<p>green, blue, red</p>`.

- example
    
    ```tsx
    const List = (props) => {
      { /* Change code below this line */ }
      return <p>{props.tasks.join(', ')}</p>
      { /* Change code above this line */ }
    };
    
    class ToDo extends React.Component {
      constructor(props) {
        super(props);
      }
      render() {
        return (
          <div>
            <h1>To Do Lists</h1>
            <h2>Today</h2>
            { /* Change code below this line */ }
            <List tasks={["walk dog", "workout"]} />
            <h2>Tomorrow</h2>
            <List tasks={["walk dog", "workout", "a77a"]} />
            { /* Change code above this line */ }
          </div>
        );
      }
    };
    ```
    

## **Default Props**

You can assign default props to a component as a property on the component itself and React assigns the default prop if necessary. This allows you to specify what a prop value should be if no value is explicitly provided. For example, if you declare `MyComponent.defaultProps = { location: 'San Francisco' }`, you have defined a location prop that's set to the string `San Francisco`, unless you specify otherwise. React assigns default props if props are undefined, but if you pass `null` as the value for a prop, it will remain `null`.

- example
    
    ```tsx
    const ShoppingCart = (props) => {
      return (
        <div>
          <h1>Shopping Cart Component</h1>
        </div>
      )
    };
    // Change code below this line
    ShoppingCart.defaultProps = {items : 0}
    ```
    

## **Overriding Default Props**

The way to override the default props is to explicitly set the prop values for a component.

```tsx
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = {
  quantity: 0
}

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    { /* Change code below this line */ }
    return <Items quantity= {10}/>
    { /* Change code above this line */ }
  }
};
```

## **PropTypes to Define the Props You Expect**

React provides useful type-checking features to verify that components receive props of the correct type. For example, your application makes an API call to retrieve data that you expect to be in an array, which is then passed to a component as a prop. You can set `propTypes` on your component to require the data to be of type `array`. This will throw a useful warning when the data is of any other type.

It's considered a best practice to set `propTypes` when you know the type of a prop ahead of time. You can define a `propTypes` property for a component in the same way you defined `defaultProps`. Doing this will check that props of a given key are present with a given type. Here's an example to require the type `function` for a prop called `handleClick`:

```tsx
MyComponent.propTypes = { handleClick: PropTypes.func.isRequired } 
```

In the example above, the `PropTypes.func` part checks that `handleClick` is a function. Adding `isRequired` tells React that `handleClick` is a required property for that component. You will see a warning if that prop isn't provided. Also notice that `func` represents `function`. Among the seven JavaScript primitive types, `function` and `boolean` (written as `bool`) are the only two that use unusual spelling. In addition to the primitive types, there are other types available. For example, you can check that a prop is a React element. Please refer to the [documentation](https://reactjs.org/docs/typechecking-with-proptypes.html#proptypes) for all of the options.

**Note:** As of React v15.5.0, `PropTypes` is imported independently from React, like this: `import PropTypes from 'prop-types';`

- example
    
    ```tsx
    const Items = (props) => {
      return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
    };
    
    // Change code below this line
    Items.propTypes = {
      quantity: PropTypes.number.isRequired };
    // Change code above this line
    
    Items.defaultProps = {
      quantity: 0
    };
    
    class ShoppingCart extends React.Component {
      constructor(props) {
        super(props);
      }
      render() {
        return <Items />
      }
    };
    ```
    

## **Access Props Using this.props**

what if the child component that you're passing a prop to is an ES6 class component, rather than a stateless functional component? The ES6 class component uses a slightly different convention to access props. Anytime you refer to a class component within itself, you use the `this` keyword. To access props within a class component, you preface the code that you use to access it with `this`. For example, if an ES6 class component has a prop called `data`, you write `{this.props.data}` in JSX.

- example
    
    ```tsx
    class App extends React.Component {
      constructor(props) {
        super(props);
    
      }
      render() {
        return (
            <div>
                { /* Change code below this line */ }
                <Welcome name="name"/>
                { /* Change code above this line */ }
            </div>
        );
      }
    };
    
    class Welcome extends React.Component {
      constructor(props) {
        super(props);
    
      }
      render() {
        return (
            <div>
              { /* Change code below this line */ }
              <p>Hello, <strong>{this.props.name}</strong>!</p>
              { /* Change code above this line */ }
            </div>
        );
      }
    };
    ```
    
    output: Hello, **name**!
    

# states and stateful components

## initializing states

One of the most important topics in React is `state`. State consists of any data your application needs to know about, that can change over time. You want your apps to respond to state changes and present an updated UI when necessary. React offers a nice solution for the state management of modern web applications.

You create state in a React component by declaring a `state` property on the component class in its `constructor`. This initializes the component with `state` when it is created. The `state` property must be set to a JavaScript `object`. Declaring it looks like this:

```tsx
this.state = {

}
```

You have access to the `state` object throughout the life of your component. You can update it, render it in your UI, and pass it as props to child components. The `state` object can be as complex or as simple as you need it to be. Note that you must create a class component by extending `React.Component` in order to create `state` like this.

- example
    
    ```tsx
    class StatefulComponent extends React.Component {
      constructor(props) {
        super(props);
        // Only change code below this line
          this.state={firstName : 'chouchen'}
        // Only change code above this line
      }
      render() {
        return (
          <div>
            <h1>{this.state.firstName}</h1>
          </div>
        );
      }
    };
    ```
    
    output: chouchen
    

## **Rendering State in the User Interface**

### method 1: in the return statement

Once you define a component's initial state, you can display any part of it in the UI that is rendered. If a component is stateful, it will always have access to the data in `state` in its `render()` method. You can access the data with `this.state`.

If you want to access a state value within the `return` of the render method, you have to enclose the value in curly braces.

`state` is one of the most powerful features of components in React. It allows you to track important data in your app and render a UI in response to changes in this data. If your data changes, your UI will change. React uses what is called a virtual DOM, to keep track of changes behind the scenes. When state data updates, it triggers a re-render of the components using that data - including child components that received the data as a prop. React updates the actual DOM, but only where necessary. This means you don't have to worry about changing the DOM. You simply declare what the UI should look like.

Note that if you make a component stateful, no other components are aware of its `state`. Its `state` is completely encapsulated, or local to that component, unless you pass state data to a child component as `props`. This notion of encapsulated `state` is very important because it allows you to write certain logic, then have that logic contained and isolated in one place in your code.

In JSX, any code you write with curly braces `{ }` will be treated as JavaScript. So to access the value from `state` just enclose the reference in curly braces. View the [previous heading](https://www.notion.so/React-ee8661dc32cb40988bcd16409741f825?pvs=21) for an example

### method 2: before return statement, after render()

There is another way to access `state` in a component. In the `render()` method, before the `return` statement, you can write JavaScript directly. For example, you could declare functions, access data from `state` or `props`, perform computations on this data, and so on. Then, you can assign any data to variables, which you have access to in the `return` statement.

- example
    
    ```jsx
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        this.state = {
          name: 'freeCodeCamp'
        }
      }
      render() {
        // Change code below this line
        const name=this.state.name
        // Change code above this line
        return (
          <div>
            { /* Change code below this line */ }
            <h1>{name}</h1>
            { /* Change code above this line */ }
          </div>
        );
      }
    };
    ```
    

## setting states ****

### **with this.setState**

React provides a method for updating component `state` called `setState`. You call the `setState` method within your component class like so: `this.setState()`, passing in an object with key-value pairs. The keys are your state properties and the values are the updated state data. For instance, if we were storing a `username` in state and wanted to update it, it would look like this:

```tsx
this.setState({
  username: 'Lewis'
});
```

React expects you to never modify `state` directly, instead always use `this.setState()` when state changes occur. Also, you should note that React may batch multiple state updates in order to improve performance. What this means is that state updates through the `setState` method can be asynchronous. There is an alternative syntax for the `setState` method which provides a way around this problem. This is rarely needed but it's good to keep it in mind! Please consult our [React article](https://www.freecodecamp.org/news/what-is-state-in-react-explained-with-examples/) for further details.

### in a function and arguments

```tsx
handleClick() {
  this.setState((prevState) => {
    return {
      counter: prevState.counter + 1
    };
  });

  console.log("counter", this.state.counter);
}
```

## Buttons and state changes

```tsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    // Change code below this line
    this.setState({name : 'React Rocks!'})
    // Change code above this line
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

- The line `this.handleClick = this.handleClick.bind(this);` ensures that the `handleClick` function has access to the component's `this` context (and its state) when called from the event handler.
- In modern React, using arrow functions for event handlers simplifies this process.

## **Bind 'this' to a Class Method**

# Context

used to pass down props to all of the children of the app without having to manually pass: like a global state to all the children

contexts are broken into two different sections

- context provider; you wrap within it all the code that needs access to the information in the context and it has a single prop called value (whatever the value of the context is)