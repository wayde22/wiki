### Redux
[react-redux tutorial](https://daveceddia.com/redux-tutorial/)

##### index.js -- Add the imports createStore from redux, Provider from react-redux, reducer from ./reduce. Add createStore and wrap
the App component in the Provider tags.
```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';

import { createStore } from 'redux'; //This is added for Redux
import { Provider } from 'react-redux'; //This is added for Redux to wrap around the components
import { reducer } from './reducer' //This is added for Redux

const store = createStore(reducer, window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()); //This is added for Redux, the window object is for the Redux Dev Tools

ReactDOM.render(<Provider store={store} ><App /></Provider>, document.getElementById('root')); // Wrap the components(in this case App) in Provider tags with the store prop

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister();
```
##### App.js -- import actions from ./actions, connect from react-redux and create the event handlers and buttons ect to render life cycle. Create the mapsStateToProps and give it an export.
```js
import React from 'react';
import logo from './logo.svg';
import './App.css';
import { CHANGE_WHIZ_TO_BANG, CHANGE_BAR_TO_RANDOM, CHANGE_SOMETHING} from './actions' // must import these from you actions.js file to keep from mispelling errors

import { connect } from 'react-redux'; // Using the connect function that comes with react-redux, you can plug any component into Redux’s store and pull out the data it needs.


class App extends React.Component {

  handleClick = () => {
    this.props.dispatch({ type: CHANGE_BAR_TO_RANDOM, payload: Math.floor(Math.random() * 100)}) //this.props.dispatch({ type: 'CHANGE_BAR_TO_RANDOM', payload: Math.floor(Math.random() * 100)})
  }

  handleWhizClick = () => {
    this.props.dispatch({ type: CHANGE_WHIZ_TO_BANG, payload: 'Bang!!!'})
  }

  handleSomeClick = () => {
    this.props.dispatch({ type: CHANGE_SOMETHING, payload: 'WOW!!!'})
  }
  
  render() {
    return (
      <div className="App">

        <button onClick={this.handleClick}> Click </button>
        <div>{this.props.reduxState.foo}</div>
        
        <button onClick={this.handleWhizClick}>Whiz</button>
        <div>{this.props.reduxState.whiz}</div>

        <button onClick={this.handleSomeClick}> Something </button>
        <div>{this.props.reduxState.some}</div>

      </div>
    );
  }
}

const mapStateToProps = (state) => ({ // state is the whole state of Redux
  reduxState: state
})

export default connect(mapStateToProps)(App);
```
##### reducer.js -- Create the initialState, the reducer function, with the switch state actions
```js
const initialState = {
  foo: 'Random Number',
  whiz: 'Targeted',
  some: 'OOOHHH'
}

export const reducer = (state = initialState, action) => { // The store needs to be initialized before its ran the first time or it will break
  
  switch(action.type) {
    case 'CHANGE_BAR_TO_RANDOM':
      return {...state, foo: action.payload};
    case 'CHANGE_WHIZ_TO_BANG':
      return {...state, whiz: action.payload};
    case 'CHANGE_SOMETHING':
      return {...state, some: action.payload};
    default:
      return state;
      
  }
}
```
##### actions.js -- Create the action constants and export them so that you can use them to keep from mispelling errors.
```js
// These are "action constants" that are used to keep from making spelling mistakes that could arise later with errors

export const CHANGE_WHIZ_TO_BANG = 'CHANGE_WHIZ_TO_BANG';

export const CHANGE_BAR_TO_RANDOM = 'CHANGE_BAR_TO_RANDOM';

export const CHANGE_SOMETHING = 'CHANGE_SOMETHING';
```

```js

```
