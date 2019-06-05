#Files in component folder
---
### App.js
```js
import React from 'react';
import ReactDOM from 'react-dom';

import Toggle from './components/Toggle.js';
import EventsAndState from './components/EventsAndState.js';
import Form from './components/Form.js';
import TextArea from './components/TextArea.js';
import Select from './components/Select.js';

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isToggleOn: true,
      name: '',
      people: [],
      food: '',
      poem: '',
      chocolate: '',
    };
  }
  handleClick = () => {
    this.setState(state => ({
      isToggleOn: !state.isToggleOn
    }));
  }
  handleChange = (event, stateKey) => {
      this.setState({
        ...this.state,
        [stateKey]: event.target.value
      });
   }
  handleEnterPress = (event) => {
    if (event.key === 'Enter') {
      this.setState({
        ...this.state,
        name: '',
        people: [
          ...this.state.people,
          event.target.value
        ]
      });
    }
  }
  handleSubmit = (event, stateKey, input) => {
    alert(`Sumited: ${input}`);
    this.setState({
      ...this.state,
      [stateKey]: '',
    });
    event.preventDefault();
  }
  render() {
    return (
      <div className="App">
        <Toggle
          handleClick={this.handleClick}
          isToggleOn={this.state.isToggleOn}
        />
        <hr/>
        <EventsAndState
          name={this.state.name}
          onKeyDown={this.handleEnterPress}
          onChange={(event) => this.handleChange(event, 'name')}
          people={this.state.people}
        />
        <hr/>
        <Form
          onSubmit={(event) => this.handleSubmit(event, 'food', this.state.food)}
          food={this.state.food}
          onChange={(event) => this.handleChange(event, 'food')}
        />
        <hr/>
        <TextArea
          onSubmit={(event) => this.handleSubmit(event, 'poem', this.state.poem)}
          poem={this.state.poem}
          onChange={(event) => this.handleChange(event, 'poem')}
        />
        <hr />
        <Select
          onSubmit={(event) => this.handleSubmit(event, 'chocolate', this.state.chocolate)}
          chocolate={this.state.chocolate}
          onChange={(event) => this.handleChange(event, 'chocolate')}
        />
      </div>
    );
  }
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);

```
---
### Events and States.js

```js
import React from 'react';

const EventsAndState = (props) => (
  <div>
    <h2> Input a name </h2>
    <input
      type="text"
      value={props.name}
      onKeyDown={props.onKeyDown}
      onChange={props.onChange}
    />
    <p> Current Name: {props.name} </p>
    <p> Current array of people: {props.people.map((person, index) => {
      if (index !== (props.people.length - 1)) {
        return `${person}, `;
      } else {
        return person;
      }
    })} </p>
  </div>
);

export default EventsAndState;
```
---
### Form.js
```js
import React from 'react';

const Form = (props) => (
  <div>
    <form onSubmit={props.onSubmit}>
      <p>My cool form:</p>
      <label>
        Input your favorite food
        <input type="text" value={props.food} onChange={props.onChange} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  </div>
);

export default Form;

```

---
### Select.js

```js
import React from 'react';

const Select = (props) => (
  <form onSubmit={props.onSubmit}>
     <label>
       Pick your favorite chocolate bar:
       <select value={props.chocolate} onChange={props.onChange}>
         <option>Select One</option>
         <option value="White Chocolate">White Chocolate</option>
         <option value="Milk Chocolate">Milk Chocolate</option>
         <option value="Dark Chocolate">Dark Chocolate</option>
       </select>
     </label>
     <input type="submit" value="Submit" />
   </form>
)

export default Select;

```

---
### TextArea.js
```js
import React from 'react';

const TextArea = (props) => (
  <form onSubmit={props.onSubmit}>
    <p>Write me a poem</p>
    <label>
      Poem:
      <textarea value={props.poem} onChange={props.onChange} />
    </label>
    <input type="submit" value="Submit" />
  </form>
);

export default TextArea;

```
---
### Toggle.js
```js
import React from 'react';

const Toggle = (props) => (
  <div>
    <button onClick={props.handleClick}>
      Click me
    </button>
    <p> Current isToggleOn: {props.isToggleOn.toString()} </p>
  </div>
);

export default Toggle;
```

---


