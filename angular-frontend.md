1. Install nx => npm i -g nx
2. Install VS code extensions
    1. Angular Language service
    2. Prettier code formatter
    3. Bracket pair colorizer
    4. CSS navigation

### Create nx workspace 
  npx create-nx-workspace --preset=angular
  
  
running the application:
=> nx serve e-shop 


Create new app => nx generate @nrwl/angular:app e-shop-admin

create component using nx => nx g component --project=e-shop (if want to run it in dry run mode append --dry-run at end of the syntax)

 # linting => eslint needs to be updated when we have an component and directives naming conventions
 
 # generate lib => npx nx g @nrwl/workspace:lib ui --dry-run
