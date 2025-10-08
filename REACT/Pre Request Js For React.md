

## What is the Spread Operator?

The **spread operator** is written as **three dots (`...`)**.

It **expands an iterable (like an array or object) into individual elements or properties**.

Think of it as “spreading out” all the items inside an array or object.

---

## ⚡ 1. Spread Operator with Arrays

### Example 1: Copying an array

```jsx
const numbers = [1, 2, 3];
const copy = [...numbers];
console.log(copy); // [1, 2, 3]

```

✅ Works like a **shallow copy** of the array.

---

### Example 2: Merging arrays

```jsx
const arr1 = [1, 2];
const arr2 = [3, 4];
const merged = [...arr1, ...arr2];
console.log(merged); // [1, 2, 3, 4]

```

---

### Example 3: Adding elements

```jsx
const fruits = ["apple", "banana"];
const newFruits = ["mango", ...fruits, "orange"];
console.log(newFruits); // ["mango", "apple", "banana", "orange"]

```

---

## ⚡ 2. Spread Operator with Objects

### Example 1: Copying objects

```jsx
const user = { name: "Dharani", age: 20 };
const copyUser = { ...user };
console.log(copyUser); // { name: "Dharani", age: 20 }

```

---

### Example 2: Merging objects

```jsx
const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };
const merged = { ...obj1, ...obj2 };
console.log(merged); // { a: 1, b: 3, c: 4 }

```

✅ Notice: **Later properties overwrite earlier ones** (`b: 3` overwrites `b: 2`)

---

### Example 3: Adding properties

```jsx
const user = { name: "Dharani" };
const newUser = { ...user, age: 20 };
console.log(newUser); // { name: "Dharani", age: 20 }

```

---

## ⚡ 3. Spread Operator in Function Calls

You can use it to **pass array elements as individual arguments**:

```jsx
const numbers = [1, 2, 3];
function sum(a, b, c) {
  return a + b + c;
}

console.log(sum(...numbers)); // 6

```

## 🧩 2. Rest Operator (`...`)

**Purpose:** “Collects” multiple elements into a single array or object.

**Used in:** **function parameters, destructuring assignment**

---

### Example 1: With Function Parameters

```jsx
function sum(...numbers) {  // 'numbers' is an array of all arguments
  return numbers.reduce((a, b) => a + b, 0);
}

console.log(sum(1, 2, 3, 4)); // 10

```

Here, `...numbers` **collects all arguments** into an array.

---

### Example 2: With Array Destructuring

```jsx
const [first, ...rest] = [1, 2, 3, 4];
console.log(first); // 1
console.log(rest);  // [2, 3, 4]

```

- `first` = first element
- `rest` = array of remaining elements

---

### Example 3: With Object Destructuring

```jsx
const { a, ...others } = { a: 1, b: 2, c: 3 };
console.log(a);      // 1
console.log(others); // { b: 2, c: 3 }

```

- `a` = extracted property
- `others` = object with remaining properties

---

## 🧭 Key Difference

|Operator|Meaning|Example|Context|
|---|---|---|---|
|Spread (`...`)|“Expand”|`[...arr]` or `{...obj}`|Arrays, objects, function calls, JSX|
|Rest (`...`)|“Collect”|`function(...args)` or `const [first, ...rest]`|Function parameters, destructuring|