# Introduction

All applications are run on browser, since reactjs is javascript it loads faster than normal html page, user don't have to wait(it's like a mobile app)

#### What is Reactjs?
    - A Javascript library for building user interfaces
    - Create components rather than creating entire page
    - Reactjs is all about component, this can reused and update semelessly 
    - Library for reactjs ==> react.js and react-dom.js(renderting the components into real dom)
    - Javascript compiler/preprocessor - Babel(compile next gen code into browser readable)

    
    
    
    html: 
    ```
    <div id="p1"></div>

    <div class="person">
      <h1>Elakya</h1>
      <p>You age: 32</p>
    </div>
    ```
    java script:
    ```
    function Person(){
      return (
        <div class="person">
          <h1>Madhav</h1>
          <p>You age: 3</p>
        </div>
      );
    }
    ```

    Return text from person method will be transformed into Javascript.
    
    ReactDOM.render(<Person/>, document.querySelector('#p1'));

    Component should be created by fucntion as above and it is rendered by calling **ReactDOM.render(<[functionName]/>, document.querySelector('[id Name]'))**
    
    
    User can pass the argument by passing name and age(from above snippets)
    
   
    Javascript:
    ```
    function Person(props){
      return (
        <div className="person">
          <h1>{props.name}</h1>
          <p>You age: {props.age}</p>
        </div>
      );
    }
 ```
ReactDOM.render(<Person name="Madhav" age="3"/>, document.querySelector('#p1'));

ReactDOM.render(<Person name="Elakya" age="32"/>, document.querySelector('#p2'));

html:
 ```
<div id="p1"></div>

<div id="p2"></div>
```

To simplify, create app componment and add all person component into it

Javascript:
 ```
var app = (
  <div>
    <Person name="Madhav" age="3"/>
    <Person name="Elakya" age="32"/>
  </div>
);
 ```
ReactDOM.render(app, document.querySelector('#app'));

html:
 ```
<div id="app"></div>
 ```


