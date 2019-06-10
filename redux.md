### Redux
[react-redux tutorial](https://daveceddia.com/redux-tutorial/)
- Redux holds the State of React, which is called the "Store".
- The "State" is the data and the "Store" is where it is kept.
- You need to create the store to hold the state.
- Redux comes with a handy function that creates the store for you called ```js const store = createStore();```.
- Then you add createStore as an import : ```js import { createStore } from 'redux'; ```.
- We have to make a function that will return a state:
  ```js 
  function reducer(state, action) {
  console.log('reducer', state, action);
  return state;
}

const store = createStore(reducer);
```
