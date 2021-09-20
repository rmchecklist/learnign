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
          

*ngFor
          ```
          <p *ngFor="let logItem of log; let i = index" [ngStyle]="{backgroundColor: i > 4 ? 'blue' : 'green'}" >{{logItem}}</p>
          ```
        
Creating a component without test file
          ```
          ng g c comp_name --skip-Tests true
          ```
          
#### Custom binding or passing value from parent to children
```
 app.component.ts
          
          serverElements = [{name:'server', type: 'Test Server', content: 'Just a test'}];
app.component.html
          <app-first-comp *ngFor="let element of serverElements" [element]="element"></app-first-comp>

first.component.ts
          import { Component, Input, OnInit } from '@angular/core';
          declare inside the class:
          @Input() element!: { name: string; type: string; content: string; };
first.component.html
          <p>first-comp works!</p>
          <p>{{element.name}}</p>
          <p>{{element.type}}</p>
          <p>{{element.content}}</p>
```
If you want to use alias on the external variable, need to declare @Input('alias_name')and need to use alias name to bind the object, in this scenario original object variable  will not work.       
          
#### Component communication
          
##### Custom binding receiving value from children to parent
  
```
          app.component.ts --> Reading count from child component
          
          onServerAdded(serverCount: {count: number}){
              console.log(serverCount.count);
            }
          
          app.component.html => serverCreated will be referenced in child component and onServerAdded will be defined in app.component.html
          
          <app-server-element (serverCreated)="onServerAdded($event)"></app-server-element>
          
          server.component.ts
          
          export class ServerElementComponent implements OnInit {
            names: number[] = [];
            @Output() serverCreated = new EventEmitter<{count : number}>();
            constructor() { }

            ngOnInit(): void {
            }

            onClickHandler(){
              this.names.push(this.names.length+1);
              this.serverCreated.emit({count: this.names.length});
            }

          }
          
          server-element.component.html
          
          <button (click)="onClickHandler()">Add Server</button>
          
          
```
 #### Local References
```
         any.component.html
          
          <input type="text" #serverName value="text" />
          <button (click)="onClickHandler(serverName)">Add Server</button>
          
          any.component.ts
          
          onClickHandler(serverName : any){
              console.log(serverName);
              this.names.push(this.names.length+1);
              this.serverCreated.emit({count: this.names.length});
            }
```
          
#### Getting access to the template & DOM with @ViewChild
          
          ```
   server.component.html     

          <input type="text" #serverNameViewChild value="text" />
          
     server.component.ts
          import { Component, EventEmitter, OnInit, Output, ViewChild } from '@angular/core';

          @ViewChild('serverNameViewChild' , {static:true}) serverNameViewChild : any;
          
          onClickHandler(serverName : any){
              console.log(this.serverNameViewChild);
            }
          
          Read direct value from @ViewChild
          
          @ViewChild('serverNameViewChild', { static: true })
          serverNameViewChild!: ElementRef;
          
          console.log(this.serverNameViewChild.nativeElement.value);
          ```
ng-content ==> Replace any content insider the component 
          
         ```
          .html
          <ng-content></ng-content>
          
          from parent html:
          
          <app-server-element>
              Hello How are you? ==> This content appened on the <ng-content> area
          </app-server-element>
          ```
               
#### Component lifecyle[https://angular.io/guide/lifecycle-hooks]
               
   ![image](https://user-images.githubusercontent.com/5713791/133895721-96fb11a4-8b2d-49ee-aa1e-0ad5c9eae6b5.png)

     
- constructor : Wil be called at the time of compoent creation
- ngOnInit() - Called once the component is initialized
- ngOnChanges - called when property changed from parent component
- ngDoCheck - Check/detected any changes
- ngAfterContentInit() - Called one afer the content initialized
- ngAfterContentChecked() - called after ngAfterContentInit and every subsequent changes
- ngAfterViewInit() - Called once after the first ngAfterContentChecked().
- ngAfterViewChecked() - Called after the ngAfterViewInit() and every subsequent ngAfterContentChecked().
- ngOnDestroy() - Called immediately before Angular destroys the directive or component.


               
#### Deep dive Directives

##### Creating our own directive
               
1. Create directive ts file
```
import { Directive, ElementRef, OnInit } from "@angular/core";

@Directive({
    selector: '[appBasicHighlight]'
})
export class BasicHighlighterDirective implements OnInit {

    constructor(private elementRef:ElementRef){

    }

    ngOnInit(){
        this.elementRef.nativeElement.style.backgroundColor = 'green'
    }
}
```
               
2. Use this directive on the app component (basic directive)
               
```
app.module.ts add directive into it
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';
import { AppComponent } from './app.component';
import { FirstCompComponent } from './first-comp/first-comp.component';
import { ServerElementComponent } from './server-element/server-element.component';
import { ComplifecyleComponent } from './complifecyle/complifecyle.component';
import { BasicHighlighterDirective } from './basic-highlighter/basic-highlighter-directive';

@NgModule({
  declarations: [
    AppComponent,
    FirstCompComponent,
    ServerElementComponent,
    ComplifecyleComponent,
    BasicHighlighterDirective,
  ],
  imports: [
    BrowserModule,
    FormsModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
               
               
app.component.html
               
<p appBasicHighlight>Hello This is the first directive</p>
```

##### Better directive 
```        
betterdirective.directive.ts
               
import { Directive, ElementRef, OnInit, Renderer2 } from '@angular/core';

@Directive({
  selector: '[appBetterhighlighter]'
})
export class BetterhighlighterDirective implements OnInit {

  constructor(private eleRef:ElementRef, private renderer : Renderer2) { }

  ngOnInit(){
    this.renderer.setStyle(this.eleRef.nativeElement, 'backgroundColor', 'blue')
  }
}
               
app.component.html
               
<p appBetterhighlighter>Hello This is the first directive</p>
               
```
