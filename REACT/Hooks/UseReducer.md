## What is `useReducer`

- `useReducer` is a React Hook used for **managing complex state logic**.
    
- It works like a mini version of **Redux** inside your component.
    
- You give it a **reducer function** and an **initial state**, and it returns the **current state** and a **dispatch function** to update it.

## Why we use `useReducer`

1. **For complex state logic**
    
    - When you have multiple state updates that depend on each other.
        
2. **Cleaner and more organized code**
    
    - Instead of many `useState` calls, you can handle all state updates in one place.
        
3. **Predictable state updates**
    
    - The reducer function controls how state changes, making it easy to debug.
        
4. **Useful when next state depends on previous state**
    
    - Example: increment, decrement, reset actions.
        
5. **Great for larger applications**
    
    - When managing forms, authentication, or dynamic data flows.