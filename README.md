# linkedin-learning-reactjs

## What did you learn?

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
