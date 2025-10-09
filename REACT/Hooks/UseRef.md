## Why use `useRef`

1. **Access DOM elements directly**
    
    - Example: focus an input, scroll, play/pause video.
        
2. **Store mutable values across renders**
    
    - Keeps data like timers, previous state, counters, etc.
        
3. **Avoid unnecessary re-renders**
    
    - Updating a ref does **not trigger component re-render** like `useState` does.
        
4. **Persistent storage for component lifetime**
    
    - The value inside `useRef` persists even after re-renders.
        
5. **Useful for cleanup tasks**
    
    - Store timer IDs or subscriptions to clear them in `useEffect` cleanup.


