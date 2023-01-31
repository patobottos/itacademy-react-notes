# NOTES ON REACT<br/>
**Source**: <br/>
*Full Modern React Tutorial*<br/>
https://www.youtube.com/playlist?list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d<br/>
by **The Net Ninja**<br/>

React is a JavaScript library, used for implementing user interfaces (UI). It was launched by Facebook in 2013.

How is JavaScript and HTML linked? With a syntax, called **JSX**. This returns HTML content, through a function written in JavaScript.

React uses a **Virtual DOM**, that is, an in-memory representation of the DOM.

**STATE:** each component has its own state. They communicate through a **global state**.

### **COMPONENTS**

**Components** are JavaScript objects, and one of the most important elements of React. **components** can be **reused** and **combined**.

They are the building blocks of any React application. A typical web in React might be made with several components, where components are self contained sections of contents. For example, a nav-bar, an article, a side-bar, in a website might be a component. Our mission i sto build these components and rendered them into the webpage, by React. 

Components contain: 
1) template 
2) logic

JSX syntax allows us to easily create the HTML style-like templates in components: but, though tt seems HTML, it has little differences. In the background, it transpiles this JSX into HTML, and renders this HTML to the DOM. 
One main difference: in JSX we use the keyword **"className"**, camel case, and when it converts into HTML it turns into **"class"**.

A component is, basically, a function. At the end of the file, we export it. For example:

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

In web applications, components are structure in a way they make a **components tree**. The **root component** is the first component rendered to the DOM, and sits at the very top of this tree. Next, if we are to make new components we nest them in the root one.

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
 
### **CLICK EVENTS**

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

### **STATE or data motch**

When we talk about **state** we talk about data being used by that component at point in time. That data could be an array of values, booleans, strings, objects, any kind our component uses.

If a variable changes its value, and it is not reactive, we won't see the changes in our browser. To see the new values, we have to use a **hook**, and that hook is called **useState** in this case. To use this hook, we have to import it at the beginning of the file, from the react library.

This is an example:

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

The useState hook is a function that help us create a reactive value, and provides us with the way to change that value whenever we want.  

We store the state in some kind of value. We use an array that grabs two values: first, the initial value, the second one is a function that we can ust to change the value, and most of the times starts with "set...":
    
    const [name, setName] = useState('mario');
    




