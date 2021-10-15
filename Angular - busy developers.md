##### Structure of Angular projects

Angular projects
    - src
        - app
            - app.component.html
            - app.component.ts
            - app.moduel.ts
     - assets(Static files and images)
     - environement(Configuration setting for different env)
     - favicon.ico(favorite icon displayed on the home page)
     - index.html (basic html file, javascript and css files are loading dynamically)
     - main.ts(main file, starring point of application)
     - pollyfills.ts(fills the gap between angular and browser javascript)
     -style.css(global style for the application)
     - test.ts(settingup test env)
     - angular-cli.json(preconfigured confuration files)
     - editorconfig(all developer setting file)
     - gitignore(ignore some specific files)
     - karma.congf.js(test runner config file)
     - package.json
            - all dependent files 
            - devdependencies(required for developing the application in other way developer machine)
     - protractor.conf.js(configuration file for running end to end testing)
     - tsconfig.json(type script config file)
     - tslint.jspn(static analysis code typescript)
            
            
 - Components:
        - Create a component
        
![image](https://user-images.githubusercontent.com/5713791/137421194-5a07e70d-1108-483a-bd90-040f09970d03.png)
 
        - Register in a module
        
 ![image](https://user-images.githubusercontent.com/5713791/137421247-b04e97fe-e4f1-4261-8a7e-38f35a687678.png)

        - Add an element in a HTML markup
        
 ![image](https://user-images.githubusercontent.com/5713791/137421274-090a6480-e54e-4027-8ea1-7d0141901a2b.png)

- Generating component using angular CLI.
    - ng g c course

- Templates
        Values will binded in html using {{}} => String intepolation, we can call any javascript functions
        
![image](https://user-images.githubusercontent.com/5713791/137422144-fbc27115-e8fa-4882-8478-c4f6f7a0c822.png)
        
- Directives
    Whenever directives modifies the dom should be prefix with * i.e **ngFor
    
 - Services   
