# Seperating Client And API Services

## Objectives

* Setup Create React App
* Walkthrough setting up a small application
* Explain how .env files work within Create React App

## Introduction: 

In the last lesson we built out a small client app using HTML and Vanilla JS, which was fun, but would take a lot of work to build a full scale app. Plus why did we learn all of this React and Redux stuff if we weren't going to use it? In this lesson, we are going to introduce on of the greatest tools in the React toolset __Create React App CLI__. 

## Create React App

The __Create React App CLI tool__ is one of the best things to happen in the React world. Once upon a time, to get a React app working we had to spend days/weeks learning the tooling just to get it up and running. Now it takes 4 simple steps 

```bash 
1. npm install -g create-react-app (we might need to run 'sudo npm install -g create-react-app')
2. create-react-app hello-world
3. cd hello-world
4. npm start
```

And.... 

![App Success](https://camo.githubusercontent.com/506a5a0a33aebed2bf0d24d3999af7f582b31808/687474703a2f2f692e696d6775722e636f6d2f616d794e66434e2e706e67)

In most dev environments it should automatically open up in our browser and show the app running at localhost:3000, but if not we can open up our favorite browser and go to localhost:3000. This is the screen we should see.

![create react app splash page](https://s3.amazonaws.com/learn-verified/create-react-app-splash-page.png)


## File Structure 

The app will create a file structure similiar to this 

```
hello-world
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   └── favicon.ico
│   └── index.html
│   └── manifest.json
└── src
    └── App.css
    └── App.js
    └── App.test.js
    └── index.css
    └── index.js
    └── logo.svg
    └── registerServiceWorker.js
```

A couple things to note, all of our code should stay inside of the `./src` folder. A typical React application is set up like this, but varies depending on the company using them. 

```

# example file structure of /src folder
├src
  |── actions
  |     └── itemsActions.js
  |── containers 
  |     └── Items.js
  |── components
  |     └── ItemDetail.js
  |── reducers
  |     └── itemsReducer.js
  └── App.css
  └── App.js
  └── App.test.js
  └── index.css
  └── index.js
  └── logo.svg
  └── registerServiceWorker.js
```

React file structure is not as set in stone as a Rails app, so don't feel like this is the one true way. 

### Features 

The CLI comes with a few wrappers around common npm commands that allow us to do some simple stuff easily. 

```
npm start
```

Will run the app in development mode at localhost:3000. It will also reload the browser when making changes to our code with common build errors and lint warnings.

```
npm test
```

Runs the default test watcher that comes built into Create React App, which uses the Jest assertion library (One of the best JS testing libraries). Their is an example test for App.test.js in the /src folder, to show us how to mock up a basic component test.

```
npm run build
```

This command is used for a creating a production build and compiles all of the code into the a /build folder on the root directory. We will not be using this command, but is good to know that it exists. 

### .env

Create React App allows the use of .env files out of the box, so if we need to set environment variables Create React App handles this well. Let's try out setting up a Environemental Variable just so we can get the hang of it. First lets make sure that we are in the root directory of the app we just created. Once we guarantee that we can create our then .env file. 

```
touch .env
```

Let's open up the .env file and lets add a variable for a favorite color. Mine is blue, so let's use that. One thing to note, Create React App requires that the environmental variable starts with `REACT_APP_` otherwise it will ignore it. This is in place so that sensitive machine info is inaccessable in our React code. 

```javascript 
// .env 
REACT_APP_FAVORITE_COLOR=blue
```

Since these are environment variables, we do have to shut down the React server and restart it to access it in our code. Lets shut down the server and restart it using `npm start` then go into our App.js file and change the code to look like this. 

```jsx
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

class App extends Component {
  render() {
    return (
      <div className="App">
        <div className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h2>Favorite Color App</h2>
        </div>
        <p className="App-intro">
          My favorite color is {process.env.REACT_APP_FAVORITE_COLOR}
        </p>
      </div>
    );
  }
}

export default App;
```

Now if we check out the browser we should see the original Create React App splash page but with our favorite color blue on the screen. 

### Summary

In this lesson we learned a ton about Create React App. In the next lesson we will work on connecting the React app to our Rails API.

<p class='util--hide'>View <a href='https://learn.co/lessons/introducing-create-react-app'> Introducing Create React App</a> on Learn.co and start learning to code for free.</p>
