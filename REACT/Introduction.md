

### *1. What is React?*


*React is a JavaScript library developed by Meta for building dynamic user interfaces using a component-based approach.* 

*It uses a Virtual DOM to efficiently update only the parts of the page that change.* 

*For example, in a counter app, when you update the count, React re-renders just that part of the UI — not the entire page — making the app fast and responsive.*

*---*

### *2) What is the difference between the Library vs Framework  ?* 


***Library**-na — tools kudukura set.*  
	*=>Neetha decide panra, epdi use pannanum, eppo call pannanum.*  
***Framework**-na — athu decide panum.*
	*=>un code-a epdi run pannanum-nu.*  



*Neetha decide panra — routing venumna React Router use panra, state management venumna Redux use panra.*

```jsx
ReactDOM.createRoot(document.getElementById('root')).render(<App />);

```

*Everything — neetha control panra.*

***Next.js (Framework):***

*File name decide panum route, rendering automatic-ah nadakum.*

```jsx
export default function Home() {
  return <h1>Hello Next.js</h1>;
}

```

*Illa control un kitta illa — framework handle panum.*


*👉 React is a **library** — only UI build panna help panum.*  
*👉 Next.js is a **framework** — structure, routing, rendering ellam ready-ah kudukum.*


*Example :* 

*React is a library — I control it.* 
*Next.js is a framework — it controls me.”*

---

### What is DOM?

1. **DOM** = stands for **Document Object Model**.
2. It is a **tree-like structure** that represents everything on a web page.
3. Every HTML tag (like `<h1>`, `<p>`, `<div>`, etc.) becomes a **node** or **object** in that tree.
4. The **browser creates the DOM** when it loads an HTML page.
5. Using JavaScript, you can **access**, **change**, **add**, or **remove** elements in the DOM.


Example : 

HTML code 👇

```html
<html>
  <body>
    <h1>Hello Machan!</h1>
    <p>This is a paragraph.</p>
  </body>
</html>

```

DOM structure 👇

```
Document
 └── html
      └── body
           ├── h1 → "Hello Machan!"
           └── p → "This is a paragraph."

```


---

### What is a single page application?

1. A **Single Page Application** is a **web app** that **loads only one main HTML page**.
    
2. When you click links or buttons, it **doesn’t reload** the whole page.
    
3. Instead, it **updates only the parts** that need to change — using **JavaScript** (usually React, Angular, or Vue).
    
4. The page feels **faster** and more like a **mobile app** because it doesn’t refresh every time.
    
5. Data is loaded **dynamically** from the server using **APIs (AJAX / Fetch)**.

---


### *3. What is React Virtual DOM [document object model ] ?*


1. ***DOM** = structure of your webpage (like a tree of HTML elements).*
    
2. ***Virtual DOM** = a **copy** of the real DOM made by React (stored in memory).*
    
3. *When something changes (like a button click or text update),*  
    *React updates the **Virtual DOM first**, not the real one.*
    
4. *React then **compares** the new Virtual DOM with the old one (this is called **diffing**).*
    
5. *It finds **only the changes** and updates **just that part** in the real DOM.*
    
6. *This makes React apps **faster** and **more efficient**.*


***Main idea:** Fast updates, smooth UI, less re-rendering.*


----

### What is JSX (JavaScript XML)? 

1. **JSX** stands for **JavaScript XML**.
    
2. It lets you **write HTML code inside JavaScript** — used in **React**.
    
3. With JSX, you can easily design your UI using a **mix of HTML and JS**.
    
4. The browser doesn’t understand JSX directly — React’s tools (like **Babel**) convert it into **regular JavaScript**.
    
5. It makes React code **cleaner**, **easier to read**, and **more powerful**.

>JSX = a way to **write HTML-like code in JavaScript** to make React components easy to create and read. ⚡


---

### What is Babel => A Transpiler ?

1. **Babel** is a **JavaScript compiler (A specific JavaScript transpiler)**.
    
2. It converts **modern JavaScript (ES6, ES7, JSX, etc.)** into **older JavaScript (ES5)** so that **all browsers can understand it**.
    
3. React uses Babel to **convert JSX** into **plain JavaScript**.
    
4. Without Babel, your browser wouldn’t know how to handle JSX or newer JS features.
    
5. It helps developers write **modern, clean code** while keeping it **compatible** with older browsers.

Example : 

👉 You write this modern React code (with JSX & ES6):

```jsx
const element = <h1>Hello Machan!</h1>;

```

👉 Babel converts it into old-style JavaScript:

```jsx
const element = React.createElement("h1", null, "Hello Machan!");

```



> **Babel** is a tool that helps React and modern JavaScript code run **smoothly in all browsers** by **converting new code into old code** that browsers can understand. ⚡

---
### What is a Transpiler? 

1. A **Transpiler** is a tool that **converts code from one version of a programming language to another** version of the **same language**.

	### **Final Summary Table** : 

|Term|What it Means|Example|
|---|---|---|
|**Transpiler**|General term for tools that convert modern code → older code|TypeScript → JS, ES6 → ES5|
|**Babel**|A specific **JavaScript transpiler**|Converts JSX → JS, ES6 → ES5|

> Transpiler = any tool that changes code into an older or different version of the same language.

---


### Build Tools : 

Build tools are programs or processes that transform your code into a production-ready version that browsers can understand. They handle tasks like bundling, minification, transpiling, and optimization.


### Popular Build Tools :

- CRA  → (Create React App) → Easy React setup
- **Vite** → Super fast modern dev tool
- **Webpack** → Highly customizable bundler for big apps
- **Parcel** → Zero-config bundler, easy for small projects


### Build Tool Analogy –> Package Delivery 

1. **Your App = Many small packages**
    
    - Every file (`App.js`, `index.js`, `style.css`) = a small parcel
        
2. **Problem if you send them individually:**
    
    - Delivery takes **too long** (browser has to download each file separately)
        
    - Packages may get **lost or delayed** (extra/unused code)
        
3. **Build Tool = Logistics Company**
    
    - **Bundler** → Combines all small parcels into **one big box** → faster delivery
        
    - **Transpiler** → Converts “special items” (JSX/modern JS) into standard items the recipient (browser) can understand
        
    - **Optimizer** → Removes extra packing materials → lighter, faster to deliver
        
4. **Result = One big ready-to-use package**
    
    - Browser receives the “big box” → unpacks everything quickly → app works smoothly

### In short : 

> **Build Tool = Logistics Company**
> 
> - Converts special code → readable code
>     
> - Combines many files → one fast-loading bundle
>     
> - Optimizes size → faster delivery and better performance




### Diffing (Reconciliation Algorithm): 


- React **compares old Virtual DOM vs new Virtual DOM** using **diffing algorithm**.
    
#### Algorithm Details : 

- React uses a **heuristic O(n) diffing algorithm** instead of deep comparison (which would be slower).
    
- Key rules:
    
    1. **Element type matters**
        
        - `<div>` vs `<p>` → replace entire node
            
        - Same type → only update props/children
            
    2. **Keys for Lists**
        
        - For arrays/lists of elements, React uses **`key` prop** to track which items are added/removed/updated efficiently
            
    3. **Minimal updates**
        
        - Only changed nodes are marked for **commit to real DOM**

---

## Algorithms Used: 

1. **Virtual DOM Diffing Algorithm**
    
    - **O(n)** heuristic algorithm
        
    - Compares **node types first** → if same, compares props/children → recursively applies to tree
        
    - Uses **keys for list reconciliation**
        
2. **Fiber Architecture (React 16+)**
    
    - Introduces **incremental rendering**
        
    - Splits the render/reconciliation work into **units of work** (fibers)
        
    - Allows React to **pause, prioritize, and resume work**
        
    - Supports **concurrent mode** → smoother UI updates

### Key Points : 

- **Virtual DOM →  in-memory JS object** → cheap to compare
    
- **Diffing = smart comparison** → detects exactly what changed
    
- **Fiber = React’s scheduler** → efficiently updates DOM without blocking the main thread 
    
- **Real DOM updated minimally** → fast, smooth UI

---

## Complete React Rendering Pipeline

1. **Render Phase:**
    
    - Component rendering (calling component functions/render methods)
    - Virtual DOM creation
    - Reconciliation (with diffing):
        - Tree comparison
        - Element type checking
        - Props comparison
        - Children reconciliation
        - Creation of a list of updates needed
2. **Commit Phase:**
    
    - DOM node creation for new elements
    - DOM node removal for deleted elements
    - Property and attribute updates on existing DOM nodes
    - Event listener attachment/detachment
    - Reference updates
    - Lifecycle method calls (componentDidMount, componentDidUpdate, useLayoutEffect)



Refer this Blog for the In depth Knowledge  : 

https://www.deepintodev.com/blog/how-react-works-behind-the-scenes 



---

## Dependency vs DevDependency

### Dependencies

- These are **packages your app needs to run** in **production**.
- Without them, your app **won’t work**.
- They’re required when your app is actually being **used by the user**.

👉 Installed when you run:

```bash
npm install package-name

```

**Example:**

```json
"dependencies": {
  "react": "^18.2.0",
  "react-dom": "^18.2.0",
  "axios": "^1.6.0"
}

```

✅ Used at runtime (browser or server).

=======================

### DevDependencies: 

- These are **packages only needed while developing** your app — not when running it.
- They’re used for **building, testing, linting, bundling, etc.**
- They are **not included** in the production build.

👉 Installed when you run:

```bash
npm install package-name --save-dev # shorthand -D instead of --save-dev 

```


**Example:**

```json
"devDependencies": {
  "vite": "^5.0.0",
  "eslint": "^9.0.0",
  "jest": "^29.7.0"
}

```

✅ Used only during **development** (not in runtime).



## In short :

| Type                | Used When                              | Example Packages                    | Installed in Production? |
| ------------------- | -------------------------------------- | ----------------------------------- | ------------------------ |
| **dependencies**    | When app runs (runtime)                | `react`, `express`, `axios`         | ✅ Yes                    |
| **devDependencies** | When app is built/tested (development) | `vite`, `webpack`, `jest`, `eslint` | ❌ No                     |

---

### Simple Real-Life Analogy: 

Think of your project like a **restaurant** 🍽️:

- **Dependencies** → The **ingredients** you need to cook and serve food (customers can’t eat without them).
- **DevDependencies** → The **kitchen tools** you use to prepare food (knife, stove, apron).
    - Customers (production) never see these tools; they only see the final food.

---


> Dependencies = Needed to run the app
> 
> **DevDependencies = Needed to build or test the app**




