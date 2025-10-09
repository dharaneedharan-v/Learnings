## What is `useContext`

- `useContext` is a React Hook that **allows a component to access values from a Context** directly, without passing props through every level.
    
- Think of it as **React’s way of avoiding “prop drilling”**.
    


## Why we use `useContext`

1. **Share data globally across components**
    
    - Example: theme, user info, language settings.
        
2. **Avoid prop drilling**
    
    - Don’t need to pass props manually through many nested components.
        
3. **Simplifies state management for small apps**
    
    - Easier than Redux for simple use cases.
        
4. **Works with any value**
    
    - Objects, arrays, functions — anything can be shared.
        
5. **Makes components cleaner and more readable**
    
    - No need to pass unnecessary props to intermediate components.