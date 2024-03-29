# NOTES ON REACT<br/>
**Source**: <br/> *Full Modern React Tutorial*<br/>
https://www.youtube.com/playlist?list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d<br/>
by **The Net Ninja**<br/>

React is an open source JavaScript view library, used for implementing user interfaces (UI). It was originally created by Jordan Walke and launched by Facebook in 2013.

How is JavaScript and HTML linked? With a syntax, called **JSX**. This returns HTML content, through a function written in JavaScript. To write JavaScript within JSX, you simply include the code within curly braces. However, because JSX is not valid JavaScript, JSX code must be compiled into JavaScript. **Babel** is the most popular transpiler.

In nested JSX, **one parent element** must wrap all the other elements. Otherwise, elements with no parent will not transpile. In order to use JSX we need to import React at the beginning of the file:

    import React from "react"
    import ReactDOM from "react-dom"

### **VIRTUAL DOM**
React uses a **Virtual DOM**, that is, an in-memory representation of the DOM. So, we can render JSX directly to the HTML DOM using React Rendering API known as ReactDOM. It offers a simple method to render React elements to the DOM which look like this:

    ReactDOM.render.(componentToRender, targetNode)

The _targetNode_ is the DOM node that you want to render the component to.

**STATE:** each component has its own state. They communicate through a **global state**.

### **COMPONENTS**

**Components** are JavaScript objects, and one of the most important elements of React. **components** can be **reused** and **combined**.

They are the building blocks of any React application. A typical web in React might be made with several components, where components are self contained sections of contents. For example, a nav-bar, an article, a side-bar, in a website might be a component. Our mission is to build these components and render them into the webpage, by React. Here's an example of a custom component named _<Page />_:

    import React from 'react'
    import ReactDom from 'react-dom'

    function Page() {
        return (
            <div>
                <h1>Reasons why I'm learning React</h1>
                <ol>
                    <li>It's cool</li>
                    <li>It will help my find a better job</li>
                </ol>
            </div>
        )
    }

    const myPage = document.getElementById("root"); // This is the place in my DOM where it will print my <Page /> component.

    ReactDom.render(<Page />, myPage);

You can decompose a whole page into smaller components. Let's see an example:

        import React from "react"
        import ReactDOM from "react-dom"

        /**
        Challenge: 

        - Move the `footer` into its own component called "Footer" 
          and render that component inside the Page component.
        - Move the `h1` and `ol` together into another component
          called "MainContent" and render inside Page as well.
        */

        function Header() {
            return (
                <header>
                    <nav>
                        <img src="./react-logo.png" width="40px" />
                    </nav>
                </header>
            )
        }

        function Footer() {
            return (
                <footer>
                    <small>© 2021 Ziroll development. All rights reserved.</small>
                </footer>
            )
        }

        function MainContent() {
            return (
                <div>
                    <h1>Reasons I'm excited to learn React</h1>
                    <ol>
                        <li>It's a popular library, so I'll be 
                        able to fit in with the cool kids!</li>
                        <li>I'm more likely to get a job as a developer
                        if I know React</li>
                    </ol>
                </div>
            )
        }

        function Page() {
            return (
                <div>
                    <Header />
                    <MainContent />
                    <Footer />
                </div>
            )
        }

        ReactDOM.render(<Page />, document.getElementById("root"))

The <Page /> component, is composed by three different and separate components: 
_<Header />, <MainContent />, <Footer />_. 
These components are reusable and easier to update.

Components contain: 
1) template 
2) logic

__JSX syntax__ allows us to easily create the HTML style-like templates in components: but, though it seems HTML, it has little differences. In the background, it transpiles this JSX into HTML, and renders this HTML to the DOM.

One main difference: in JSX we use the keyword **"className"**, camel case, and when it converts into HTML it turns into **"class"**.

A component is, basically, a function. We declare it with a capital letter (PascalCase). At the end of the file, we export it. For example:

    import './App.css';
    
    function App() {
      return (
      
      const title = "App components";
      const likes = 50;
      const link = "http://google.com";
      
        <div className="App">
          <div className="content">
           <h1>{ title }</h1>
           <p>Liked { likes } times</p>
           
           <p>{ 10 }</p>
           <p>{ 'Hello everyone' }</p>
           <p>{ [1,2,3,4,5] }</p>
           <a href={link}>Google</a>
                 
          </div>
        </div>
      );
    }
    
    export default App;"

We can output strings and numbers (which are converted to strings), calling the variables with curly braces {}, but we can't pass booleans nor objects.

In JSX, any element can be written with a __self closing tag__, and every element **must be closed**.

    <div /> // can can use it this way if we leave it empty
    or 
    <div> </div> // OK!

In web applications, components are structured in a way they make a **components tree**. The **root component** is the first component rendered to the DOM, and sits at the very top of this tree. Next, if we are to make new components we nest them in the root one.

![ROOT COMPONENT CHART](https://user-images.githubusercontent.com/92860255/215748109-9ef43e75-e8ac-4f9d-a6d1-d47b252a3469.png)

And the code in the root component would look like this:

    import './App.css';
    import Navbar from './Navbar';
    
    function App() {
    
        const title = "Welcome to the new blog";
        return (
            <div className="App">
              <Navbar />
              <div className="content">
                <h1>{ title }</h1>
              </div>
            </div>
        );
    }
    
    export default App;
 
We can add as many components as we like, and nest one component into another. 
 
There are two ways to create a React Component. One of them, is to use a JavaScript function. We call it: *Stateless Functional Component*, and we declare them with a capital letter:

    const DemoComponent = function () {
        return (
            <div className="CustomClass" />
        );
    };
 
 The other way to define React Component is with the ES6 class syntax. 
 
     class kitten extends React.Component {
     constructor(props) {
     super(props);
     }
     render () {
     return (
     <h1>Hello World!</h1>
     );
     }
    }
    React.DOM.render(`kitten', document.getElementById("node"));
 
 This creates an ES6 class **kitten** which extends the React component. So, the kitten class has **access to many useful React features**.
 
### **PROPS**
**Source**: <br/> *Learn React for free*<br/>
https://scrimba.com/learn/learnreact/<br/>
by **Bob Ziroll**<br/>

Props are used to pass information from one component to another. It can be from a parent component to a child, or from the child to the parent. They are JavaScript objects.

Just parameters being passed into a function, props being passed into a component help us make that component more reusable.

But how do we pass a prop into a component? In this way:

    <MyAwesomeFilmComponent 
        prop1="filmTitle" 
        prop2="year"
        prop3="country"
    />

How do I receive props in a component? In this way:

    function Navbar(props) {
        console.log('film title', props.prop1)
        return (
            <header>
                <h1>{props.prop1}</h1>
                <h4>{props.prop2}, {props.prop3}</h4>    
            </header>
        )
    }
    
The parameter we put inside our component will be an **object** (in our case, 'props'), that represents **all of the props** that your component received. 

So, what we _could_ decide to do _or not_ is to **destructure** that object immediately as we receive it inside of my function:

     function Navbar({prop1, prop2, prop3}) {
            console.log('film title', prop1)
            return (
                <header>
                    <h1>{prop1}</h1>
                    <h4>{prop2}, {prop3}</h4>
                </header>
            )
        }
Both ways are valid ways to use props. Whichever way we use, we must try to be consistent with it.

If I'm working with booleans, or numbers, or arrays, we put it in curly braces. Let's see an example:

    export default function App() {
        return (
            <div>
                // HERE, THE JOKE COMPONENT TAKE PROPS AS STRINGS, LIKE SETUP AND PUNCHLINE, AS NUMBERS, AS UPVOTES AND DOWNVOTES, 
                // AND AS BOOLEANS, ISPUN. ALSO, AN ARRAY OB OBJECTS IN COMMENTS.
                <Joke 
                    setup="How did the hacker escape the police?" 
                    punchline="He just ransomware!"
                    isPun={true}
                    upVotes={6}
                    downVotes={3}
                    comments={[{author: "", body: "", title: ""}, {...}]}
                />
                <Joke 
                    setup="Why don't pirates travel on mountain roads?" 
                    punchline="Scurvy."
                    isPun={false}
                    upVotes={9}
                    downVotes={1}
                    comments={[{author: "", body: "", title: ""}, {...}]}
                />
            </div>
        )
    }

In sum, curly braces is an scape to whatever we want to code in JavaScript... inside JSX.

In web apps is common for us to find raw data in an array, or in an array of JavaScript objects, and we want to turn that data into visible values on the screen. To catch those values, it is common to use **.map()** JavaScript method. This method allow us to convert an array of raw data into an array of JSX elements that can be displayed on the page. It makes our code more "self-sustaining" - not requiring additional changes whenever the raw data changes.

 
### **CLICK EVENTS**

When you have a web, there many events happening: hover events, click events, keyboard events etc. This is the way you add a click event when user clicks a button:
const Home = () => {

    const handleClick = () => {
        console.log('Hello World!');
    }

    return ( 
        <div className="home">
            <h2>Homepage</h2>
            <button onClick={handleClick}>Click me</button>
        </div>
     );
    }

    export default Home;
    
We do not use (), beacuse this would fire the event, event without clickiing the button. But what would happen if we'd like to pass a function with a parameter? We have to wrap it in an anonimous function. This is the way we'd do it:

    const Home = () => {

      const handleClick = (e) => {
        console.log('hello ninjas', e);
      }

      const handleClickAgain = (name, e) => {
        console.log('hello ' + name, e.target);
      }

      return (
        <div className="home">
          <h2>Homepage</h2>
          <button onClick={handleClick}>Click me</button>
          <button onClick={(e) => handleClickAgain('mario', e)}>Click me again</button>
        </div>
      );
    }

    export default Home;

e => is the event object, that we access when the event occurs. In this case, on clicking the button handleClickAgain we print by console the target of the event object.


## **STATE or data motch** and **HOOKS**

When we talk about **state** we talk about data being used by that component at a point in time. That data could be an array of values, booleans, strings, objects, any kind our component uses.

If a variable changes its value, and it is not reactive, we won't see the changes in our browser. To see the new values, we have to use a **hook**. You can identify a hook by its name because they usually start by the word _use_... 

### **STATE VS PROPS**

At this point, it is interesting to differenciate between Props and State.

_"Props"_ refers to the properties being passsed into a component in order for it to work correctly, similar to how a function receives parameters: from above. A component receiving props is not allowed to modify those props (i.e., they are _immutable_).

_"State"_, on the other hand, refers to values thar are _managed by the component_, similar to variables declared _inside_ a function. Any time you have changing values that should be saved/displayed, you will likely be using **state**. States are _mutable_.

## useState
States are generally used to paint information on the browser and to make React aware when some value changes. But we can also use states to collect values from the user. Usually to collect data from a form we do not use the useState hook, but rather the useRef hook. But, although in React JS both the useState and the useRef hook work, when we use React to make mobile applications, with React Native, the useRef does not work.

In this first case, we'll focus on the hook **useState**. The useState hook is a function that help us create a reactive value, and provides us with the way to change that value whenever we want. 

To use this hook, we have to import it at the beginning of the file, from the react library. This is an example:

    import { useState } from "react";

    const Home = () => {
      // let name = 'mario';
      const [name, setName] = useState('mario');
      const [age, setAge] = useState(25);

      const handleClick = () => {
        // name = 'luigi';
        setName('luigi');
        setAge(30);
      }

      return (
        <div className="home">
          <h2>Homepage</h2>
          <p>{ name } is { age } years old</p>
          <button onClick={handleClick}>Click me</button>
        </div>
      );
    }

    export default Home;

We store the state in some kind of value. We use an array that grabs two values: first, the initial value, the second one is a function that we can use to change that initial value, and most of the times starts with "set...", and then whatever we called that initial value. For example:
    
    const [name, setName] = useState('mario');

Then, when I use that value later, in the template, is going to get whatever the state of that value is:

    <p>{ name } is { age } years old</p>

So, when this value changes, is going to change in the template as well. 

    setName('luigi');
   
**setName** here is triggering React, and it re-renders the component, and when it re-renders, we have the new value of _name_ in the component. So we will use the **useState** hook when we need to use a value that changes.

### **A counter example**
**Source**: <br/> *Learn React for free*<br/>
https://scrimba.com/learn/learnreact/<br/>
by **Bob Ziroll**<br/>

Let's take the example of a counter. We have a page with two buttons, a - and a +, and when we click, we go up or down by 1. Let's see the code:

    import {useState} from "react";
    
    function App() {
      const [count, setCount] = useState(0);

      const adjustCount = (amount) => {
        setCount((prevCount) => {
        return (
            prevCount + amount
        )
        }
      };

      return (
        <div>
          <p>This is the counter value: {count}</p>
          <br />
          <button onClick={() => adjustCount(-1}>-</button> <button onClick={() => adjustCount(1}>+</button>
       </div>
      );
    }

    export default App;

If you ever need the old value of state to help you determine the new value of state, you should pass a callback function to your state setter function instead of using state directly. This callback function will receive the old value of state as its parameter, which you can then use to determine your new value of state.

### **useRef** 
There are times when we need to modify an element of the DOM in an imperative way, for example when we want to perform an animation, play a multimedia file or force a "focus" on a field. This is where having the direct reference to the DOM element using **useRef** comes in handy.

    import { useRef } from "react";

    function App() {
      const inputRef = useRef(null);
      const resultRef = useRef(null);

      const makeThings = () => {
        alert(inputRef.current.value);
        resultRef.current.innerHTML = inputRef.current.value;
      };

      return (
        <div>
          <input type="text" ref={ inputRef }/>
          <button onClick={ makeThings }>Just Do It</button>

          <br />
          <div ref={ resultRef }></div>
        </div>
      );
    }

    export default App;
   
### **useEffect**
**Source**: <br/> *The road to React*<br/>
https://www.roadtoreact.com/<br/>
by **Robin Wieruch**<br/>


The primary effect of React is to display HTML in the DOM. With **useEffect** we're looking for a side-effect: we want React to do more than just display HTML. useEffect is a hook that triggers a code every time a certain state *changes* (which is different from re-renders). This is how it looks:

    useEffect(() => {
        first

        return () => {
          second
        }
      }, [third])


React’s useEffect Hook takes two arguments: the first argument is a function where the side-effect occurs. In our case, the side-effect is when the user types the searchTerm into the browser’s local storage. The optional second argument is a dependency array of variables. If one of theses variables changes, the function for the side-effect is called. In our case, the function is called every time the searchTerm changes; and it’s also called initially when the component renders for the first time.

Leaving out the second argument, to be specific the dependency array, would make the function for the side-effect run on every render (initial render and update renders) of the component. If the dependency array of React’s useEffect is an empty array, the function for the side-effect is only called once, after the component renders for the first time. The hook lets us opt into React’s component lifecycle. It can be triggered when the component is first mounted, but also one of its dependencies are updated.

### **ADDING STYLES**
 
We generally import a css file into the app file. But, we can also do some in-line style, a bit different than HTML syntaxis. Our inline styling is a **JavaScript object**, and cannot use hiphens. So, we camelCase each CSS property (for instance, we say "backgroundColor", and not background-color). Let's see an example:

    const Navbar = () => {
      return (
        <nav className="navbar">
          <h1>The Dojo Blog</h1>
          <div className="links">
            <a href="/">Home</a>
            <a href="/create" style={{ 
              color: 'white', 
              backgroundColor: '#f1356d',
              borderRadius: '8px' 
            }}>New Blog</a>
          </div>
        </nav>
      );
    }
 
    export default Navbar;

### **STYLED COMPONENTS**

[TO BE COMPLETED]

### **ORGANIZING PROJECT STRUCTURE**
**Source**: <br/> *Learn React for free*<br/>
https://scrimba.com/learn/learnreact/<br/>
by **Bob Ziroll**<br/>

1) Every component in a separate file. To avoid any confussion, we put a name starting with a capital letter, explaining the name of that component. For example: "Header.js"
2) Piece of advice: install Vite, an extension that helps to render projects faster. (https://vitejs.dev/)
3) Decompose the design into "pieces of content", i.e., possible separate custom components. This may be an example.

![WEBPAGE STRUCTURE](https://user-images.githubusercontent.com/92860255/216955466-ea642415-5d17-41cc-bf69-431ddbcf8a8a.png)

In this way, we can start thinking how many separate custom component files we need to create.
