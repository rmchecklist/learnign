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

### useState() Hook for state manipulation for funcational based component

1. Change the app based component to functional based component
    ```
    const App = (props) => {}
    ```
2. Import UseState to achieve hook/user state
    ```
    import {useState} from 'react'
    ```
3. return JSX value

    ```
     return (<div className="App">
        <h1>Hi, I'm a React App</h1>
        <button onClick={swithNameHandler}>Switch Name</button>
        <Person name={personState.person[0].name} age={personState.person[0].age}  />
        <Person name={personState.person[1].name} age={personState.person[1].age}>My hobbies are: Watching TV</Person>
        <Person name={personState.person[2].name} age={personState.person[2].age}/>
      </div>);
    ```
4. use useState method to create state object 

    ```
    useState({
        person : [
        {name: "Madhav", age:3},
        {name: "Elakya", age:32},
        {name: "Ygnesh", age:34}
        ]});
    ```
5. useState method can return to objects, first args is current state and 2nd args is update state, Use destructing to assign the values
    
    ```
    const [personState, setPersonState] = useState({
        person : [
        {name: "Madhav", age:3},
        {name: "Elakya", age:32},
        {name: "Ygnesh", age:34}
        ]});
    ```
    
 6. In place of this.state use personstate[1st args from useState()]
 
 ```
 <Person name={personState.person[0].name} age={personState.person[0].age}  />
 ```
 
 7. When call the onClick method, use **swithNameHandler** inplace of **this.swithNameHandler**
 8. onClick Method can placed inside App method, update the state object using setPersonState method
    
    ```
    const swithNameHandler = () => {
        setPersonState({
          person : [
            {name: "Madhav Rengith", age:3},
            {name: "Elakya", age:32},
            {name: "RM", age:36}
          ]
        });
      };
    ```
 9. When you have multiple state values, we should update all when we update any specific state values
 
 ```
 Original Value:
 
 const [personState, setPersonState] = useState({
    person : [
    {name: "Madhav", age:3},
    {name: "Elakya", age:32},
    {name: "Ygnesh", age:34}
    ],
    otherState: ['some other value']
    });
    
 Updated value:
 
 setPersonState({
      person : [
        {name: "Madhav Rengith", age:3},
        {name: "Elakya", age:32},
        {name: "RM", age:36}
      ]
    });
    
 Here otherstate object values is not updated, so it will removed from udpated state value
 
 ```
 
 10. When you have multiple state values then create as much you need using userState

```
Original value:

const [personState, setPersonState] = useState({
    person : [
    {name: "Madhav", age:3},
    {name: "Elakya", age:32},
    {name: "Ygnesh", age:34}
    ] 
    });
  
  const [otherState, setOtherState] = useState({
    otherState: ['some other value']
  });
  
  
  updated value:
  
  setPersonState({
      person : [
        {name: "Madhav Rengith", age:3},
        {name: "Elakya", age:32},
        {name: "RM", age:36}
      ]
    });
    
 Since otherState object value is defined seperately, When we update setPersonState objcet, it won't affect the otherState object value   
```

### Passing method Reference between Components

1. When we want to add onClick function on the Person.js component, then we can pass the event name as props and access them from Person.js class

```
App.js

<Person name={this.state.persons[1].name} 
 age={this.state.persons[1].age}
 click={this.swithNameHandler}>My hobbies are: Watching TV</Person>
 
 Person.js
 
 <p onClick={props.click}>I'm {props.name} and I'm {props.age} old</p>
         

```

2. Click bind to add arguments to the function
```
<button onClick={this.swithNameHandler.bind(this, "Rengith")}>Switch Name</button>

swithNameHandler = (name) => {
      this.setState({
        persons : [
          {name: name, age:"3"},
          {name: "Elakya S", age:"32"},
          {name: "Ygnesh", age:"34"}
        ]
      })
  }
```

3. Pass the same arguments to child component(Person.js)
```
<Person name={this.state.persons[1].name} 
         age={this.state.persons[1].age}
         click={this.swithNameHandler.bind(this, "Madhav Rengith")}>My hobbies are: Watching TV</Person>
```
4. Instead of bind, we can use annoymouns function to achieve the same result
    - If possible use bind function than annoymous function, it faster rendering 
```
<button onClick={() => this.swithNameHandler("Elakya Sekar")}>Switch Name</button>
```
    
### Adding two way binding

- When input changed from child component and it should udpate from to parent compoent(update it's state)

```
App.js

<Person name={this.state.persons[0].name} 
 age={this.state.persons[0].age}  
 change={this.nameChangedHandler}/>
 
 nameChangedHandler = (event) => {
    this.setState({
      persons : [
        {name: event.target.value, age:"3"},
        {name: "Elakya S", age:"32"},
        {name: "Ygnesh", age:"34"}
      ]
    })
}

Person.js

<input type="text" onChange={props.change} value={props.name}/>

Browser throw warning message, when we have value without onChange event.

When the user inputs change, and it is automatically udpate the state and component

```

### Adding styling with Stylesheets

1. Add className on Person.js

```
<div className="Person">
    <p onClick={props.click}
    >I'm {props.name} and I'm {props.age} old</p>
    <p>{props.children}</p>
    <input type="text" onChange={props.change} value={props.name}/>
</div>
```
2. Create Person.css folder under Person folder
3. Add css style on Person.css

```
.Person {
    width: 60%;
    margin: auto;
    border: 1px solid #eee;
    box-shadow: 0 2px 3px #ccc;
    padding: 16px;
    text-align: center;
}
```

4. Import Person.css 

```
import './Person.css'
```

### Working with inline styles

- Add style class into CSS element, Since it is method level variable, we can directly call by the name, no need of this
```
<button 
  style={style}
  onClick={() => this.swithNameHandler("Elakya Sekar")}>Switch Name</button>
```

- Declare the style object inside the render() method
```
const style = {
      backgroundColor: 'white',
      font: 'inherit',
      border: '1px solid blue',
      padding: '8px',
      cursor: 'pointer'
    }
```


### Assignment#1
1. Create new project name called Assignment_1
```
create-react-app react_assignment_1
```
2. Start the server from application folder [react_Assignment_1]
3. Create two components: UserInput and UserOutput
```

```


### Useful Resources & Links

- create-react-app: https://github.com/facebookincubator/create-react-app
- Introducing JSX: https://reactjs.org/docs/introducing-jsx.html
- Rendering Elements: https://reactjs.org/docs/rendering-elements.html
- Components & Props: https://reactjs.org/docs/components-and-props.html
- Listenable Events: https://reactjs.org/docs/events.html

### Rendering the content conditionally

- we have ternary oprator to conditionally display the content

```
<div>
{ this.state.showPerson ? 

<Person
    name={person.name}
    age={person.age}
    key={person.id}
    click={() => this.deleteNameHandler(personIndex)}
  />

     <Person
        name={person.name}
        age={person.age}
        key={person.id}
        click={() => this.deleteNameHandler(personIndex)}
      />
              
              <Person
                name={person.name}
                age={person.age}
                key={person.id}
                click={() => this.deleteNameHandler(personIndex)}
              />
              
} : null
<div>
```

### Handling dynamic content "The Javascript way"

- create a person object and initialize to null and if state.showPerson object is true and then add person component to persons obeject

```
let persons = null

if(this.state.showPerson){
    if (this.state.showPerson) {
      persons = (
        <div>
          {this.state.persons.map((person, personIndex) => {
            return (
              <Person
                name={person.name}
                age={person.age}
                key={person.id}
                click={() => this.deleteNameHandler(personIndex)}
              />
            );
          })}
        </div>
      );
    }

}
```

- This snippets will be called inside the render(), anytime state object changes render method will be trigger automatically, persons object will initialize to null and then set the value based upon the showPersons value

### Outputting list

- Render the component by using list 

```
 {this.state.persons.map((person, personIndex) => {
            return (
              <Person
                name={person.name}
                age={person.age}
                key={person.id}
                click={() => this.deleteNameHandler(personIndex)}
              />
            );
          })}
```

### List and State

- We can click handler the delete person componet

```
 deleteNameHandler = (personIndex) => {
    //  const persons = this.state.persons;
    // const persons = this.state.persons.slice();
    const persons = [...this.state.persons];
    persons.splice(personIndex, 1);
    this.setState({ persons: persons });
  };
```

### Updating state immutably

--When we mutate the state we should copy the state object and then update, several ways to do these
     - Use slice() method to create a copy of the array
     - user spread(ES6)

```
deleteNameHandler = (personIndex) => {
    //  const persons = this.state.persons;
    // const persons = this.state.persons.slice();
    const persons = [...this.state.persons];
    persons.splice(personIndex, 1);
    this.setState({ persons: persons });
  };
```

### List and Keys

- all componet should have unique key value to identify the previous component

```
<div>
          {this.state.persons.map((person, personIndex) => {
            return (
              <Person
                name={person.name}
                age={person.age}
                key={person.id}
                click={() => this.deleteNameHandler(personIndex)}
              />
            );
          })}
```
### Flexible list

- Since we used list iteration to populate the component, now we are going to update the input element and change it respective element than all, Here are the steps

1. Add change event to Person component

```
 <Person
                name={person.name}
                age={person.age}
                key={person.id}
                click={() => this.deleteNameHandler(personIndex)}
                change = {(event) => this.swithNameHandler(event, person.id)}
              />
```
    - We are passing event and person.id to identify the current value change and respective component(by person.id)
        -need to use ES6 function to pass the event and person.id or else use bind function to achieve this
        ```
        change = {(event) => this.swithNameHandler(event, person.id)}
        ```
2. Create a switchNameHandler function

```
 swithNameHandler = (event, personId) => {

    const personIndex = this.state.persons.findIndex(p => {
      return p.id === personId;
    })

    const person = {...this.state.persons[personIndex]};

    person.name = event.target.value;

    const persons = [...this.state.persons];
    persons[personIndex] = person;

    this.setState({persons:persons})
    }
```
2.1 find the current component index(person index) using person.findIndex

```
const personIndex = this.state.persons.findIndex(p => {
      return p.id === personId;
    })
    This will return current person index 
```
2.2 Copy of the person by using person index, using ES7 spread to take the copy of the object

```
const person = {...this.state.persons[personIndex]};
```
2.3 Update the person name 

```
person.name = event.target.value;
```
2.4 Spread(Copy) the current state object

```
const persons = [...this.state.persons];
```
2.5 Update the current person to persons object
```
persons[personIndex] = person;
```
2.6 Update the state object

```
this.setState({persons:persons})
```

## Assignment#2

1. Create an input field (in App component) with a change listener which outputs the length of the entered text below it(e.g. in a paragraph)

1.1 Create a new project and start the app
```
create-react-app assignment_2
cd create-react-app assignment_2
npm start
```
1.2 Import useState from react

```
import {useState} from 'react';
```

1.3. Create a useState of maintaining the state of input field length

```
 const [currentState, updateState] = useState({
    inputFieldTextLength : 0
  })
  
```
1.4 Add onChange event and add state variable to paragraph

```
<div className="App">
  <input type="text"
    onChange={(event)=>{textChangeHandler(event)}}
  />
  <p>Entered Text length: {currentState.inputFieldTextLength}</p>
</div>
```
1.5 Create onChange handler method textChangeHandler 

```
  const textChangeHandler = (event) => {
      updateState({
        inputFieldTextLength : event.target.value.length        
      });
  }
```
2. Create a new component(=> Validation component) which receives the text length as prop
3. Inside the validation component either output "Text long enough" or "Too short" depending on the text length(e.g. take 5 as min length

2.1 Create validation component, set the paragraph value based upon the input field text

```
const Validation = (props) => {
    let textSize = null;

    if(props.Size > 5){
        textSize = "Text too long";
    }else
    {
        textSize = "Text too short";
    }
    return (
        <p>Current Field Text length is: {textSize}</p>
    );
}
```
2.2 Add validation component to App component

```
return (
    <div className="App">
      <input type="text"
        onChange={(event)=>{textChangeHandler(event)}}
      />
      <p>Entered Text length: {currentState.inputFieldTextLength}</p>

      <Validation Size={currentState.inputFieldTextLength}/>
    </div>
```
4. Create another component(=> CharComponent) and style it is an inline box

```
import React from 'react';
import './Char.css';

const Char = (props) => {
    return(
        <div className="Char" onClick={props.click}>
            <p>{props.Text}</p>
        </div>
    );
}

export default Char;

Char.css

.Char {
    display: inline-block;
    padding: 16px;
    text-align: center;
    margin: 16px;
    border: 1px solid black;
}

```
5. Render a list of Char components where each Charcomponent receives a different letter of the entered text (in the initial input field) as a prop

```

return (
    <div className="App">
      <input type="text"
        onChange={(event)=>{textChangeHandler(event)}}
        value = {currentState.inputFieldText}
      />
      <p>Entered Text length: {currentState.inputFieldTextLength}</p>

      <Validation Size={currentState.inputFieldTextLength}/>
      
      {box}

    </div>
  );
  
  
  let box = null;

  const textChar = currentState.inputFieldText.split('');
  box = textChar.map((t, id) => { 
    return (<Char 
      key={id}
      Text={t} 
      click={()=>{removeBox(t)}}/>); ==> Split the current string object, this would convert to array and then using map function to create Char component
  });
  
  
  const textChangeHandler = (event) => {
      updateState({
        inputFieldTextLength : event.target.value.length, --> When type the text on text field, udpate the state using updateState object
        inputFieldText: event.target.value     
      });
  }
  
```

6. When you clikc a Charcomponent it should be removed from the entered text 

```
const removeBox = (text) => {
    if(text.length > 0){
      const fieldTxt = [...currentState.inputFieldText]; --> Use Spread to copy the state object
      const findIndex = fieldTxt.findIndex((t) => { --> Return the index of the selected text box
        return text === t;
      })
      console.log("Test1==>"+fieldTxt)
      const fieldText = fieldTxt.slice(0, findIndex) + fieldTxt.slice(findIndex+1); - Remove the current selected text 
      
      ## Alternatively we can use 
      
      const fieldText = currentState.inputFieldText.split('') ==> Char Array
      fieldText.splice(findIndex, 1) ==> Remove the char from indexed position
      const updatedText  = fieldText.join(''); ==> Join all the char and converts to string
      
      
      console.log("Test=>"+fieldText.replaceAll(',', ''));

      updateState({
        inputFieldText: fieldText.replaceAll(',', '') --> Update the state with replacing ',' with ''   
      });

    }
  }
  
```

### Useful Resources & Links

- Conditional Rendering: https://reactjs.org/docs/conditional-rendering.html
- Lists & Keys: https://reactjs.org/docs/lists-and-keys.html


# Styling React components & elements

1. Outlining the problem set
     - There are many limitation on the inline styling and also create any styling on the component css file might affect the global styling

2. Setting Styles Dynamically
  
- Since all codes are in Javascrpit we can call the variable name to set the colors dynamically

```
const style = {
      backgroundColor: "green",
      color: 'white',
      font: "inherit",
      border: "1px solid blue",
      padding: "8px",
      cursor: "pointer",
    };
    
if (this.state.showPerson) {
      persons = (
        <div>
          {this.state.persons.map((person, personIndex) => {
            return (
              <Person
                name={person.name}
                age={person.age}
                key={person.id}
                click={() => this.deleteNameHandler(personIndex)}
                change = {(event) => this.swithNameHandler(event, person.id)}
              />
            );
          })}
        </div>
      );
      style.backgroundColor = 'red';
    }

```

3. Setting Class Names Dynamically
    - creating classes variable, and push styles based upon the conditions.
    - On the className, we should add .join(' ') make this object to string to add all styles with space 

```
let classes = [];

if(this.state.persons.length >= 2){
  classes.push('red');
}

if(this.state.persons.length <= 1){
  classes.push('bold');
}

<p className={classes.join(' ')}>This is really working!</p>
```
4. Adding and using Radium
    - Adding button hover won't be added through inline styling, since it isn't CSS property we can't integrate the styling, in order to do that we need to use third party package which is radim
    - Installing radium

```
npm install --save radium
```
- import Radium on App.js
- Enclose the App component with higher order component Radium

```
import Radium from 'radium';
export default Radium(App);
```
     - Now all sudo selector from css can be accessed through Radium package, but we need to add in quotes

```
render() {
    const style = {
      backgroundColor: "green",
      color: 'white',
      font: "inherit",
      border: "1px solid blue",
      padding: "8px",
      cursor: "pointer",
      ':hover': {
        backgroundColor: 'lightgreen',
        color: 'black'
      }
    };
    
    
    style.backgroundColor = 'red';
      style[':hover'] =  {
        backgroundColor: 'salmon',
        color: 'black'
    
    
```

5. Using Radium for Medial Queries

 - Create a const syle variable

```
const style = {
        '@media (min-width: 500px)': {
            width: '450px'
        }
    };
```

- add style to person component

```
return (
        <div className="Person" sytle={style}> 
            <p onClick={props.click}
            >I'm {props.name} and I'm {props.age} old</p>
            <p>{props.children}</p>
            <input type="text" onChange={props.change} value={props.name}/>
        </div>
    );
```
- On app component, import named component StyleRoot and wrap the entire component

```
import Radium, { StyleRoot } from 'radium';
 <StyleRoot>
 </StyleRoot>

```

6. Styled components
 - https://styled-components.com/ 

   - install styled-components 
    -  npm install --save styled-components

    - import styled components

```
import styled from 'styled-components';

create a style variable back tik(`)==> template literal

const StyledDiv = styled.div`
    width: 60%;
    margin: 16px;
    border: 1px solid #eee;
    box-shadow: 0 2px 3px #ccc;
    padding: 16px;
    text-align: center;

    @media (min-width: 500px) {
        width: '450px'
    }
`;

Add styled component in place of div
//<div className="Person" sytle={style}> 
        <StyledDiv>
            <p onClick={props.click}
            >I'm {props.name} and I'm {props.age} old</p>
            <p>{props.children}</p>
            <input type="text" onChange={props.change} value={props.name}/>
        </StyledDiv>
```
  
 7. More on styled component
 - add styled-component style to button

```
const StyledButton = styled.button`
  background-color: green;
  color: white;
  font: inherit;
  border: 1px solid blue;
  padding: 8px;
  cursor: pointer;
  &:hover {
    background-color: lightgreen;
    color: black;
  }
`;


<StyledButton onClick={this.togglePerson}>
          Toggle Person
        </StyledButton>
        
        
```

8. Styled component and Dynamic styles

- add conditional style using props

```
<StyledButton alt={this.state.showPerson} ==> This the property use to conditionally format the style
          onClick={this.togglePerson}>
          Toggle Person
        </StyledButton>
        
        
        
 const StyledButton = styled.button`
  background-color: ${props => props.alt ? 'red' : 'green'}; ==> Pass the property handle the styling conditionally
  color: white;
  font: inherit;
  border: 1px solid blue;
  padding: 8px;
  cursor: pointer;
  &:hover {
    background-color: ${props => props.alt ? 'salmon': 'lightgreen' };;
    color: black;
  }
`;

```

9. Working with CSS modules

Below steps for older versions:


- In order to use CSS modules, you need to do the following steps to achieve this
    - eject the under the hood configuration

```
Stop the server 

Ctrl+C

execute eject command 

npm run eject
```

New version:

1. Rename the css file into [Component name].[moduel].css e.g. Person.module.css
2. Import the css by 

```
import classesStyle from "./App.module.css";
```
3. Declare btnclass variable 

```
 let btnClasses = [classesStyle.Button];
```
5. update the button element 

```
<button className={btnClasses.join(' ')} 
          alt={this.state.showPerson}
          onClick={this.togglePerson}>
          Toggle Person
        </button>
```
6. Update the conditional block style

```
btnClasses.push(classesStyle.Red);
```

7. App.module.css 

```
.App {
  text-align: center;
}

.red {
  color:red;
}

.bold {
  font-weight: bold;
}

.Button {
  background-color: green;
  color: white;
  font: inherit;
  border: 1px solid blue;
  padding: 8px;
  cursor: pointer;
  
}

.Button:hover {
  background-color: lightgreen;
    color: black;
}

.Button.Red {
  background-color: red;
}

.Button.Red:hover {
  background-color: salmon;
}
```

### More on CSS modules

 - When we have classes defined in css module file, we can call the classed as below
 ```
 App.module.css
.Button {
  background-color: green;
  color: white;
  font: inherit;
  border: 1px solid blue;
  padding: 8px;
  cursor: pointer;
  
}

.Button:hover {
  background-color: lightgreen;
    color: black;
}

.Button.Red {
  background-color: red;
}

.Button.Red:hover {
  background-color: salmon;
}

App.js

import the classes by using import statement

import classesStyle from "./App.module.css";

use the app module by using 

<div className={classesStyle.App}>

In order to use conditional statement, declare the variable array inside the render()


let btnClasses = [classesStyle];

push the red class if records exists

 btnClasses.push(classesStyle.Red);
 
 <button className={classesStyle.Button} 
          alt={this.state.showPerson}
          onClick={this.togglePerson}>
          Toggle Person
        </button>
 ```
 
  - Altenatively we can append the App on the css module class

```
App.module.css

.App button {
  background-color: green;
  color: white;
  font: inherit;
  border: 1px solid blue;
  padding: 8px;
  cursor: pointer;
  
}

.App button:hover {
  background-color: lightgreen;
    color: black;
}

.App button.Red {
  background-color: red;
}

.App button.Red:hover {
  background-color: salmon;
}

App.js

So everything inside the App[CSS class] can directly used the button element classes

declare a empty array 

let btnClasses = [];

conditional statement use module class name to assign the class

btnClasses = classesStyle.Red;

<button className={btnClasses} 
          alt={this.state.showPerson}
          onClick={this.togglePerson}>
          Toggle Person
        </button>
```
  
### CSS modules & Media queries

- media queries can be used by css module, that way we can seperate javascript and css codes.
- More on css modules https://github.com/css-modules/css-modules


```
Example:

In Post.css File

.Post {
    color: red;
}
In Post Component File

import classes from './Post.css';
 
const post = () => (
    <div className={classes.Post}>...</div>
);
```

- Here, classes.Post  refers to an automatically generated Post  property on the imported classes  object. That property will in the end simply hold a value like Post__Post__ah5_1 .

So your .Post  class was automatically transformed to a different class (Post__Post__ah5_1 ) which is unique across the application. You also can't use it accidentally in other components because you don't know the generated string! You can only access it through the classes  object. And if you import the CSS file (in the same way) in another component, the classes  object there will hold a Post  property which yields a different (!) CSS class name. Hence it's scoped to a given component.

By the way, if you somehow also want to define a global (i.e. un-transformed) CSS class in such a .css  file, you can prefix the selector with :global .

Example:

:global .Post { ... } 

Now you can use className="Post"  anywhere in your app and receive that styling.


### Useful Resources & Links

- Using CSS Modules in create-react-app Projects: https://medium.com/nulogy/how-to-use-css-modules-with-create-react-app-9e44bec2b5c2
- More information about CSS Modules: https://github.com/css-modules/css-modules

### Debugging React Apps

##### Understanding error messages

- Looking at the errors, and read the top most eror logs from browser console

##### Finding logical errors by using dev tools & sourcemaps

- Debug the code try to find the object attributes, if any attributes are not find then fix the issues and rerun the application.

##### Working with React developer tools

- Install React developer tools
    -    install tool from chrome web store :: https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en
    -    Run the react application and click on component from dev tool(more >> Components)
    -    we can change the attribute name and props

##### Using Error Bountaries(React 16+)

-- Error boundaries are useful when you know you can't handle the error on the runtime.

Steps to setup Error boundaries

1. Create ErrorBoundary class

```
class ErrorBoundary extends Component {
    state = {
        hasError: false,
        errorMessage: ''
    }

    componentDidCatch = (error, info) => {
        this.setState({
            hasError: true,
            errorMessage: error
        })
    }

    render(){
        if(this.state.hasError){
            return <h1>{this.state.errorMessage}</h1>;
        }else{
            return this.props.children;
        }
    }
}

export default ErrorBoundary;
```
- we neeed to have a state to maintain the error state and message
- override the componentDidCatch method, which can pass error and info to this method
- render error message if there is an erro
- Or else render this.props.children

- Import the ErrorBoundary into App component
    - Wrap the ErrorBoundary component into Person component
    - Add key attribute into outer component 

- When there is a error occured on the person component that will translate to ErrorBounday

```
App.js

return (
      <ErrorBoundary key={person.id}><Person
        name={person.name}
        age={person.age}
        click={() => this.deleteNameHandler(personIndex)}
        change = {(event) => this.swithNameHandler(event, person.id)}
      />
      </ErrorBoundary>
      
Person.js  

const number = Math.random();

if(number > 0.7){
    throw new Error('Something went wrong');
}
```

#### Useful Resources & Links
Error Boundaries: https://reactjs.org/docs/error-boundaries.html
Chrome Devtool Debugging: https://developers.google.com/web/tools/chrome-devtools/javascript/

# Drving deeper into Components and React internals

 - Better project structure

1. Create components folder to keep all comoponents into it, if there is any list componentsm then keep component inside the list comp

```
Components
        -->Persons
                --> Person
```

2. Create assets folder to keep all images 
3. Create Container folder to move all App.js related files (App.js, App.css, App.test.js)

##### Section 9: Driving deeper: working with Fragments, Portals & "Ref"
    
1. JSX Limitation
    - All component are wrapped by root element, wraping component will leads to mutiple <div>, this may affect/break the css stying     
2. Creating a wrapper component
    - Creating Wrapper component without JSX code and it return just 
    - This wrapper component can be replaced by <div> root components
    - Empty wrapper component, it doesn't render any real HTML elements to the DOM. But it fulfills React's/JSX element.    

```
const Wrapper = (props) =>{
    return props.children;
};

export default Wrapper;

```

3.React Fragments

 - Intead of Wrapper component, alternatively use empty tag(<></>), if it doesn't work then use <React.Fragment></React.Fragment>
 - If you import Fragment then we can use <Fragment></Fragment>

```
Option#1 ==> <></>
Option#2 ==> <React.Fragment></React.Fragment>
Option#3 ==> import {Fragment} from 'react' <Fragment></Fragment>
```
##### 4. Introducing React Portals
      - Portal can remove <div> soup issue, we can render the element inside the body without any nested element on it.

          1. Created div element on public/index.html 

```
  <div id="backdrop-root"></div>
    <div id="overlay-root"></div>
    <div id="root"></div>
```
        2. create backdrop and model overlay compoment and add them using portal 
```
import Card from '../Card/Card';
import Button from '../Button/Button';
import classes from './ErrorModal.module.css';
import reactDom from 'react-dom';

const Backdrop = props => {
    return 	<div className={classes.backdrop} onClick={props.onConfirm}/>;
};

const ModelOverlay = props => {
    return (
        <Card className={classes.modal}>
                <header className={classes.header}>
                    <h2>{props.title}</h2>
                </header>
                <div className={classes.content}>
                    <p>{props.message}</p>
                </div>
                <footer className={classes.actions}>
                    <Button onClick={props.onConfirm}>Okay</Button>
                </footer>
            </Card>
    );
};


const ErrorModal = (props) => {
    return(
        <>
           {reactDom.createPortal(<Backdrop onConfirm = {props.onConfirm}/>, 
           document.getElementById("backdrop-root"))} 
           {reactDom.createPortal(<ModelOverlay title = {props.title} message = {props.message} 
                    onConfirm = {props.onConfirm}/>, 
                    document.getElementById("overlay-root"))}
        </>      
    );
};

export default ErrorModal;
```

##### 5. Working with ref

1. Import named component 

```
import React, { useRef} from 'react';
```

2. Initialize ref

```
const userRef = useRef();
const ageRef = useRef();
```

3. Input element has ref as attribute, you can use this to read the input value

```
<input id="age" type="number" ref={ageRef}  />
```
4. On click on Add user event handler read the input value from ref object

```
const userRefVal = userRef.current.value;
const userAgeVal = ageRef.current.value;
```

5. Reset  the user enter value after click on Add user

```
userRef.current.value = '';
ageRef.current.value = '';
```
##### 5. Controlled vs Uncontrolled components

 - Controlled components are controlled by react when we use state object, component will be controlled by React
 - Uncontrolled components are not controlled by React, for example when we use ref these are native element and update this will not be controlled by react.


### Section 10: Advanced: Handling side effects, using reducers & Context

###### 1. What are "Side effects & introducing useEffect"
        useEffect can be used execute the code specific to state change, it would avoid the infinite loop if any state object changes.
        
syntax:
        
```
useEffect(()=> {
   
  }, []);
```
   
if we add any variable inside the method, can be executed once or dependencies changed([])

```
import React, { useState, useEffect } from 'react';

import Login from './components/Login/Login';
import Home from './components/Home/Home';
import MainHeader from './components/MainHeader/MainHeader';

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  useEffect(()=> {
    console.log('use Effect');
    const storedUserLogInInfo = localStorage.getItem('isLoggedIn');

    if(storedUserLogInInfo === '1'){
      setIsLoggedIn(true);
    }
  }, []);

  const loginHandler = (email, password) => {
    // We should of course check email and password
    // But it's just a dummy/ demo anyways
    localStorage.setItem('isLoggedIn', '1');
    setIsLoggedIn(true);
  };

  const logoutHandler = () => {
    setIsLoggedIn(false);
    localStorage.removeItem('isLoggedIn');
  };

  return (
    <React.Fragment>
      <MainHeader isAuthenticated={isLoggedIn} onLogout={logoutHandler} />
      <main>
        {!isLoggedIn && <Login onLogin={loginHandler} />}
        {isLoggedIn && <Home onLogout={logoutHandler} />}
      </main>
    </React.Fragment>
  );
}

export default App;

```
###### 2. useEffect & Dependencies

- when we add dependencies, useEffect will execute if these variables are changed

```
useEffect(()=>{
      setFormIsValid(
        enteredEmail.includes('@') && enteredPassword.trim().length > 6
      );
    }, [enteredEmail, enteredPassword]);

  const emailChangeHandler = (event) => {
    setEnteredEmail(event.target.value);

    
  };
```  
###### 3. Using the useEffect cleanup function

- useEffect has 2 args fucntion and dependencies, in our example we don't want to check for every key stroke instread use setTimeout function to limit the validation and also call return from function this can be annoymous function, which can execute every time(not first time). In this example we can clear the identifier variable for every time it hits.
```
useEffect(()=>{
    const indentifier = setTimeout(()=> {
      console.log('checking validity');
      setFormIsValid(
        enteredEmail.includes('@') && enteredPassword.trim().length > 6
      );
    }, 500);  
    
    return () => {
      console.log('CLEANUP');
      clearTimeout(indentifier);
    }

    }, [enteredEmail, enteredPassword]);
```

###### 4. useEffect Summary

- useEffect will execute whenever changes in the dependencies
- loads once if there is no dependencies
- cleanup function can be configured for element removal and call before the executes

- The below code will execute after every components rendered.(Every action/Key stroke)
```
useEffect(()=> {
    concole.log('Effect running');
})
```
- Execute for first time not for every render[added empty dependency args]
```
useEffect(()=> {
    concole.log('Effect running');
}, [])
```
- Eexcutes for every password keystroke

```
useEffect(()=> {
    concole.log('Effect running');
}, [enteredPassword])
```
- Cleanup function can be called before state funcation not first time
```
useEffect(()=> {
    concole.log('Effect running');
   return ()=>{console.log('clean up')} 
}, [enteredPassword])
```
- Cleanup function executes, when DOM removed


##### 5. Indroducing useReducer & Reducers in General
 - combine enteredEmail, validateEmail into one, so entered value and validate email Can be one single state that can achieve through reducers

###### 6. Using the useReducer() Hook

- Syntax

```
const[state, dispatchFn] = useReducer(reducerFn, initialState, initFn);

state - state snapshot, values will reads from state object
dispatchFn - update the state 

reducerFn - get the latest state snapshots, get the action it dispatched and update the new state

inititalState - 
initialFn - 
```

- Steps to use useReducer

1. import useReducer 

```
import {useReducer} from 'react';
```

2. Initialize the useReducer

```
const [emailState, dispatchEmail] = useReducer(emailReducer);

~ dispatchEmail 

~ emailReducer(can be defined outside of functional component, all the information required for emailReducer will passed as args) are functions
    - emailReducer will accept 2 argument last state snapshot and action that was dispatched by dispatchEmail
~ inittialState
```

3. define emailReducer function, action argument will be supplied by dispathEmail Funcation

```
const emailReducer = (state, action) => {
  if(action.type === 'USER_INPUT'){
    return {value:action.val, isValid: action.val.includes('@')};   
  }

  if(action.type === 'INPUT_BLUR'){
    return {value:state.value, isValid: state.value.includes('@')};
  }

   return {value:'', isValid: false};
};
```
4. declare dispatchEmail

```
dispatchEmail({type: 'USER_INPUT', val: event.target.value});
```

- Take Away:
    - use same state object key for example, this will used in {type: 'USER_INPUT', val: event.target.value} email reducer action


5. When you use useEffect, make sure we are adding correct depency to load render at the minimal

for eg.

```
const {isValid: emailValid} = emailState;
  const {isValid: passValid} = passwordState;
  useEffect(()=>{
    const indentifier = setTimeout(()=> {
      console.log('checking from validity');
      setFormIsValid(
        emailValid && passValid
      );
      // dispatchEmail({type: 'USER_INPUT', val: emailState.value});
      // dispatchPassword({type: "PSWD_INPUT", val: passwordState.value});
    }, 500);  
    
    return () => {
      console.log('cleanup')
      clearTimeout(indentifier);
    }

    }, [emailValid, passValid]);
```

On above instead of using emailValidState object,we can use isValid method to extract emailValid and passValid, so that when it satisfy the condition and if we add any further char won't change the state and it won't render again.

###### 6. useReducer vs useState for state management

1. useState
    -   The main state management tool
    -   Great for independent pieces of state/data
    -   Great if state updates are easy and limited to a few kinds of updates

2. useReducer
    - Great if you need more power
    - should be considered if you have related pieces of state/data
    - can be helpful if you have more complex state updates

##### 7. Introducing React context(Context AP)

-- Mangaring the state through props, can lead to uncessarry state management

![image](https://user-images.githubusercontent.com/5713791/115080746-451fd680-9ed1-11eb-8e96-ee16ee2fe78e.png)

##### 8. Using the React Conext API

In order to access the context object, we need to follow the below steps

1. Create AuthContext component

```
import React from 'react';

const AuthContext = React.createContext({
    isLoggedIn: false
});

export default AuthContext;
```

2. Wrap the compoent with AuthContext provider

```
App.js
return (
    <AuthContext.Provider value={{isLoggedIn: isLoggedIn}}>
        <MainHeader onLogout={logoutHandler} />
        <main>
          {!isLoggedIn && <Login onLogin={loginHandler} />}
          {isLoggedIn && <Home onLogout={logoutHandler} />}
        </main>
      </AuthContext.Provider>
  );
```

3. Wrap the componet with AuthContext.Consumer
    - We can access the ctx using anonymous function inside AuthContext.Consumer

```
const Navigation = (props) => {
  return (
    <AuthContext.Consumer>
      {
        (ctx) => {
          return (
            <nav className={classes.nav}>
              <ul>
                {ctx.isLoggedIn && (
                  <li>
                    <a href="/">Users</a>
                  </li>
                )}
                {ctx.isLoggedIn && (
                  <li>
                    <a href="/">Admin</a>
                  </li>
                )}
                {ctx.isLoggedIn && (
                  <li>
                    <button onClick={props.onLogout}>Logout</button>
                  </li>
                )}
              </ul>
            </nav>
          );
        }
      }
      
    </AuthContext.Consumer>
  );
};
```

##### 9. Tapping into Context with the useContext Hook

- Instead of using AuthContext.Provider and Consumer, we can use useContext named component 

Steps to use:

1. import useContext from react
2. read the context from useContext

```
ctx = useContext(AuthContext);
```

3. Use ctx from #2, AuthContext object can be accessed through this

```
import React, {useContext} from 'react';

const Navigation = (props) => {

  const ctx = useContext(AuthContext);
  return (
    <nav className={classes.nav}>
      <ul>
        {ctx.isLoggedIn && (
          <li>
            <a href="/">Users</a>
          </li>
        )}
        {ctx.isLoggedIn && (
          <li>
            <a href="/">Admin</a>
          </li>
        )}
        {ctx.isLoggedIn && (
          <li>
            <button onClick={props.onLogout}>Logout</button>
          </li>
        )}
      </ul>
    </nav>
  );
};
```

###### 10. Making context Dynamic

also pass the handler to useContext, do not include paratheseis [()]
```
Apps.js

return (
    <AuthContext.Provider 
      value={
        {isLoggedIn: isLoggedIn,
          onLogout: logoutHandler
        }}>
        <MainHeader onLogout={logoutHandler} />
        <main>
          {!isLoggedIn && <Login onLogin={loginHandler} />}
          {isLoggedIn && <Home onLogout={logoutHandler} />}
        </main>
      </AuthContext.Provider>
  );
  
  Navigation.js
  
  const Navigation = (props) => {

  const ctx = useContext(AuthContext);
  return (
    <nav className={classes.nav}>
      <ul>
        {ctx.isLoggedIn && (
          <li>
            <a href="/">Users</a>
          </li>
        )}
        {ctx.isLoggedIn && (
          <li>
            <a href="/">Admin</a>
          </li>
        )}
        {ctx.isLoggedIn && (
          <li>
            <button onClick={ctx.onLogout}>Logout</button>
          </li>
        )}
      </ul>
    </nav>
  );
};
```
###### 11. Building & using a custom context provider component

1. create dedicated component for login and logout

```
auth-context.js

import React, { useState, useEffect } from 'react';

const AuthContext = React.createContext({
    isLoggedIn: false,
    onLogout: () => {},
    onLogin: (email, password) =>{}
});


export const AuthContextProvider = (props) => {
    console.log('AuthContextProvider');
    const [isLoggedIn, setIsLoggedIn] = useState(false);

    useEffect(()=> {
        console.log('use Effect');
        const storedUserLogInInfo = localStorage.getItem('isLoggedIn');
    
        if(storedUserLogInInfo === '1'){
          setIsLoggedIn(true);
        }
      }, []);

    const onLogoutHandler = () => {
        localStorage.removeItem('isLoggedIn');
        setIsLoggedIn(false);
    };

    const loginHandler = () => {
        localStorage.setItem('isLoggedIn', '1');
        setIsLoggedIn(true);
    };

    return <AuthContext.Provider value={
        {isLoggedIn: isLoggedIn, onLogout: onLogoutHandler, 
            onLogin: loginHandler}
    }>{props.children}</AuthContext.Provider>;
}

export default AuthContext;

```

2. Wrap the app component with AuthContext.Provider named component

```
index.js

import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import { AuthContextProvider } from './store/auth-context';

ReactDOM.render(
<AuthContextProvider><App /></AuthContextProvider>
//<App />
, document.getElementById('root'));
```

3. Remove the all the login/logout functionalilty from App.js, use context to access the state object

```
App.js

import React, {useContext} from 'react';

import Login from './components/Login/Login';
import Home from './components/Home/Home';
import MainHeader from './components/MainHeader/MainHeader';
import AuthContext from './store/auth-context';


function App() {
  console.log('App component');  
  const ctx = useContext(AuthContext);
    
    return (
      <React.Fragment>
           <MainHeader onLogout={ctx.onLogout} />
          <main>
            {!ctx.isLoggedIn && <Login />}
            {ctx.isLoggedIn && <Home />}
          </main>
        </React.Fragment>
  );
}

export default App;
```
4. Similarly update the code to all other components


###### 12. React context limitations

1. Context can be used application wide state management where props can be used for reusable component
2. Context is not optimized for high frequency changes
3. There is an alternative which is Redux

##### 13. Rules of Hooks

###### 1. Only call React Hooks in React Function component(which is return JSX) and custom Hooks
###### 2. Only call React Hooks at the Top Level(do not call in any conditional statement or loop or any other internal methods)
###### 3. Rule for useEffect(): Always add everything you refer to inside of useEffect() as a dependency


###### 14. Refactoring an input component

1. Create an input component

```
Input.js

import React from 'react';
import classes from './Input.module.css';

const Input = (props) => {
    return (
        <div
          className={`${classes.control} ${
            props.isValid === false ? classes.invalid : ''
          }`}
        >
          <label htmlFor={props.id}>{props.label}</label>
          <input
            type={props.type}
            id={props.id}
            value={props.value}
            onChange={props.onChange}
            onBlur={props.onBlur}
          />
        </div>
    );
};

export default Input;
```

2. Reuse in Login.js, we are using props on reusable components, so that we can configure for each compoennt, if we use context then functionality is same and it cannot be changed for individual component needs

```
<Input 
            id="email" 
            label="E-Mail" 
            type="email" 
            isValid={emailValid} 
            value={emailState.value}
            onChange={emailChangeHandler}
            onBlur={validateEmailHandler}
            />
            <Input 
            id="password" 
            label="Password" 
            type="password" 
            isValid={passValid} 
            value={passwordState.value}
            onChange={passwordChangeHandler}
            onBlur={validatePasswordHandler}
            />
```
##### 14. Diving into Forward Refs

 - Steps to use Forward Refs

1. Import useRef  
2. Create a ref attribute on Input element
3. In order to use this ref from login.js(outside of its component
4. Import useImperativeHandle and define them inside input component
        - this will accept 2 args
            - 1. ref which will be passed from input component args, in order to pass we need to wrap with React.forwardRef
            - 2. method which can return the object, map the function name which can be called from outide

```
Input.js

import React, {useRef, useEffect, useImperativeHandle} from 'react';
import classes from './Input.module.css';

const Input = React.forwardRef((props, ref) => {
    const inputRef = useRef();

    //useEffect(()=> {inputRef.current.focus();}, []);

    const activate = () => {
        inputRef.current.focus();
    };

    useImperativeHandle(ref, () => {
        return {
            focus: activate
        };
    })
    return (
        <div
          className={`${classes.control} ${
            props.isValid === false ? classes.invalid : ''
          }`}
        >
          <label htmlFor={props.id}>{props.label}</label>
          <input
            ref={inputRef}
            type={props.type}
            id={props.id}
            value={props.value}
            onChange={props.onChange}
            onBlur={props.onBlur}
          />
        </div>
    );
});

export default Input;
```

5. Import useRef on login.js

```
import React, { useState, useEffect, useReducer, useContext, useRef } from 'react';
```
6. declare useRef for each input element email and password

```
const emailRef = useRef();
const passRef = useRef();
```
7. On Submit call the ref based upon the condition to focus

```
const submitHandler = (event) => {
    event.preventDefault();
    if(formIsValid){
      authCtx.onLogin(emailState.value, passwordState.value);
    }else if(!emailValid){
        emailRef.current.focus();
    }else{
      passRef.current.focus();
    }
    
  };
```
8. Here we are using focus method from useRef hook which is exposed to outside component using imperativeHandle and React.forwardRef on Input component
9. This can usefull for focusing and scrolling and avoid for all other purposes.


##### Food Order app

###### 1. Download the resources and extrace them
###### 2. inside the project app run `npm install` and `npm start`
###### 3. Create some of the folder to organize the component
            - components --> folders which holds all the components
            - UI --> All sytle related component can be placed here
            - Meals --> Meal component have list of meals
            - Layout --> hold all layout related components
            - Cart --> Cart related components
###### 4. Working on Header Component

    - Create Header component under Layout
        - Header.js and Header.module.js
    - It can contain Header cart and image
        - Image can be import from assets folder, syntax of this image import as mentioned below
```
import mealsImage from '../../asserts/meals.jpg';

<img src={mealsImage} alt="A table of full delicious food" />
```     
    - Import the css class, if there is any '-', then we should use [] to reference
```
<div className={classes['main-image']}>
```
    - Import the Header component into App

```
import React, {Fragment} from 'react';
import Header from './components/Layout/Header';

function App() {
  return (
    <Fragment>
      <Header />
    </Fragment>
  );
}

export default App;
```

###### 5. Adding the "Cart" Button component

1. Create a HeaderCartButton component, try to add image and name and badge

```
import CartIcon from '../Cart/CartIcon';
import classes from './HeaderCartButton.module.css';

const HeaderCartButton = props => {
    return(
        <button className={classes.button}>
            <span className={classes.icon}>
                <CartIcon />
            </span>
            <span>
                Your cart
            </span>
            <span className={classes.badge}>
                3
            </span>
        </button>
    );
}

export default HeaderCartButton;
```
2. Use CartIcon component in HeaderCartButtom component to import image
    - Create CartIcom component, this will create JSX file which include svg icon

```
const CartIcon = () => {
    return (
      <svg
        xmlns='http://www.w3.org/2000/svg'
        viewBox='0 0 20 20'
        fill='currentColor'
      >
        <path d='M3 1a1 1 0 000 2h1.22l.305 1.222a.997.997 0 00.01.042l1.358 5.43-.893.892C3.74 11.846 4.632 14 6.414 14H15a1 1 0 000-2H6.414l1-1H14a1 1 0 00.894-.553l3-6A1 1 0 0017 3H6.28l-.31-1.243A1 1 0 005 1H3zM16 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM6.5 18a1.5 1.5 0 100-3 1.5 1.5 0 000 3z' />
      </svg>
    );
  };
  
  export default CartIcon;
```
3. Import HeaderCartButton in Header component

```
import { Fragment } from 'react';
import mealsImage from '../../asserts/meals.jpg';
import classes from './Header.module.css';
import HeaderCartButton from './HeaderCartButton,';

const Header = props => {
    return (
        <Fragment>
            <header className={classes.header}>
                <h1>ReactMeals</h1>
                <HeaderCartButton />
            </header>
            <div className={classes['main-image']}>
                <img src={mealsImage} alt="A table of full delicious food" />
            </div>
        </Fragment>
    );
};


export default Header;
```

##### 6. Adding a "Meals" Component

1. Create 3 components 
    - Meals ==> Combine MealsSummary and AvailableMeals
    - MealsSummary ==> Have static text 
    - AvailableMeals ==> List of available meal and transform the test data into jsx

###### 7. Adding Individual Meal Items & Displaying them

###### 8. Adding a Form


# Things to remind for building projects

1. useState
2. useEffect
3. useContext
4. useReducer


## A look behind the scenes of React & Optimization techniques


##### How does React work?

 ![image](https://user-images.githubusercontent.com/5713791/115616792-9b6c8b00-a2be-11eb-843b-3d68ee4cd343.png)

![image](https://user-images.githubusercontent.com/5713791/115617495-74628900-a2bf-11eb-9e0b-1ee2321e82a8.png)

###### Preventing Unneccessary Re-Evaluations with React.memo()

 - useCallback - wrap handler method to useCallback, this will store function into React storage and reuse for subsequent execution.

- We can use React.memo() to reload the components based upon the props value
- But if compoonent used event handler then it is reload everytime, in order avoid this we can use useCallback to copy the variable

```
const toggleParagraphHandler = useCallback(() => {
    setShowParagraph()
}, [])
```

###### useCallback() and its dependencies

```
const toggleParagraphHandler = useCallback(()=>{
    if(allowToggle){ ==> This is variable which is used outside of the function
        setShowParagraph((prevShowPragraph) => ~preShowParagraph);
    }
}, [allowToggle]);

```
- allowToggle state changes, then button will retrigger, if we are not adding dependencies then it never going to be retriggered because functions are constant and values are closure within the function.



##### State update and scheduling

![image](https://user-images.githubusercontent.com/5713791/115760476-69673180-a36f-11eb-8844-5fce2c0df29c.png)

useMemo to memorize the data


###### An Alternative way of building components: class based components

#### Sending Http request:


```
const response = await fetch('https://swapi.dev/api/films'); --> Call api using fetch(inbuild javascript function) and make them async
    const data = await response.json(); --> await to return the response in json
    const tranformedMovies = data.results.map(movieData => {
          return {
            id: movieData.episode_id,
            title: movieData.title,
            openingText: movieData.opening_crawl,
            releaseDate: movieData.release_date
          };
        });
        setMovies(tranformedMovies);
        setLoading(false);
```

##### Dealing with form submission and user input values

- useRef, useState

Approch#1: Want to capture and validate on each key stroke then use onChange function and update the state value on every key stroke


Approach#2: Want to validate the entered value at the time of submission then use useRef

```
import { useState, useRef } from 'react';

const SimpleInput = (props) => {
  const [enteredName, setEneteredName] = useState('');
  const inputNameRef = useRef();

  const inputChangeHandler = event => {
    setEneteredName(event.target.value);    
  }

  const onSubmitHandler = event =>{
    event.preventDefault();
    console.log(enteredName);
    console.log(inputNameRef.current.value);
  }

  return (
    <form onSubmit={onSubmitHandler}>
      <div className='form-control'>
        <label htmlFor='name'>Your Name</label>
        <input ref={inputNameRef} type='text' id='name' onChange={inputChangeHandler}/>
      </div>
      <div className="form-actions">
        <button>Submit</button>
      </div>
    </form>
  );
};

export default SimpleInput;

```

##### Rest the input value

Approach#1: use set state to reset the value - Ideal Approach
Approach#2: use Ref varialbe to reset the value - This is not the ideal approach to change the dom value, let react take care of it.

- Input validation should on onBlur, OnSubmission and onChange
- 

##### Third party form lib FORMIK, this can avoid using custom hooks and easy to use complex forms validations.

https://formik.org/


##### useState() vs useReducer()

![image](https://user-images.githubusercontent.com/5713791/116470282-34f8e700-a841-11eb-8963-c79cadc51d5c.png)


#### REDUX

- A state management system for cross-component or app-wide state

![image](https://user-images.githubusercontent.com/5713791/117085478-e56e5b80-ad17-11eb-9a21-20bc966f493e.png)

![image](https://user-images.githubusercontent.com/5713791/117085873-02575e80-ad19-11eb-8412-1cf41eb4a6d1.png)

![image](https://user-images.githubusercontent.com/5713791/117086932-06d14680-ad1c-11eb-809b-6a066d3625c7.png)



##### Exploring the core Redux

- Create a empty folder
- run 'npm init -y'
- install redux 'npm install redux'
- create demo.js file(redux-demo.js)


![image](https://user-images.githubusercontent.com/5713791/117152597-2b630800-ad88-11eb-9c4e-11b5b883b1bc.png)
1. include redux by using require('redux')
2. create reducer funcation which can accept current state, and action

```
const counterReducer = (state = {counter:0}, action) => {
    return {
        counter: state.counter +1 
    }
};
```
3. create redux store which can accept reducer

```
const store = redux.createStore(counterReducer);
```
4. need a subscriber method to access the store

```
const counterSubscriber = () => {
    const latestState = store.getState();
    console.log(latestState);
}
```
5. subscribe the function

```
store.subscribe(counterSubscriber);
```

6. dispatch the function

```
store.dispatch({type:'increment'});
```

###### React redux

1. install redux and react-redux package on the application
    - npm install redux react-redux 
    - create redux store component
    - wrap them in root component which is app component
    
```
import React from "react";
import ReactDOM from "react-dom";
import { Provider } from "react-redux";
import "./index.css";
import App from "./App";
import store from "./store/index";

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById("root")
);
```
- useSelector to subcribe the component and read the specific compoent
 
 
 ```
 import classes from "./Counter.module.css";
import { useSelector, useDispatch } from "react-redux";

const Counter = () => {
  const dispatch = useDispatch();
  const counter = useSelector((state) => state.counter);
  const toggleCounterHandler = () => {};

  const incrementHandler = () => {
    dispatch({type: 'INCREMENT'});
  }

  const decrementHandler = () => {
    dispatch({type: 'DECREMENT'});
  }
  return (
    <main className={classes.counter}>
      <h1>Redux Counter</h1>
      <div className={classes.value}>{counter}</div>
      <div><button onClick={incrementHandler}>Increment</button>
      <button onClick={decrementHandler}>Decrement</button></div>
      <button onClick={toggleCounterHandler}>Toggle Counter</button>
    </main>
  );
};

export default Counter;

 ```
 
 #### Redux on class level component
 
 ```
 import classes from "./Counter.module.css";
import { useSelector, useDispatch, connect } from "react-redux";
import { Component} from 'react';

// const Counter = () => {
//   const dispatch = useDispatch();
//   const counter = useSelector((state) => state.counter);
//   const toggleCounterHandler = () => {};

//   const incrementHandler = () => {
//     dispatch({type: 'INCREMENT'});
//   }

//   const decrementHandler = () => {
//     dispatch({type: 'DECREMENT'});
//   }
//   return (
//     <main className={classes.counter}>
//       <h1>Redux Counter</h1>
//       <div className={classes.value}>{counter}</div>
//       <div><button onClick={incrementHandler}>Increment</button>
//       <button onClick={decrementHandler}>Decrement</button></div>
//       <button onClick={toggleCounterHandler}>Toggle Counter</button>
//     </main>
//   );
// };

const mapStateToProps = state => {
  return {
    counter: state.counter
  };
}

const mapDispatchToProps = dispatch => {
  return {
    increment: ()=> dispatch({ type: 'INCREMENT'}),
    decrement: ()=> dispatch({ type: 'DECREMENT'}),
  }
}

class Counter extends Component {

  decrementHandler(){
    this.props.decrement();
  }

  incrementHandler(){
    this.props.increment();
  }

  toggleCounterHandler(){

  }

  render(){
    return (
      <main className={classes.counter}>
      <h1>Redux Counter</h1>
      <div className={classes.value}>{this.props.counter}</div>
      <div><button onClick={this.incrementHandler.bind(this)}>Increment</button>
      <button onClick={this.decrementHandler.bind(this)}>Decrement</button></div>
      <button onClick={this.toggleCounterHandler}>Toggle Counter</button>
    </main>
    );
  };

  
};

export default connect(mapStateToProps, mapDispatchToProps)(Counter);
// export default Counter;

 ```

###### Redux dev tools

#### Deploying react apps


###### Deploying Steps

- Test code
- Optimize code(use react memo to avoid unneccsary redering
- Build App for production
- Upload production code to server
- Configure Server


##### Lazy loading ==> Load code only when it's needed

#### Building  code for production

- On package.json ==> we have the script ready server start, build, test and eject
- for building use `npm run-script build`

##### Hosting static website

Follow this link for google firebase

https://console.firebase.google.com/u/0/project/react-app-7828a/hosting/sites



