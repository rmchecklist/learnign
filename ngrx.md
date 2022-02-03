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
 
 

