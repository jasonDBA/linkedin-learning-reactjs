# linkedin-learning-reactjs

## What did you learn?

# React.createElement()
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
