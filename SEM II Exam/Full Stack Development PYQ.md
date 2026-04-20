# 🔥 FSD – Q1 (12 marks, EASY SCORING)

Attempt any 6 → I’ll give ALL.

---

## 🔹 a) let and const

**Answer:**

- `let` → block-scoped variable, can be reassigned
    
- `const` → block-scoped, cannot be reassigned
    

Example:

```js
let x = 10;
const y = 20;
```

---

## 🔹 b) Arrow Functions

**Answer:**  
Short syntax for functions using `=>`

```js
const add = (a, b) => a + b;
```

---

## 🔹 c) Template Literals

**Answer:**  
Used for string interpolation using backticks `` ` ``

```js
let name = "Harsh";
console.log(`Hello ${name}`);
```

---

## 🔹 d) Advantages of TypeScript

**Answer:**

- Static typing
    
- Better error detection
    
- Supports OOP
    
- Improves code maintainability
    

---

## 🔹 e) Node.js

**Answer:**  
Node.js is a **JavaScript runtime** used for building **server-side applications**.

---

## 🔹 f) Features of React.js

**Answer:**

- Component-based
    
- Virtual DOM
    
- Reusable components
    
- Fast rendering
    

---

## 🔹 g) Components in React

**Answer:**  
Components are reusable building blocks of UI.

---

## 🔹 h) Controlled Components

**Answer:**  
Form elements controlled by React state.

---

# 🎯 MOST IMPORTANT (Q1)

👉 Always comes:

- Arrow functions
    
- Node.js
    
- React features
    
- TypeScript
    

---

# 🔥 Q2 (VERY IMPORTANT)

---

## 🔹 (i) Functional vs OOP

**Answer:**

|Functional|OOP|
|---|---|
|Uses functions|Uses objects|
|Stateless|Stateful|
|Immutability|Mutable data|
|Example: FP|Example: Java|

---

## 🔹 (ii) Enums in TypeScript

**Answer:**

Enums define named constants.

```ts
enum Color {
  Red,
  Green,
  Blue
}
```

---

## 🔹 Props in React

**Answer (VERY IMPORTANT):**

Props are used to pass data between components.

Example:

```jsx
function Child(props) {
  return <h1>{props.name}</h1>;
}

function App() {
  return <Child name="Harsh" />;
}
```

---

# 🔥 Q3 (IMPORTANT)

---

## 🔹 Node.js Architecture (VERY IMPORTANT)

**Answer:**

Node.js uses:

- **Single-threaded**
    
- **Event-driven architecture**
    
- **Non-blocking I/O**
    

### Flow:

1. Client request
    
2. Event loop handles request
    
3. Callback executed
    

👉 Write “Event Loop” → guaranteed marks

---

## 🔹 Generics in TypeScript

**Answer:**

Generics allow reusable components.

```ts
function identity<T>(value: T): T {
  return value;
}
```

---

## 🔹 Interactive Props

**Answer:**  
Used in dynamic forms to update UI based on user input.

---

# 🔥 Q4 (VERY IMPORTANT)

---

## 🔹 Event Handling in React vs JS

**Answer:**

|React|Traditional JS|
|---|---|
|Uses synthetic events|Uses DOM events|
|JSX syntax|addEventListener|

---

## 🔹 Async Programming in Node.js

**Answer:**

- Improves performance
    
- Handles multiple requests
    
- Uses callbacks, promises
    

---

## 🔹 Immutable Data Structures

**Answer:**

- Data cannot be modified
    
- Improves predictability
    
- Used in FP
    

---

# 🔥 Q5 (IMPORTANT)

---

## 🔹 TypeScript OOP vs JS Prototype

**Answer:**

|TypeScript|JavaScript|
|---|---|
|Class-based|Prototype-based|
|Strong typing|Weak typing|

---

## 🔹 Uncontrolled Components

**Answer:**  
Uses DOM instead of React state.

---

## 🔹 WebSockets (VERY IMPORTANT)

**Answer:**

- Enables real-time communication
    
- Full-duplex connection
    
- Used in chat apps
    

---

# 🔥 Q6 (VERY IMPORTANT)

---

## 🔹 Virtual DOM (MOST EXPECTED)

**Answer:**

Virtual DOM is a lightweight copy of real DOM.

Benefits:

- Faster updates
    
- Efficient rendering
    

---

## 🔹 Type Narrowing

**Answer:**  
Refining type during runtime.

---

## 🔹 JSX

**Answer:**  
JSX allows writing HTML inside JavaScript.

---

# 🔥 Q7 (VERY IMPORTANT)

---

## 🔹 Async/Await vs Promises

**Answer:**

|Async/Await|Promises|
|---|---|
|Cleaner syntax|Complex chaining|
|Easier to read|Harder to manage|

---

## 🔹 Currying

**Answer:**  
Function returning another function.

```js
const add = a => b => a + b;
```

---

## 🔹 Props vs State (VERY IMPORTANT)

**Answer:**

|Props|State|
|---|---|
|Read-only|Mutable|
|Passed from parent|Managed inside component|

---

# 🚀 FSD FINAL ANALYSIS

From PYQ:

### 🔥 MOST REPEATED:

- Node.js architecture ✅
    
- Props vs State ✅
    
- Virtual DOM ✅
    
- Async/Await ✅
    
- TypeScript basics ✅
    

👉 These alone = 70% paper

---

# ⚠️ IMPORTANT TIP

For FSD:  
👉 Write **examples in every answer**

Even small code = +1 to +2 marks

---
