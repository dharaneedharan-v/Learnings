


### 1. **Functional Components**

- These are just JavaScript functions.
- They accept `props` as an argument and return JSX.
- Simpler and commonly used in modern React.

**Example:**

```jsx
import React from 'react';

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

export default Greeting;

```

Usage:

```jsx
<Greeting name="Machan" />

```

Output:

```
Hello, Machan!

```

---

### 2. **Class Components**

- These are ES6 classes that extend `React.Component`.
- They can have **state** and **lifecycle methods**.
- Less common now but still important for legacy code.

**Example:**

```jsx
import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

export default Greeting;

```

Usage:

```jsx
<Greeting name="Machan" />

```

Output:

```
Hello, Machan!

```


---


Functional Components : 

To identify it is a  component:

- When a **function name starts with a capital letter**, it means it is a component.
    
- It should **return a single HTML element** or single div elements.
    

All React components are **JavaScript functions**, but not all JavaScript functions are React components.

**Best practices:**

- Keep the **file name with the first letter capitalized**.
    
- **Name the function the same as the file name**.
    
- **Return a single component by default**.

Example : 

Template    
```jsx 
// main.jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'
import Greetings from './Greetings.jsx'
createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
    <Greetings />
  </StrictMode>,
)
```


```jsx 
// Greetings.jsx
function Greetings() {
    return <h1>Hello, World!</h1>;
}
export default Greetings;

```


Exporting One or More Compontes : 


```jsx 
// main.jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'
import { Greetings , Hello as dd  } from './Greetings.jsx'  Imported as like as how exported in the Greeting.jsx

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
    <Greetings />
    {/* <Hello /> */}
    <dd> 
  </StrictMode>,
)

```

```jsx 

// Greetings.jsx
function Greetings() {
    return <h1>Hello, World!</h1>;
}

function Hello(){
    return <h3> Vanakam da Mapla Theni la Irunthu...!!! </h3>;
}
export { Greetings, Hello };


```


---

### Why We are using the Functional Components Not the class Components: 

1. In modern React, we mostly use **functional components** instead of class components because of a few reasons. 
2. First, functional components are **simpler and shorter**—we don’t need constructors, `this`, or `render()` methods. 
3. Second, with **React hooks** like `useState` and `useEffect`, functional components can manage **state and lifecycle methods**, which previously required class components.
4. Third, functional components **reduce common bugs** caused by `this` binding, and they align better with **modern React libraries and best practices**. 
5. So, while class components are still valid, functional components are the standard for new React projects.

---

### What is a Fragment? 

A **Fragment** is a **special wrapper in React** that lets you group **multiple elements** **without adding extra nodes to the DOM**.

In plain HTML, if you want to return multiple elements, you usually need a parent `<div>`:

```jsx
function Example() {
  return (
    <div>
      <h1>Hello</h1>
      <p>How are you?</p>
    </div>
  );
}

```

But this adds an **extra `<div>`** to the DOM, which can mess up your CSS or layout.

With **Fragments**, you can do this instead:

```jsx
import React from 'react';

function Example() {
  return (
    <><h1>Hello</h1>
      <p>How are you?</p>
    </>
  );
}

export default Example;

```

- `<>...</>` is **short syntax** for a Fragment.
- You can also write it as `<React.Fragment>...</React.Fragment>`.

---

### **Why use Fragments?**

1. **No extra DOM element** – keeps the DOM cleaner.
2. **Better for styling and layout** – avoids unnecessary wrappers.
3. **Useful in lists or tables** – you can wrap multiple children without breaking structure.





