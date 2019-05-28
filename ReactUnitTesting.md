##### Unit Testing React Apps

### What do you want to test?
- Is the right information rendered?
- Do interactions rendr the right results?
- What about styling?

### How Do we test
- React-test-renderer
Provided by React Team
Does the basics
Lond of Hard to use
- Enzyme
Made by Airbnb
- React-testing-library
user-centric approach
Discourages shallow rendering

Enzyme example:
[Enzyme](https://airbnb.io/enzyme/)
```js
expect(component.find('TemperaturInput').find({scale: 'f'}).length).toEqual();

desctibe('when 32 entered in 'f', () => {
  beforeAll() => {
  component.find('TemeratureInput').find({scale: 'f'})
      .sumulate('temperatureChange', '212);
      });
      it('shows 0 in celcius', () ()=> {
 ```js     
      
### What is snapshot testing?
- Captures the rendered output of the unit under test (saves a snapshot file in your project)
- Subsequent runs compare output to captured output
Pros: is it is easy.
Cons: Its hard to tell what you are testing

Test are very brittle
Tests are easily broken by imlementation details
When test break, it's gard to tell why.
Gives you a false sense of security.

## Adding Enzyme to your react app:
```js
Yarn add –dev enzyme enzyme-adapter-react-16
Create setupTests.js
```

## Add to your app
```js
import Enzyme from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';
Enzyme.configure({ adapter: new Adapter() });
```
