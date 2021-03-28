# Introduction

All applications are run on browser, since reactjs is javascript it loads faster than normal html page, user don't have to wait(it's like a mobile app)

#### What is Reactjs?
    - A Javascript library for building user interfaces
    - Create components rather than creating entire page
    - Reactjs is all about component, this can reused and update semelessly 
    - Library for reactjs ==> react.js and react-dom.js(renderting the components into real dom)
    - Javascript compiler/preprocessor - Babel(compile next gen code into browser readable)
# html: 
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

Component should be created by fucntion as above and it is rendered by calling 

```
**ReactDOM.render(<[functionName]/>, document.querySelector('[id Name]'))**
```

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

ReactDOM.render(<Person name="Madhav" age="3"/>, document.querySelector('#p1'));

ReactDOM.render(<Person name="Elakya" age="32"/>, document.querySelector('#p2'));
```
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

ReactDOM.render(app, document.querySelector('#app'));
```
html:
```
<div id="app"></div>
```

Why React?

1. UI State becomes difficult to handle
2. Focus on business logic than how it is build

React Alternatives: 

1. Angular
2. React
3. Vue

2 kinds of applications
  - Single page application
  - Multi page application

## Next Gen Javascript

Code can be tested in [https://jsbin.com/](Jsbin)

1. let & const
    - let - variable values
    - const - constant, assign once and it cannot be changed
2. Arrow Functions
    ```
    Syntax:
        const myfunc = () => {}
        
        if one argumnent is passed:
        
            const myfunc = name => {} , this can also written as const myfunc = name => "name:"+ name(paranthisis, calibraces and return can be removed.
        
        more than 1 arg passed:
            const myfunc = (arg1, arg2) => {}
        
    ```
3. Exports & Imports (Modules)
```
const person = {
    name: 'Max'
}

export default person

import person from './person.js'
```

Default export 
    ```
    import person from './person.js'
    import prs from './person.js'
    ```
named export
```
    import {smth} from './person.js'
    import {smth as smth} from './person.js'
    import * as bundled from './utiltiy.js'
```

4. Classes

```
    class Person{
        name = "Max" --> Property
        call = () => {...} --> Function
    
    const myperson = new Person()
    myperson.call()
    console.log(myperson.name)
    }
    
    Class extends from another class
    
    class Person extends Master
```

Example of class:

    ```
    Class 1: Human
    
        class Human{
          constructor(){
            this.age = '3';
          }

          printMyAge(){
            console.log(this.age);
          }
        }
        
       class2: Person
       
       class Person extends Human{
          constructor(){
            super()
            this.age = '4' --> Alter the parent class attributes
            this.name = 'Madhav';
          }

          print_name(){
            console.log(this.name);
          }
        }
        
        const h = new Human();
        h.printMyAge(); 

        const p = new Person();
        p.print_name();
        p.printMyAge();
    ```
    
- When extends the class then should call super() from contructor()
- can access all properties of super class, using current class instance
        
    
5. Classes, Properties & methods
    - Propeties are attached the classes/Object
    - Methods are like functions attached to classes/objects
    
    ```
    - Properties:
    
    ES6:    
    constructor(){
        this.myprop = 'value'
    }
    
    ES7:    
    myprop = 'value'
    
    - Methods:
    
    ES6:
    mymethod(){
    }
    
    ES7:
    mymethod = () => {}
   
    
    
    ```
    
    ES7
        - Contructor can replaced by regular variable assignemnt
            - constructor(){this.name = "Madhav"} replaced by name = "Madhav"
            - No need to call super() on the constructor, directly access the parent class variable
        - method can be replaced by arrow function mymethod = () => {}
    
6. Spread & Rest Operators
        - Spread ==> Used to split up array elements OR object properties, denoted by [...]
           - const newArray = [...oldArray, 1, 2] ==> Extract the old array and add it to new array
           - const newObject = {...oldObject, newProp:5}  
           - e.g.
                -Array
                    const oldArray = [1,2,3,4];
                    const newArray = [...oldArray, 5, 6];
                    console.log(newArray);
                -Object
                    const person = { name: "Madhav"};
                    const newPerson = {...person, age:3}
                    console.log(newPerson);
                  
       - Rest ==> Used to merge a list of function argument into an array
            - function sortArgs(...args){ return args.sort()}
            e.g.
                const filter1 = (...args) => {
                  return args.filter(el => el === 1);
                } 
                console.log(filter1(2,3,4,5,6));
                
7. Destructuring
             - Easily extract array elements or object properties and store them in variables
                - Array destructuring
                    - [a, b] = ['Madhav', '3']    
                    
                    -   [a, b] = ['Madhav', '3'];
                        console.log(a, b); 
                -Object destructing
                        const {name, age } = {name:"Madhav", age:"3"};

                        console.log(a, age);  
                 
8. Reference and primitive type refreshers
        - Primitive types(All primitive data types) ==> Copy the value when we reassign the variable
            e.g.
                const number = 10
                const number2 = number
         - Reference(Object and Arrays) ==> Refence objects are reference to memory location
                const person = {name:"Madhav"};
                const person2 = person
                
                if you really want to copy of the object then use {...} 
                    e.g. const person2 = {...person}
                    
                        const person = {name: "Madhav"};

                        console.log(person.name);
                        const person2 = person; ==> Copy the object reference
                        const person2 = {...person}; ==> Copy the value

                        person.name = "Elakya";
                        console.log(person2.name); 

9. Refreshing array functions[map, filter, reduce]
    - Array map functions ==> Read all array and manupulate by map function
        ```
        - e.g. 
        - map
                const numarray2 = numarray.map(num => num *2);
                console.log(numarray);
                console.log(numarray2); 
        - filter
            - e.g. const numberarray = [1,2,3].filter(el = () => el === 1))
        - reduce
            - e.g. const result = numarray.reduce((acc, curr) => {
                      return acc+curr;  
                    });      
         ```
         
 # The Basics - All core react concepts
 
 create react app --> [https://github.com/facebook/create-react-app](Set up a modern web app by running one command)
 
 ## Install and create reactjs
 
 1. Install nodejs [https://nodejs.org/en/](Nodejs installation url)
 2. Install react ==> npm install create-react-app -g [-g install react globally on our local machine] 
 3. Create new react app ==> create-react-app [ap_name] --scripts-version 1.1.5
 4. Once project created, go application folder and then start the server by **npm start**
 5. Access the server using [http://localhost:3000/](React app local server)

## Understanding the folder structure

1. package.json 
    - dependecies ==> define the general dependencies [react, react-dom, react-scripts]
    - Scripts ==> start, build by running these commands through npm
2. node_modules ==> This will be created as part of the create app script, it contains all dependencies. Do not change/update this folder
3. public ==>
    - index.html ==> Contains root id and rendering all our components into this id, we don't create any other html file, all will be in javascript components
        - Add any libraries   
    - manifest.json ==> creates a meta-data for our application.
4. src
    - index.js ==> This will get access to index.html by accessing root element(id)
    - App.js ==> This is first react componented created by create-react-app script
    - App.css ==> styling used in App.js
    - index.css ==> used for global styling
 
## Understanding component basics

 1. index.js ==> Rendering the application components into root elememt which is defined in index.html
 2. App.js 
        - This should render html page from render method[class level component] or App function[functional level component] which return html 
            - class level component ==> class App extends Component { render(){return (JSX)};
            - functional level component ==> function App(){ return (JSX)}; 
            - export default App
 3. index.js
        - Import the app component by 
                ```
                import App from './App'
                ```
                
## Understanding JSX
    #### JSX:
```
    return (
        <div className="App">
          <h1>Hi, I'm a React App</h1>
        </div>
      );
```
   This can be translated into 
```
  return React.createElement('div', {className: 'App'},   React.createElement('h1', null, 'Does this work?'));
```
  Since it is cumbersome, we can use JSX code 
    
## JSX Restrictions

1. JSX looks like html file, class should be replaced by className becuase class is reversed keyword which will be used to create a classes

```
<div **className**="App">
  <h1>Hi, I'm a React App</h1>
</div>
```
2. JSX can have one root element, can't have mutiple
```
<div className="App">
  <h1>Hi, I'm a React App</h1>
</div>
~~<h1></h1>~~
```

## Creating a functional components(Components are core building blocks of React apps)

1. Create a new folder under src, best practice is to create a folder name starts with Uppercase, this would avoid any html tags e.g. Person

2. Create a js file Person.js(Naming convenstion first char should be Upper case)

3. Import React package
    - This will transform JSX into Javascript
    ```
    import React from 'react'
    ```
4. Create a function
```
const person = () => { return <p>I'm a Person</p>}
```
5. Export component
```
export default person
```
6. Use the functional component in App.js
    - import the Person components
        ```
        import Person from './Person/Person'
        ```
     - Use the person component like html element
        ```
        <Person />
        ```

### Functional vs Class based component
    - Functional component - Stateless component
        ```
        e.g.
        
        const cmp = () => { return <div>some JSX</div> }
       ```
    - Class bases component - Stateful component
    ```
    class Cmp extends Component { render () { return <div>some JSX</div> } }
    ```
    
   - Compoent dynamic content can placed by using {} e.g. Math.random()

## Working with props

 - When we have a component ready, then can pass the value through component tag and this will read by an argument in the component function(props)
 ```
 const person = (props) => {
    return <p>I'm {props.name} and I'm {props.age} old</p>
}

In App.js

<Person name="Madhav" age="3" />
 ```
 
 ## Understanding the children props
 
 - Any content between html element can be accessed by props.children. This can be any simple and complex html elements.
 ```
   <div>
        <p>I'm {props.name} and I'm {props.age} old</p>
        <p>{props.children}</p>
    </div>
 ```
 ## Understanding & using state
 
    - State can used in Class components which extend Component
        - state can be accessed by special variable **state**
        - e.g. state = { person: [{name:"MR", age:3}]}
        - access this variable by this.state.person[0].name
        - All class variable and method can access using this keyword.

## Props and State

 - Props ==> Can pass the data from parent compoent to child
    e.g.
    
    ```
    App.js(Parent component)
    
    <Person name="Madhav" age="3">
    
    Person.js(Child component)
    
    const person = (props) => {
        return (
            <div><p>{props.name}</p></div>
        );
    }
    ```
- State ==> State is used to change the component, and trigger an UI update

### Calling a function

- When call JSX function we should follow camelCase
  e.g. onClick={this.swithcNameHandler}
- JSX function should be case came e.g. onClick
- Calling name of the function by this.function_name
- Do not use paranthesis'()', if we use then function will be called at page loads
- best practice is to use Handler at end of the function.


### Manipulating the state

- Change the state of object can be acheived by **this.setState({})**;
- It just update the existing values and won't discard if any additioanl information what we are not updating as part of the setState 



