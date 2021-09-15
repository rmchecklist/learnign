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
  

#### How angular works?

main.ts -->AppModule app.module.ts (@NgModule bootstrap: [AppComponent] -->app.component.ts(@Component selector: app-root --> app-root defined in the index.html

###### Creating component[Manual]:
   - All the component should be created under the app folder, each component should created under folder
          e.g. creating server component
               server
                 server.component.ts
                 ```
                         import {Component} from '@angular/core';
                         
                         @Component({ - Decorator from typescript
                              selector: 'app-server' ==> Starts with app and followed by component name
                              templateURL: app.component.html => This is html file for this app component, name of the temple url should be app.component.html
                         })
                         export class ServerComponent { ==> since component will be used in the other module this has be exported to resue
                         }
                         
                         To use component, we need to update app.module.ts file.
                    ```
                    
                    
#### Use custom component

- use custom component, we need to register in app.module.ts 


@NgModule(){
     declarations: [
          ServerComponent,
     ]
     
Add the component tag in app.component.html to use them.

###### Creating component[CLI command]:
```
ng generate component servers or ng g c server
```
html code can written inside the app.component.ts file

```
@NgModule({
     selector: 'app-servers',
     template: `<app-server><app-server>`, => multiline use backtik(`)
     
})
```

#### Using styling component

@Component({
     styingURL: ['./app.component.css'] => styling from external file
     stying: [`
          h3: {
          color: darkblue`}
          ] => inline styling
})


selector can be use as attribute selector by using square brackets [] => selector: [app-server]

<div app-server>
     
use as class 
     selector: '.app-server'
     <div class='app-server'>
          
          Selecting by id is not supported by angular
          

##### Databinding
          
          1. String interpolation ( {{}} )
          
                    You use method which returns string or regular String variable or String value
 ```                        e.g 
                              String value ==> {{'Status'}}
                              String variable ==> {{ status}}
                              method ==> {{getStatus()}}
   ```       
 2. Property binding([] = ""):
    
```
          allowServerAccess = false;
          
          constructor(){
               setTimeOut(()=> {
               this.allowServerAccess = true;
          },2000)
                
          
          On Html 
          
          <button class="btn btn-primary" [disabled]="!allowNewServer"></button>
  ```   

3. Event binding( (event) ):
          <button (click)="onCreateServer()"}>Add Server</button>
          
          onCreateServer() will be declared in component.ts file
          
4. Two way binding(FormModule is required for 2 way binding)
          For 2 way binding, we need to import FormModule in app.module.ts and add the them to imports []
          
```
          app.module.ts
          
          import { FormsModule } from '@angular/forms';
          
          imports: [
             FormsModule
            ],
          <input [(ngModel)] = "serverCreated" />
```
#### Directives
          *ngIf -> Strutural directives, display the content conditionally, otheres are attribute directives
          ```
          <p *ngIf="buttonClicked">{{serverCreated}}</p>
          ```
          
          *ngif else:
          
          <p *ngIf="buttonClicked else noServer">{{serverCreated}}</p>
          <ng-template #noServer>
              <p >No Server was created</p>
          </ng-template>
          
#### Structural vs Attribute directives
          Unlike structural directives, attribute directives don't add or remove elements. They only change the elements they were places on.
          
          
ngStyle is an attribute directive 
          ```
         <p *ngIf="buttonClicked else noServer" [ngStyle] = "{backgroundColor: getServerStatus()}">{{serverCreated}}</p> 
          ```
ngClass
       Add classes based upon the condition   
          <p [ngClass] ="{online:serverCreated}">This is ngClass demo</p> 
          
