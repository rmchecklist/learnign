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

 #### linting => eslint needs to be updated when we have an component and directives naming conventions
 
 #### generate lib => npx nx g @nrwl/workspace:lib ui --dry-run

How call libraries:

1. Want to use component from lib always use path e.g. import { UiModule } from '@e-world/ui';
2. path will be defined in the tsconfig.base.ts under path, we can change the path as we want
3. Under path we will be using index.ts, where we mentioned all the export components, module, services
