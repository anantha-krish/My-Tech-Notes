---
title: "Redux Notes"
tags: ""
---

# Redux Notes

Following are the notes for redux in react

## Start npm project

    npm init

## Install redux

    npm add redux

## Three concepts of redux

1.  Store : holds the state of ur action
2.  Action : describe the change in state of app
3.  Reducers: carries out state transition depending on action

## Redux pattern

The application can't update state directly.

1.  You have to dispatch an action (action contains the type)
2.  The action will be processed by reducer to update store.
3.  Update in the state is reflected to app as its subscribed.
4.  ![](image-keee20c5.png)

## Actions

-   json must contain a type key (field), and any no of fields u can add

```js
const BUY_CAKE='BUY_CAKE'
//function is called action creator
function buyCake()
{
  return {
      type:BUY_CAKE,
      info:'First action for redux'
  }
}
```

## Reducers

Reducer accepts the prevState & action -> return state variable based on action 

```js
const initialState =
{
    numberOfCakes:10
}

const reducers = ( state = initialState, action)=>{
  switch(action.type){
 //returning a new state object not mutating existing one
  case BUY_CAKE:return{
     //convention to make the copy of state & then modify the key 
      ...state,
      numberOfCakes: state.numberOfCakes - 1
  }
  default: return state  
}
}
```

## Store

-   step 1:
    Import redux library. Below is example for nodejs app

```js
const redux = require('redux')
const createStore = redux.createStore
```

-   step 2: 
    create a store

```js
const store = createStore(reducers)
```

-   step 3: access the state using get state

```js
console.log('Initial State',store.getState())
```

-   step 4: subscribe the app to the store 

```js
const unsubscribe = 
    store.subscribe( ()=> console.log('update state', store.getState() ))
```

-   step 5: dispatch actions to the store

```js
store.dispatch(buyCake())
store.dispatch(buyCake())
store.dispatch(buyCake())
```

-   step 6: unsubscribe the app

```js
//unsubscribe is variable declared in step 4
unsubscribe()
```

### OUTPUT

    PS D:\ReactProjects\redux-demo> node index.js
    Initial State { numberOfCakes: 10 }
    update state { numberOfCakes: 9 }
    update state { numberOfCakes: 8 }
    update state { numberOfCakes: 7 }
