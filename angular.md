##### What is angularjs?
     Javascript framework to create reactive single page applications.
     
     CLI - Command Line Interface tool.
     
###### Install angular on nodejs
  windows: npm install -g @angular/cli@latest
  mac: sudo npm install -g @angular/cli@latest

- Creating a new project
 ```
 ng new [project_name] --no-strict
 ```
 
- Start the server

```
ng serve
```

Package.json - contains all dependencies to run the angular application

Project Folder --> src --> app --> app.component.html

app component 
    template file - html
    styling - css
    typescript - .ts
        ```
        export class AppComponent {
          title = 'my app'
        }
        
        title can be used in html using {{title}} - binding
        ```
        
        @component({
           selector: 'app-root'
        })
        
        app-root tag is reads from index.html file
        
        directives: 
        ```
        <input type="text" [(ngModel)] = "name">
        <p>{{name}}</p>
        ```
       app.module.ts ==> import all neccessary lib
         ```
         import { FormsModule} from '@angular/forms'

         Add imports to imports

         imports: [
          FormsModule
         ]
         ```
   ###### Typescript
    - More features than vanilla JS(eg. Types, Classes, Interfaces)
    
    
  Use bootstarp as your css
  
  install bootstarp locally ==> npm install --save bootstarp3 ==>   moduel will be stored under npm_module
  
  update the styles in angular.json [architect-build -styles]
  
  update the path "node_modules/bootstarp/dist/css/bootstrap.min.css"
  

   
