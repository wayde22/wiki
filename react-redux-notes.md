##### Redux Notes

Read 12 Factor App

A minimum amount of react-redux code that will print onto a screen is this

index.js
```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';

import { createStore } from 'redux';
import { Provider } from 'react-redux';
import { reducer } from './store/reducer';

const store = createStore(reducer, window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__())

ReactDOM.render(<Provider store={store}><App /></Provider>, document.getElementById('root'));

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister();
```

App.js
```js
import React from 'react';
import logo from './logo.svg';
import './App.css';
import { connect } from 'react-redux';

class App extends React.Component {



  render() {
    return (
      <div className="App">
      <h1>The Store</h1>
      </div>
    );
  }
}

export default connect()(App);
```

reducer.js
```js
const items = [

];

const initialState = {

};

export const reducer = (state = initialState, action) => {
  switch(action.type) {
    
    default:
      return state;
  }
}
```
