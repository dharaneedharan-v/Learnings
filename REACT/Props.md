

**Props** are used to pass data **from a parent component to a child component**.

Passing the Data from App.jsx -> to the User.jsx Component: 

```jsx
// User.jsx -> 3
function User(Fuck) {
    // here the props can be passed by the var Fuck.
    console.log("This is a hello function from the user file");
    return (
        <>
            <h3>This is a user component</h3>
            <h1>{Fuck.Name}</h1>
            <h2>{Fuck.Age}</h2>
        </>
    )
}
export default User;

```


```jsx

// App.jsx -> 2
import User from './User.jsx';
function App(){
  const PropForUserComponent= {
    name : "dharani",
    Age:20,
    Collage:"BIT",
    City :"Bangalore"
  }
  console.log("This is a App Component");
  return (
  <>
   <h1>This is a App Component</h1>
   {/* <img src="" alt="" /> */}  {/* like the Image tag in the Html props can be passed to the component */}
  <User 
  // The Name , Age , collage  , city  is a variable 
  Name={PropForUserComponent.name} 
  Age= {PropForUserComponent.Age} 
  Collage={PropForUserComponent.Collage} 
  City = {PropForUserComponent.City}/>
  </>

  )
}
export default App;

```


```jsx

// main.jsx -> 1
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'
import { Greetings , Hello  } from './Greetings.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
    <Greetings />
  </StrictMode>,
)

```



>In React The data flow in  the Unidirectional Alone.

>The props are passed as a JSON object. 



---
### Using the Spread Operator : 

The spread operator in JavaScript, denoted by three consecutive dots (`...`), is a powerful feature introduced in ES6 (ECMAScript 2015). It allows you to expand or "spread out" elements of an iterable (like an array, string, or object) into individual elements where multiple elements or properties are expected.



From the App.jsx to User.jsx 

```jsx 

// App.jsx
import User from './User.jsx';
function App(){
  const PropForUserComponent= {
    name : "dharani",
    age:20,
    collage:"BIT",
    city :"Bangalore"
  }
  console.log("This is a App Component");
  return (
  <>
   <h1>This is a App Component</h1>  
<User  {...PropForUserComponent} /> 
  </>
  )
}
export default App;

```


```jsx 
//user.jsx 
function User(Fuck){
    const {name , age , collage ,city} = Fuck  // this is a Destructure Inside the Function Body
    console.log("This is a hello function from the user file");
    console.log(Fuck);
    return (
        <>
        <h3> Example for the Spread Operator </h3>
        <h1>{name}</h1>
        <h2>{age}</h2>
        <h2>{collage}</h2>
        <h2>{city}</h2>
        </>
    )
}


export default User;
```

or 

```jsx 
function User({name , age , collage ,city}){
    console.log("This is a hello function from the user file");
    return (
        <>
        <h3> Example for the Spread Operator </h3>
        <h1>{name}</h1>
        <h2>{age}</h2>
        <h2>{collage}</h2>
        <h2>{city}</h2>
        </>
    )
}
export default User;

```


>The object name must be same while in the spread as we are using the Same object as a variable for the props other wise it will not render any thing in the UI 



---



## What Are Props (Quick Recap)

**Props** (short for _properties_) are used to pass data **from a parent component to a child component**.

Example (without destructuring):

```jsx


// User.jsx 
function User(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>Age: {props.age}</p>
      <p>City: {props.city}</p>
    </div>
  );
}

export default User;
// App.jsx 
function App() {

  return (
  <>
    <User 
    name="Dharani" 
    age={20} 
    city="Bangalore" 
    
    />;
    
  </>
  )

}

export default App;

```

This works, but `props.name`, `props.age`, etc. can get repetitive — so we use **destructuring**!

---

##  Destructuring Props (Cleaner Way)

Instead of using `props.name`, you can **destructure props directly in the function parameters** 👇

```jsx
function User({ name, age, city }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>City: {city}</p>
    </div>
  );
}

function App() {
  return <User name="Dharani" age={20} city="Bangalore" />;
}

```

✅ **Cleaner**

✅ **Easier to read**

✅ **No need to repeatedly write `props.`**

---

##  You Can Also Destructure Inside the Function Body

If you prefer to access `props` first:

```jsx
function User(props) {
  const { name, age, city } = props;

  return (
    <div>
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>City: {city}</p>
    </div>
  );
}

```

Same result — just a different syntax.

---

##  Example with Nested Props

If props contain nested objects, you can destructure them too:

```jsx
function Profile({ user: { name, age, address: { city } } }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>City: {city}</p>
    </div>
  );
}

function App() {
  const userInfo = {
    name: "Dharani",
    age: 20,
    address: { city: "Bangalore" }
  };

  return <Profile user={userInfo} />;
}

	```

---

## What is Data Binding?

**Data binding** means **connecting data in your code** (like variables, `state`, or `props`) **to what appears in the UI**.

In React, data binding defines **how data flows** between:

- the **component logic** (JavaScript)
    
- and the **user interface** (JSX)

## Types of Data Binding in React

React uses **one-way data binding** by default. 
 **Two-way binding** can be simulated.

----
