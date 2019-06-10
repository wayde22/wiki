# React
[Facebook GitHub React Doc](https://github.com/facebook/create-react-app)

### Setting up

1. Install yarn
  - Installing on Windows:

  1. Get Node.js
  https://nodejs.org/en/
  2. Install Yarn package
  https://yarnpkg.com/latest.msi

2. Run `yarn create react-app your-app-name`

- if you come across an issue like `is not recognized as an internal or external command, operable program or batch file`, then run the following:

```sh
yarn global add create-react-app
create-react-app my-app
```

3. Run your app

```sh
cd your-app-name
yarn start
```

- This will run your app on localhost:3000

- Add a components file inside of the src folder.

## General things about React
##### Files and what they are for
 - package.json -- is the json manifest file that has the version of react, dependencies, packages, etc.
 - App.css -- is the file where you add css to your react project.
 - index.html -- everything outputs through ```<div id="root"></div>```.
 - index.js -- It's in the source folder, ```React.render(<App />, document.getElementById('root'));``` is the line of code the puts the App Component(```import App from './App';```) in the ``` <div id="root"></div> ``` for in to render on the UI.

- 
##### Misc
- ```<AppName />``` -- this html like tag inside divs is what gets imbeded into the UI.
- ```import React from 'react';``` -- imports react library.

- ```import ReactDOM from 'react-dom';``` -- importing react DOM.
- ```import App from './App';``` -- importing the main app component.

- When writing a function out side of the class, it must be ```const handleWhatever = () => { some code }```
- When writing inside the class the function should be writen ```handleWhatever = () => { some code }```
- You call those functions like ```saveTweets()```

#### React/Javascript Event Handlers
```
Event	     Description
onchange-----An HTML element has been changed
onclick------The user clicks an HTML element
onmouseover--The user moves the mouse over an HTML element
onmouseout---The user moves the mouse away from an HTML element
onkeydown----The user pushes a keyboard key
onload-------The browser has finished loading the page
```
