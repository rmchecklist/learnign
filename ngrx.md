install ngrx => ng add @ngrx/store
install ngrx store devtools => ng add @ngrx/store-devtools


**Step 1: npm i --save @ngrx/store
Step 2: Create new file app.reducer.ts
```
export interface State {
    isLoading:boolean
}

const initialState: State = {
    isLoading: false
}

export appReducer(state = initialState, action){
    switch(action.type){
        case 'START_LOADING':
            return {
                this.isLoading = true;
            }
        case: 'STOP_LOADING':
            return {
                this.isLoading = false;
            }
        default: 
            return state;
    }

}
```
**Step 3: Import StoreModule in app.module.ts to access the reducer, and name the reducer to access from store

```
StoreModule.forRoot({ui: appReducer})
```

**Step 4: Dispatch an action - Inject Store from service

define store 

```
private store: Store<{ui: State -> type from reducer}>

this.store.dispatch({type: 'START_LOADING'}) => displatch function accepts type parameter type and payload(optional)
```

**Step 5: Subcribe from compoents
 
 declare Observable varialbe 
 
 ```
 isLoading$: Observable<boolean>;
 
 isLoading$ = this.store.map(state => state.ui.isLoading);
 
 on html use aync to subcribe 
 isLoading | async
 ```
 
 
 
 1. install ngrx store => npm i --save @ngrx/store@4
 2. install ngrx effects => npm i --save @ngrx/effects@4
 3. intall ngrx dev-tools => npm i --save @ngrx/store-devtools
 4. Add entry to app root module(app.module.ts)
     import StoreModule StoreEffects and StoreDevTools
         a. StoreModule.forRoot({reducer}| actionreducermap)
5. Install redux dev tools
6. Enable dev store tools
      a. import store dev tools => StoreDevToolsModule.instrument({maxAge: 25, logOnly:})  - MaxAge is no of snapshot    
      
7. Add ngstore to child module
        StoreModule.forFeature('reducer_name', reducer)
8. create reducer folder & index.ts
     define State type and include all reducer into ActionReducerMap
     
     ```
     export interface State {}
     export const reducers: ActionReducerMap<State>() = {
     };
     ```
9. Calling action using pipe
```
this.auth.login(user, email).pipe(
    tap(user => {
        console.log(user);
        
        this.store.dispatch({
            type: 'Login Action',
            payload: {
            }
        })
    })
)
```
10. Grouping action tupes
        create action.tyes.ts and export all action file
        
11. Create Module specific reducer and state definition
        ```
        export interface AuthState {}
        
        
        export const authReducer = createReducer(
            initialState,
            on(AuthAction.login, (state, action) => {
                return {
                    user: action.user
                }
            })
        )
        
        ```

12. Read data from store
   this.isLoggedIn$  = this.store.pipe(
   map(state => !!state["auth"].user)
   )
   
13. Optimize the value change emit

```
import {select} from '@ngrx/store'
 this.isLoggedIn$  = this.store.pipe(
   select(state => !!state["auth"].user) ==> eliminate duplicate emit
   )
```

14. Create selector this eliminate emiting unchanges state values

auth.selectors.ts ==> Momoized function

export const isLoggedIn = createSelector(
    state => state["auth"],
    (auth) => !!auth.user ==> result from 1st arg
)

15. Use select to access the value

this.isLoggedIn$ = this.store.pipe(
    select(isLoggedIn) ==> variable from step#14
)

16. reuse the selector to compute the values

from step#14

export const isLoggedout = createSelector(
    isLoggedIn
    (isLoggedIn) => !isLoggedIn ==> result from 1st arg
)


17. FeatureSelector, this will help to autocomplete the state variable(type safety)

on auth.selectors.ts 

```
export const selectAuthState = createFeature<AuthState>('auth')

after adding udpate  the below code 

export const isLoggedIn = createSelector(
    selectAuthState,
    (auth) => !!auth.user ==> result from 1st arg
)
```


18. Implementing auth gaurd and redirecting the page to login


inside canActivate function 

return this.store.pipe(select(isLoggedIn[selector]),

tap(logggedin => {
    if(!loggedIn){
        this.router.navigateByUrl('/login')
    }
}))


19. Effects

import effects module to root module

EffectsModule.forRoot([])

20. Add effects module to child module

EffectsModule.forFeature([])


21. Implementing sideeffects

create a file auth.effects.ts

```
import {Actions} from '@ngrx/effects'
@Injectable()
export class AuthEffects {
    constructor(private action$: Actions)
}
```
23. Add new AuthEffects class to auth module

EffectsModule.forFeature([AuthEffects])


24. Implementing side effects


const login$ = this.action$.pipe(
ofType() ==> denoted the action type,
tap(action => {
    implement the side effect here 
})
)


modifying above for stable elegant way to implememnt side effects and no longer need maunal subscription

**Stop the angular server when making effect changes to avoid browser crash


const login$ = createEffect(() => {
    
}, {dispatch: false}); ==> failure to add this line leads to infinite loop of calling this action


25. Ngrx developing tool
Ngrx Router store and Time travelling debugger
