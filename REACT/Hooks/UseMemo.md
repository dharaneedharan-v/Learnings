## Why we use useMemo : 

1. **Optimize expensive calculations**
    
    - Example: complex math or data filtering that shouldn’t run on every render.
        
2. **Avoid unnecessary recalculations**
    
    - React remembers the result until dependencies change.
        
3. **Improve performance**
    
    - Prevents slow UI rendering in large lists or heavy computations.
        
4. **Useful with derived state**
    
    - When a value depends on props/state but shouldn’t recompute every time.
        
5. **Works with referential equality**
    
    - Useful when passing values/objects to child components to prevent unnecessary re-renders.