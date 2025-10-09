

`useEffect` is a React Hook that lets you synchronize a component with an external system.

Some components need to synchronize with external systems. 

For example, you might want to control a non-React component based on the React state, set up a server connection, or send an analytics log when a component appears on the screen. 

_Effects_ let you run some code after rendering so that you can synchronize your component with some system outside of React.


## Basic Syntax: 

A call back function and a Array 

```jsx
useEffect( () => {
  // 👇 Your side-effect code here
} );

or 
   useEffect (  ()=>{},[]  );
```

💬 This runs **after every render** of the component.



## Run only once (when component mounts)

```jsx
useEffect(() => {
  // This runs only once — like "on load"
}, []);

```

➡️ Empty square bracket `[]` means — run only when the component first loads.



## Run only when specific data changes

```jsx
useEffect(() => {
  // This runs only when 'count' changes
}, [count]);

```

➡️ Inside the `[]`, you list the variables you want React to _watch_.

When any of those change, the effect runs again.



##  With cleanup (when component unmounts)

```jsx
useEffect(() => {
  console.log("Component mounted");

  // 🧹 Cleanup function
  return () => {
    console.log("Component unmounted");
  };
}, []);

```

This must be taken care for the better performance memory leak etc..

➡️ The `return` part runs **before** the next effect OR **when the component is removed** — useful for clearing timers, removing event listeners, etc.


## Summary Table : 

|Purpose|Syntax|When It Runs|
|---|---|---|
|Every render|`useEffect(() => {...});`|After every render|
|Only once|`useEffect(() => {...}, []);`|On mount|
|On variable change|`useEffect(() => {...}, [count]);`|When `count` changes|
|With cleanup|`useEffect(() => { ...; return () => {...}; }, []);`|Cleanup on|

Example : 

```jsx 
import { useEffect, useState } from "react";
function UseEffectExample(){

    const [count , setcount] = useState(100);
    console.log("Component Rendered starting and the count is : ", count );

    useEffect( ()=> {
        console.log("useEffect called");
        setcount(200);
    } , []) 

    console.log("UseEffectExample rendered and  the count is : ", count );

    return (
        <>
        <h1>This is UseEffectExample Component</h1>
        <h2>The count is : {count} </h2>
        <button onClick={ ()=> setcount(count + 1) } > Click Here to increase the count </button>
        </>
        )

}
export default UseEffectExample;
```

output : 

![[Pasted image 20251008191324.png]]


Example :

```jsx 
import { useEffect, useState } from "react";

function UseEffectExample() {
  const [count, setcount] = useState(100);
  console.log("Component Rendered starting and the count is:", count);

  useEffect(() => {
    console.log("useEffect called");

    // Example side effect — setting a timer
    const timer = setInterval(() => {
      console.log("⏱ Timer running...");
    }, 1000);

    // Update the count
    setcount(200);

    // 🧹 Cleanup function (runs before component unmount or before next effect)
    return () => {
      console.log("🧹 Cleanup: clearing timer");
      clearInterval(timer);
    };
  }, []); // Runs only once and the timer will not reset whrn the reload then only it will clean it , if we want to clean means add the count in the array. 

  console.log("UseEffectExample rendered and the count is:", count);

  return (
    <>
      <h1>This is UseEffectExample Component</h1>
      <h2>The count is: {count}</h2>
      <button onClick={() => setcount(count + 1)}>
        Click Here to increase the count
      </button>
    </>
  );
}

export default UseEffectExample;

```

Output : 

![[Pasted image 20251008192154.png]]


