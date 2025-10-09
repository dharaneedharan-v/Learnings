
## What is `useCallback`

- `useCallback` is a React Hook that **returns a memoized version of a function**.
    
- It **prevents the function from being recreated on every render**, unless its dependencies change.

## Why we use `useCallback`

1. **Prevent unnecessary function re-creations**
    
    - Functions inside a component normally recreate on every render.
        
2. **Optimize performance**
    
    - Useful when passing functions to child components wrapped in `React.memo`.
        
3. **Avoid unnecessary re-renders in child components**
    
    - If a child receives a function as prop, `useCallback` ensures it doesn’t think the prop changed on every render.
        
4. **Works with dependencies**
    
    - The function is recreated **only when dependencies change**.
        
5. **Useful in event handlers and callbacks**
    
    - Example: button click handlers that are passed down as props.