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
        
    

