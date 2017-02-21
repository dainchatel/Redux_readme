## Redux

Dain Chatel, Jason Humphreys

Redux follows the uni-directional data flow model of Flux and stores state
in a singular object tree called a store rather than changing state via functions
within components.  The store contains the actions and reducer methods that have 
the ability to change the state.  Reducer methods are called on store.dispatch({}),
which signals that the state will be changed or that at least a reducer method
will be called.

So what's all that bullshit mean?  

1. Redux is a library that can be npm-ed or imported with a script tag. 
2. All of your state goes in a store.
3. You create a store like so:

```javascript
const { createStore } = Redux;
const store = createStore(counter);
```

> If you'd like to read your state, you would do so by calling: 

```javascript
    store.getState();
```

> If something in your app needs to change your state, you will need to call an 
action, by calling the .dispatch method with a type set to a string. This string is your action, and it will be passed as a parameter in the reducer function. (You have to create your actions in the store first, but you'll see how that looks in the step below). 

```javascript
    store.dispatch({
        type: "WHATEVER YOUR ACTION IS"
    })
```
> This action sets off a reducer method.  Below is an example of a simple
store where all of these concepts come together. (Note: this must be a pure function).

```javascript

const counter = (state = 0, action) => {
    switch (action.type) {
        //HERE ARE THE DIFFERENT ACTIONS AND WHAT THEY DO
        case 'INCREMENT':
            return state + 1;
        case 'DECREMENT':
            return state - 1;
        default:
            return state;
    }
}
```
> Once you change your store (state) you probably want to change stuff on your page to match the new state. To initiate UI changes after a state change, you use the store.subscribe() method to tell the component what to do once the state changes. 

```javascript
    store.subscribe(render);
```

That's it! (Kind of). Redux is a big, conceptual thing, and it has a lot to do with Flux. See these resources--especially the first tutorial--to get started using it:

>[Egghead Redux Tutorial](https://egghead.io/lessons/javascript-redux-the-single-immutable-state-tree)

>[Flux](https://github.com/facebook/flux)

>[Dan Abramov describes coming up with the idea for Redux](https://www.youtube.com/watch?v=xsSnOQynTHs)
