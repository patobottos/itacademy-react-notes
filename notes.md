# NOTES ON REACT

React és una llibreria de JavaScript, per dur a terme interfícies d'usuari (UI). Va ser llançada per FAcebook l'any 2013.

Els **components** poden **reutilitzar-se** i **combinar-se**. Els components són objectes de JavaScript.

Com es vincula JavaScript i HTML? Amb una sintaxi, anomenada **JSX**. Aquesta torna contingut HTML, a través d'una funció escrita en JavaScript.

React fa servir un **Virtual DOM**, és a dir, una representació del DOM en memòria.

**ESTADO:** cada componente tiene su propio estado. Se comunican a través de un **estado global**.

### **COMPONENTS**

They are the building blocks of any react application. A typical web in React might be made with several components, where components are self contained sections of contents. For example, a nav-bar, an article, a side-bar, in a website might be a component. Our mission i sto build these components and rendered them into the webpage, by React. 

Components contain: 
1) template 
2) logic

JSX syntax allows us to easily create the HTML style-like templates in components: but, though tt seems HTML, it has little differences. In the background, it transpiles this JSX into HTML, and renders this HTML to the DOM. 
One main difference: in JSX we use the keyword **"className"**, camel case, and when it converts into HTML it turns into **"class"**.

A component is, basically, a function. At the end of the file, we export it. For example:

    import './App.css';
    
    function App() {
      return (
        <div className="App">
          <div className="content">
           <h1>App Components</h1>
          </div>
        </div>
      );
    }
    
    export default App;"

Go on.
