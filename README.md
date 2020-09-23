# linkedin-learning-reactjs

## What did you learn?

### What is NPM?
* NPM (Node Package Manager): manages ecosystem of node packages / modules
* A package contains:
  * JS files
  * package.json
  
### Setting up lite server?
* Lite Server: A lightweight development web server with support for Single Page Apps
1. Install lite-server package in npm
```
npm install lite-server --save-dev
```
2. In package.json, add the two lines under "scripts" and save it as follows:
```
"scripts": {
    "start": "npm run lite",
    "test": "echo \"Error: no test specified\" && exit 1",
    "lite": "lite-server"
  }
```
3. Run 'npm start' in the project dir

### React.createElement()
* Create and return a new React element
* Code written with JSX will be converted to use React.createElement()
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';

ReactDOM.render(
  React.createElement("h1", null, "Hello!"),
  document.getElementById('root')
);
```

### Props
* An object that passes data from a parent component to a child component
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';

// function Hello(props) {
//   console.log(props);
//   return(
//     <div>
//       <h1>Hello, {props.name}</h1>
//       <p>{props.message}</p>
//       <p>Class Number: {props.classNumber}</p>
//     </div>
//   );
// }

function Hello({name, message, classNumber}){
  return(
    <div>
      <h1>Hello, {name}</h1>
      <p>{message}</p>
      <p>Class Number: {classNumber}</p>
    </div>
  );
}

ReactDOM.render(
  <Hello name="Jason" message="Welcome to React.js! Have fun!" classNumber={2020100}/>,
  document.getElementById('root')
);
```

### Composing Components
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';

function Person(props) {
  return(
    <h1>{props.name}</h1> 
  );
}

function Application() {
  return(
    <div>
      <Person name="Jason"/>
      <Person name="Smith"/>
      <Person name="Steven"/>
    </div>
  );
}

ReactDOM.render(
  <Application />,
  document.getElementById('root')
);
```

### Rendering Lists
```javascript
const lakeList = [
  "Echo Lake",
  "Ontario Lake",
  "Niagara Lake"
];

function Application(props) {
  return(
    <div>
      <ul>
        {props.lakes.map(x => (
          <li>{x}</li> 
        ))}
      </ul>
    </div>
  );
}

ReactDOM.render(
  <Application lakes={lakeList} />,
  document.getElementById('root')
);
```

### Rendering lists of objects
```javascript
const users = [
  {id: "1", name: "Jason", depart: "Development"},
  {id: "2", name: "Smith", depart: "Finance"},
  {id: "3", name: "John", depart: "Human Resources"}
];

function Application(props) {
  return(
    <div>
      <h1>Party Memebers</h1>
      {props.userDB.map(x => (
        <div>
          <h3>Name: {x.name}</h3>
          <p>Department: {x.depart}</p>
          <hr/>
        </div>
      ))}
    </div>
  );
}

ReactDOM.render(
  <Application userDB={users} />,
  document.getElementById('root')
);
```

###Adding Keys
```javascript
const list = [1,2,3,4,5];

function Application({items}) {
  return(
    <ul>
      {/* {items.map((item, i) => (
        <li key={i}>{item}</li>
      ))} */}
      {items.map(item => (
        <li key={item.toString()}>{item}</li>
      ))}
    </ul>
  );
}

ReactDOM.render(
  <Application items={list} />,
  document.getElementById('root')
);
```

### Conditional Rendering
```javascript
function Summersports({name}){
  return(
    <h1>I do want to play {name}!</h1>
  ); 
}

function Wintersports({name}){
  return(
    <h1>I do want to play {name}!</h1>
  );
}

function Application(props) {
  if(props.season === "summer"){
    return <Summersports name="tennis"/>
  } else if(props.season === "winter"){
    return <Wintersports name="table tennis"/>
  }
}

ReactDOM.render(
  <Application season="summer" />,
  document.getElementById('root')
);
```

### React.Fragment
* When you want components to return multiple elements in React, they must be wrapped by div, for example.
* If using <React.Fragment>, you can avoid having too many div.
* A short syntax: <> </>
```javascript
function App(){
  return(
    <div>
      <Summersports />
      <Wintersports />
    </div>
  );  
}
  
// Instead,
function App(){
  return(
    <React.Fragment>  // <>: a short syntax
      <Summersports />
      <Wintersports />
    </React.Fragment> // </>
  );  
}
```
