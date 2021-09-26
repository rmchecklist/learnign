###### Installing and exploring nodejs

- Install nodejs ==> [https://nodejs.org/en/]

- After the installation, check the version in terminal by typing 
```
node -v
``` 
- Install javascript IDE 
      -  Visual studio code
      - Webstorm

#### What is nodejs?
        - Nodejs is a server side javascript, you can write code like any other program, before nodejs, javascript can be run in the browser.
        - nodejs is a javascript runtime built on Chrome v8 javascript engine

 - How javascript runs?
![image](https://user-images.githubusercontent.com/5713791/132272340-8de95c18-e31f-45c1-81cc-f2e9f7119b71.png)

V8 javascript engine is written in C++

- write all commands we type in browser console can be write in node console, access node, type node on the terminal
- some of the commands are specific to the browser similarly node, e.g. windows object can be accessed from the browser console, but can't be accessed from node
- global can be accessed from node, but not in browser
- window and browser - browser-related object
- global  and process - node related object


####### Why should I use nodejs?

 - Perform non blocking I/O(call functions are non blocking function, it move forward with the next operation while current is on progress)
 
![image](https://user-images.githubusercontent.com/5713791/132384850-a5481605-3926-4d00-8af9-9bfa51ec8f72.png)

- Nodejs uses an event-driven, non-blocking I/O model that makes it light weight and efficient
- search npm package on [nodejs.com]

#### Your first nodejs script

- Create a js file and write console.log('test')
- run through command prompt by node file_name

##### Nodejs module system
   - import code nodejs core modules
   - fs.writeFileSync('file_name', 'text') - on order to execute this, we need to install the code modules.

```
const fs = require('fs')
fs.writeFileSync('test.txt', 'safasffsa')
```
for more information about file system, please refer to this link - [https://nodejs.org/dist/latest-v16.x/docs/api/fs.html]

```
Appending a text 

const fs = require('fs')
fs.appendFileSync('test.txt', 'appending new text', (e) => {
if (err) throw err;
    console.log('The "data to append" was appended to file!');
  });
```

Course material course video - [https://github.com/andrewjmead/node-course-v3-code]


##### import your files

- use require to load the external js file

```
require('./util.js')
```

##### Install npm package 

```
npm install [package name] or npm i [package name] - package name can be found in npmjs.com

no es6 

const validator = require('validator')

es6

import validator from 'Validator'

const validator = validator.isEmail('test@email.com')
```


#### Install nodemon

```
npm install nodemon -g (-g install globally not specific to applicaiton), this helps to execute automatically for any changes.

nodemon [file_name]
```

##### Read argument from command line
```
process.argv --> Read the argument from command line argv - argument vector
```

#### intall yargs

Yargs helps you build interactive command line tools, by parsing arguments and generating an elegant user interface

#### Json parsing and stringify

```
JSON.stringify(JSON object) ==> Parse JSON object into string
JSON.parse(string) ==> Parse String into JSON object

```
