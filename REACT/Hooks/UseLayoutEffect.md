
## *What is `useLayoutEffect`* 

- *`useLayoutEffect` is **just like `useEffect`**, but it runs **synchronously** **after the DOM is updated** and **before the browser paints the screen**.*
    
- *It is mainly used for **reading layout or doing DOM measurements** before the user sees the update.*
    

*---*

## *Why we use `useLayoutEffect`* 

1. ***To measure DOM elements (layout, size, position)***
    
    - *Example: getting width, height, or scroll position immediately after rendering.*
        
2. ***To perform visual adjustments before the screen updates***
    
    - *Avoids flicker or visual jumps.*
        
3. ***When you need synchronous DOM updates***
    
    - *Runs before the browser paints, unlike `useEffect`, which runs after.*
        
4. ***Used for animations or scroll adjustments***
    
    - *Perfect for adjusting scroll or element positions before render is visible.*
        
5. ***Advanced performance tuning***
    
    - *Use only when layout reading or DOM manipulation is required.*
        

*---*

 ***One-line :***

> *"`useLayoutEffect` na, `useEffect` madhiri thaan, aana DOM update aana odane run aagum — screen la kaatrapathukku munadi." ⚡*

