# NOTES ON REACT
**Source**: 
*Full Modern React Tutorial*
https://www.youtube.com/playlist?list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d
, by **The Net Ninja**

React is a JavaScript library, used for implementing user interfaces (UI). It was launched by Facebook in 2013.

How is JavaScript and HTML linked? With a syntax, called **JSX**. This returns HTML content, through a function written in JavaScript.

React uses a **Virtual DOM**, that is, an in-memory representation of the DOM.

**STATUS:** each component has its own state. They communicate through a **global status**.

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
 
 fwfd
