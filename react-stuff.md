React compiles the JSX to the ``` React.createElement``` which is why
we import React into our apps.

You can also put a component in the ``` ReactDOM.render(<Counter />),document.getElementById("root"))```

this can reference different objects
  //if a function is called as part of a method in an object, this in that function         will always return a reference to that object.
  // If that function() is called as a stand alone function without a object reference,       this by default returns a reference to the window object, but if the strict mode is     enabled this will return undefined
```js
(29:00)
We can return a jsx element in the render:
class Counter extends Component {
  render() {
    return <h1>Hello World</h1>
  }
}
export defualt Counter;
```

(31:30)
React must have a parent element to function properly. That is why everything must be wrapped in one <div></div>:

```js
render() {
  return(
    <div>
      <h1>Hello World</h1>
      <button>Increment</button>
    </div>
  );
}

export default Counter;
```
(37:15)
You can have any Javascript expression inside the curly braces that you want. In the span tags for ex:
```js
this.state = {
  count: 1
}

render() {
  return(
    <div>
      <span>{this.state.count}</span>
      <button>Increment</button>
    </div>
    );
   }
 }
 
 export default Counter; 
```
(37:45)
A method with destructuring with a turnary operator. This expression in the span tags calls
 the formatCount method.
```js
this.state = {
  count: 1
}

render() {
  return(
    <div>
      <span>{this.formatCount()}</span>
      <button>Increment</button>
    </div>

formatCount() {
  const {count} =this.state
  return count === 0 ? 'Zero' : count;
 }
}

export default Counter;
```

#### Expressions just return a value. (39:00)
You can also return a JSX expression in the turnary:
```js
this.state = {
  count: 1
}

render() {
  return(
    <div>
      <span>{this.formatCount()}</span>
      <button>Increment</button>
    </div>

formatCount() {
  const {count} =this.state
  return count === 0 ? <h1>Zero</h1> : count;
 }
}

export default Counter;
```

JSX expressions are like normal javascript objects. You can return them from a function, you can pass them to a function,
and can also you the as a value of a constant or variable like:
```js
const x = <h1>Zero</h1>
```

#### Setting Attributes (40:58)
Usually when setting attrubutes you set them a static text like:
```js
<input src=" " alt=" " />
```

You can add a property to the state of imageUrl and add that to you src attribute to change it dynamically:
```js
state = {
  count: 0,
  imageUrl: 'https://picsum.photos/200'
}

render() {
  return(
    <div>
      <img src={this.state.imageUrl} alt='' />
      <span>{this.formatCount()}</span>
      <button>Increment</button>
    </div>
   )
 }
 
 export default Counter;   
```

Setting classes and style attributes are a little different
```js
state = {
  count: 0,
}

styles = {
  fontSize: 10,
  fontWeight: 'bold',
}

render() {
  return(
    <div>
      <span style={this.styles} >{this.formatCount()}</span>
      <button> Increment </button>
    </div>
    )
 }
 export default Counter;
```
()
Rendering classes dynamically (47:40)
Changing the type of buttons dynamically.
```js
state = {
  count: 0,
}

render() {
  const classes = 'badge m-2 badge-';
  classes += (this.state.count === 0) ? 'warning' : 'primary';

  return(
    <div>
      <span className={classes} >{this.formatCount()}</span>
      <button>Increment</button>
    </div>
   );
 }
 
export default Counter;
```

(49:30)
You can do similar here by calling the method from inside the className itself.
```js
render() {
  
  return(
    <div>
      <span className={this.getBadgeClasses()}> {this.formatCount()} </span>
      <button>Increment</button>
    </div>
   )
 }
 
 getBadgeClasses() {
  let classes = 'badge m-2 badge-';
  classes += (this.state.count === 0) ? 'warning' : 'primary';
  return classes;
 }
}

 export default Counter;
```

(51:15)
Mapping through the tag array in state while the clssName is calling an arrow function to change its style:
```js
state = {
  count: 0,
  tags: ['tag1', 'tag2', 'tag3']
}
render() {
  

  return(
    <div>
      <span className={this.getBadgeClasses()}> {this.formatCount()} </span>
      <button>Increment</button>
      <ul>
        {this.state.tags.map(tag => <li key={tag.id}>{ tag }</li>)}
      </ul>
    </div>
   );
 }
 
 getBadgeClasses() {
  let classes = 'badge m-2 badge-';
  classes += (this.state.count === 0) ? 'warning' : 'primary';
  return classes;
 }
}

 export default Counter;
```
(55:00)
Another way to render the tag array:
```js
state = {
  count: 0,
  tags: ['tag1', 'tag2', 'tag3']
}

renderTags() {
  if (this.state.tags.length === 0) return <p>There are no tags</p> // A conditional
}

<ul> {this.state.tags.map(tag => <li key={tag.id}>{ tag }</li>)} </ul>

render() {
  return(
    <div>
      {this.state.tags.length === 0 && 'Please create a new tag!"} // Another conditional
      { this.renderTags() }
    </div>
   );
 }
 
  export default Counter;
```
This reads like:
  Please create a new tag!
  There are no tags
  
#### Handle Events (1:01:09)
  ```js
  state = {
  count: 0,
}

handleIncrement() {
  
}

render() {
  return(
    <div>
      <span onClick={this.handleIncrement} className={this.getBadgeClasses()}> {this.formatCount()} </span>
      <button>Increment</button>
    </div>
   );
 }
 
 getBadgeClasses() {
  let classes = 'badge m-2 badge-';
  classes += (this.state.count === 0) ? 'warning' : 'primary';
  return classes;
 }
 
  export default Counter;
  ```

#### Updating State (1:08:45)
To set state and increment:
```js
handleIncrement = () => {
  this.setState({ count: this.state.count + 1 })
}
```

#### Passing Event Arguments (1:13:02)
If you want to pass an argument to an event handler, put an arrow function in your onClick function.
```js
handleIncrement = (product) => {
  console.log(product)
  this.setState({ count: this.state.count + 1 })
}
render() {
  return (
    <div>
      <span className={this.getBadgeClasses()}> {this.format()} </span>
      <button 
      onClick={ () => this.handleIncrement(product)}
      className="btn btn-secondary btn-sm"
      >
        Increment
      </button>
    </div>
  );
}

 export default Counter;
```
(1:17:30)
#### Composing Components
```js
class Counters extends Component {
  state = {
    counters:[
      { id: 1, value: 0 },
      { id: 2, value: 0 },
      { id: 3, value: 0 },
      { id: 4, value: 0 },
    ]
  }
  render() {
    return (
      <div>
        { this.state.counters.map( counter => <Counter key={counter.id} /> ) }
      </div>
     );
  }
}

export default Counters
```
You can pass something in between the component itself, instead of having a self closing tag we wrap the jsx <h4> between them.
```js
class Counters extends Component {
  state = {
    counters:[
      { id: 1, value: 0 },
      { id: 2, value: 0 },
      { id: 3, value: 0 },
      { id: 4, value: 0 },
    ]
  }
  render() {
    return (
      <div>
        { this.state.counters.map( counter => 
            <Counter key={counter.id} value={counter.value} select={true} >
              <h4> Title </h4>
            <?Counter>
      </div>
     );
  }
}

export default Counters
```


(2:10:30)
componentDidount
```js

```
