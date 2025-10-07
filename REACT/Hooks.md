
### What are Hooks in React?

**Answer:** Hooks are special functions that allow you to use React features like **state, lifecycle methods, and context** in **functional components**.

- Example: `useState`, `useEffect`.
    
- Replaced the need for class components for most tasks.
---

### What is useState ? 

useState is a fundamental React Hook that allows functional components to manage and update their own internal data.


Example : 
```jsx 
// count.js
import { useState } from "react";
function Count (){
    const [count , setcount ]   = useState(0);
    return(
        <>
        <h1>Counter App</h1>
        <button onClick={()=> setcount(count+1)}>  Click Here to see the counter </button>
        <h3>This is the Rendered Result : {count } </h3>
        </>
    )
}
export default Count
```


```jsx

// main.jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'
import { Greetings , Hello  } from './Greetings.jsx'
import Count from './count.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
    <Greetings />
    <Count />
  </StrictMode>,
)

```
