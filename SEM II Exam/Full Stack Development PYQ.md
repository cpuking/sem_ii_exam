# 🔥 Full Stack Development – Previous Year Questions (Actual Paper)

**Subject:** Full Stack Development | **Code:** MSCOSDSC 202  
**Class:** M.Sc. Computer Science I (Semester II) | **Pattern:** 2024 (NEP)  
**Time:** 2.5 Hours | **Max. Marks:** 60

**Related:** [[Full Stack Development Notes]] | [[Full Stack Development QB]] | [[README]]

---

> 📌 **Instructions:**
> 
> 1. Question 1 is compulsory.
> 2. Solve any **four** questions from Q2 to Q7.
> 3. Questions 2 to 7 carry equal marks (12 marks each).

---

## Q1) Solve any 6 of the following — [6 × 2 = 12 marks]

_Write: Definition + 1 example. Keep each answer to 4–6 lines._

---

### a) Define `let` and `const` in ES6 _(2 marks)_

→ See: [[Full Stack Development Notes#1.1 let and const]]

**Answer:**

`let` and `const` are **block-scoped** variable declaration keywords introduced in ES6, replacing the problematic `var`.

|Keyword|Scope|Reassignable|Re-declarable|
|---|---|---|---|
|`var`|Function-scoped|✅ Yes|✅ Yes|
|`let`|Block-scoped|✅ Yes|❌ No|
|`const`|Block-scoped|❌ No|❌ No|

```js
let age = 20;
age = 21;          // ✅ allowed

const PI = 3.14;
// PI = 3.15;      // ❌ TypeError: Assignment to constant variable
```

> **Key point:** `const` prevents reassignment of the variable reference, but for objects/arrays, the content can still be modified.

---

### b) Define Arrow Functions with an example _(2 marks)_

→ See: [[Full Stack Development Notes#1.2 Arrow Functions]]

**Answer:**

Arrow functions are a **shorter syntax** for writing functions using the `=>` (fat arrow) operator, introduced in ES6. They also **do not bind their own `this`**, inheriting it from the surrounding scope.

**Syntax:** `const funcName = (params) => expression`

```js
// Traditional function
function add(a, b) {
    return a + b;
}

// Arrow function — single line (implicit return)
const add = (a, b) => a + b;

// With single parameter — no parentheses needed
const square = x => x * x;

// With no parameters
const greet = () => "Hello World!";

console.log(add(3, 4));    // 7
console.log(square(5));    // 25
```

---

### c) Define Template Literals and their usage _(2 marks)_

→ See: [[Full Stack Development Notes#1.3 Template Literals]]

**Answer:**

Template literals are **string literals** enclosed in backticks (`` ` ``) that allow:

1. **String interpolation** using `${}` — embed expressions directly
2. **Multi-line strings** without `\n`
3. **Expression evaluation** inside `${}`

```js
const name = "Harsh";
const age = 20;

// Old way (concatenation)
const old = "Hello " + name + ", you are " + age + " years old.";

// Template literal (modern)
const modern = `Hello ${name}, you are ${age} years old.`;

// Multi-line
const html = `
    <div>
        <h1>${name}</h1>
        <p>Age: ${age}</p>
        <p>Next year: ${age + 1}</p>
    </div>
`;
```

---

### d) Define the advantages of using TypeScript over JavaScript _(2 marks)_

→ See: [[Full Stack Development Notes#2.1 What is TypeScript?]]

**Answer:**

TypeScript is a **superset of JavaScript** with static typing. Key advantages:

|Advantage|Explanation|
|---|---|
|**Static typing**|Types checked at compile time, not runtime — bugs caught early|
|**Better error detection**|TypeScript shows errors before code runs|
|**OOP support**|Interfaces, classes, access modifiers (`private`, `protected`)|
|**Code maintainability**|Easier to refactor large codebases|
|**IDE support**|Better autocomplete, navigation, refactoring|
|**Generics**|Reusable, type-safe components|

```ts
// TypeScript catches this bug at COMPILE TIME:
function add(a: number, b: number): number {
    return a + b;
}
add("hello", 2);  // ❌ Error: Argument of type 'string' is not assignable to 'number'
// JavaScript would silently give wrong result: "hello2"
```

---

### e) Define Node.js and its main purpose _(2 marks)_

→ See: [[Full Stack Development Notes#3.1 What is Node.js?]]

**Answer:**

**Node.js** is an **open-source, cross-platform JavaScript runtime environment** that allows JavaScript to run **on the server side** (outside the browser). It is built on Chrome's **V8 JavaScript engine**.

**Main purpose:**

- Run JavaScript on the server (not just in browsers)
- Build **scalable network applications** (APIs, real-time apps)
- Handle many concurrent requests efficiently using **non-blocking I/O**

```js
// Simple HTTP server in Node.js
const http = require('http');

const server = http.createServer((req, res) => {
    res.end('Hello from Node.js server!');
});

server.listen(3000, () => console.log('Server running on port 3000'));
```

**Use cases:** REST APIs, real-time chat, streaming, microservices

---

### f) Define the key features of React.js _(2 marks)_

→ See: [[Full Stack Development Notes#4.1 What is React?]]

**Answer:**

React.js is an open-source **JavaScript library** by Facebook for building user interfaces.

**Key features:**

|Feature|Description|
|---|---|
|**Component-based**|UI is split into reusable, independent components|
|**Virtual DOM**|Lightweight copy of real DOM → faster updates via diffing|
|**Unidirectional data flow**|Data flows one way: parent → child via props|
|**JSX**|Write HTML-like syntax inside JavaScript|
|**Declarative UI**|Describe what UI should look like, React handles how|
|**Reusable components**|Write once, use anywhere|
|**Hooks**|`useState`, `useEffect` for state and lifecycle in functional components|

---

### g) Define the concept of components in React.js _(2 marks)_

→ See: [[Full Stack Development Notes#4.3 Components]]

**Answer:**

**Components** are the **fundamental building blocks** of a React application. A component is an independent, reusable piece of UI that:

- Accepts inputs called **props**
- Returns React elements (JSX) describing what should appear on screen
- Can manage its own **state**

**Two types:**

```jsx
// 1. Functional Component (modern, preferred)
function Welcome({ name }) {
    return <h1>Hello, {name}!</h1>;
}

// 2. Class Component (older style)
class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}!</h1>;
    }
}

// Usage — both render the same
<Welcome name="Harsh" />
```

---

### h) Define Controlled Components in React _(2 marks)_

→ See: [[Full Stack Development Notes#4.10 Controlled vs Uncontrolled Components]]

**Answer:**

A **controlled component** is a form element whose value is **controlled by React state**. The React component is the "single source of truth" — every state mutation has an associated handler function.

```jsx
import { useState } from 'react';

function ControlledInput() {
    const [value, setValue] = useState('');

    return (
        <div>
            {/* value is controlled by React state */}
            <input
                type="text"
                value={value}                           // tied to state
                onChange={(e) => setValue(e.target.value)}  // updates state
            />
            <p>You typed: {value}</p>
        </div>
    );
}
```

**Key characteristics:**

- Form data is handled by React state
- Every keystroke triggers a re-render
- Provides full control — easy validation, conditional formatting

---

## Q2) Attempt the following — [12 marks]

---

### Q2 a) i) Key differences between Functional and Object-Oriented Programming _(4 marks)_

→ See: [[Full Stack Development Notes#Unit 1 – JavaScript ES6+]]

**Answer:**

Functional Programming (FP) and Object-Oriented Programming (OOP) are two major **programming paradigms** with fundamentally different approaches to solving problems.

**Detailed Comparison:**

|Feature|Functional Programming|Object-Oriented Programming|
|---|---|---|
|**Core concept**|Everything is a function/expression|Everything is an object|
|**State**|Stateless — avoids changing state|Stateful — objects hold state|
|**Data**|Immutable (data is not changed)|Mutable (objects can be modified)|
|**Code organization**|Functions and transformations|Classes and objects|
|**Reuse**|Function composition|Inheritance and polymorphism|
|**Side effects**|Avoided (pure functions)|Common (methods change state)|
|**Control flow**|Recursion, map/filter/reduce|Loops, method calls|
|**Examples**|Haskell, Scala, Python (FP style)|Java, C++, Python (OOP style)|
|**Debugging**|Easier (pure functions = predictable)|Harder (shared mutable state)|
|**Concurrency**|Safe (no shared state)|Risk of race conditions|

**Code comparison:**

```js
// Functional approach (immutable, pure)
const numbers = [1, 2, 3, 4, 5];
const doubledEvens = numbers
    .filter(n => n % 2 === 0)   // [2, 4]
    .map(n => n * 2);            // [4, 8]

// OOP approach (stateful)
class NumberProcessor {
    constructor(numbers) {
        this.numbers = numbers;
    }
    doubledEvens() {
        return this.numbers
            .filter(n => n % 2 === 0)
            .map(n => n * 2);
    }
}
const p = new NumberProcessor([1,2,3,4,5]);
p.doubledEvens();  // [4, 8]
```

---

### Q2 a) ii) Use of Enums in TypeScript with examples _(3 marks)_

→ See: [[Full Stack Development Notes#2.4 Enums]]

**Answer:**

**Enums** (Enumerations) in TypeScript allow defining a **set of named constants**, making code more readable and preventing invalid values.

**Why use Enums?**

- Replace "magic strings/numbers" with meaningful names
- Type-safe — only valid enum values accepted
- Improve code readability and maintainability

**Types of Enums:**

```ts
// 1. Numeric Enum (default — values are 0, 1, 2...)
enum Direction {
    Up,     // 0
    Down,   // 1
    Left,   // 2
    Right   // 3
}

let move: Direction = Direction.Up;
console.log(move);           // 0
console.log(Direction[0]);   // "Up"

// 2. String Enum (explicit string values)
enum Status {
    Pending  = "PENDING",
    Active   = "ACTIVE",
    Inactive = "INACTIVE"
}

let userStatus: Status = Status.Active;
console.log(userStatus);   // "ACTIVE"

// 3. Practical use in function
function handleDirection(dir: Direction) {
    if (dir === Direction.Up) {
        console.log("Moving up!");
    }
}
handleDirection(Direction.Up);    // ✅ Valid
// handleDirection(10);            // ❌ Type error — safer code
```

---

### Q2 b) Explain props in React.js with an example of passing data between components _(5 marks)_

→ See: [[Full Stack Development Notes#4.4 Props]]

**Answer:**

**Props** (short for "properties") are the mechanism in React for **passing data from a parent component to a child component**. They are the primary way components communicate with each other.

**Key characteristics of Props:**

1. **Read-only** — child cannot modify the props it receives
2. **Unidirectional** — data flows only from parent → child
3. **Any type** — can be strings, numbers, objects, arrays, or even functions
4. **Immutable** — props should never be changed by the receiving component

**How data flows:**

```
Parent Component
       │
       │ passes props
       ↓
Child Component (receives and displays)
```

**Detailed Example:**

```jsx
// === CHILD COMPONENT ===
// Receives 'name', 'age', 'city' as props
function UserCard({ name, age, city }) {
    return (
        <div className="card" style={{ border: '1px solid #ccc', padding: '10px' }}>
            <h2>{name}</h2>
            <p>Age: {age}</p>
            <p>City: {city}</p>
        </div>
    );
}

// === ANOTHER CHILD — Button with function prop ===
function ActionButton({ label, onClick }) {
    return <button onClick={onClick}>{label}</button>;
}

// === PARENT COMPONENT ===
// Passes different data to same child component — reusability!
function App() {
    const handleClick = () => alert("Button clicked!");

    return (
        <div>
            <h1>User Profiles</h1>

            {/* Passing string and number props */}
            <UserCard name="Harsh" age={20} city="Pune" />
            <UserCard name="Rahul" age={21} city="Mumbai" />
            <UserCard name="Priya" age={19} city="Delhi" />

            {/* Passing a function as prop */}
            <ActionButton label="Click Me" onClick={handleClick} />
        </div>
    );
}
```

**Props with default values:**

```jsx
function Greeting({ name = "Guest", role = "User" }) {
    return <p>Welcome, {name}! You are a {role}.</p>;
}

<Greeting />                          // "Welcome, Guest! You are a User."
<Greeting name="Harsh" role="Admin" /> // "Welcome, Harsh! You are a Admin."
```

**Passing object as prop:**

```jsx
function Profile({ user }) {
    return (
        <div>
            <h2>{user.name}</h2>
            <p>{user.email}</p>
        </div>
    );
}

const userData = { name: "Harsh", email: "harsh@example.com" };
<Profile user={userData} />
```

> **Summary:** Props enable component reusability — the same `UserCard` component can display different data based on what the parent passes. This is the foundation of React's component composition.

---

## Q3) Attempt the following — [12 marks]

---

### Q3 a) i) Describe the architecture and working of Node.js _(4 marks)_

→ See: [[Full Stack Development Notes#3.2 Node.js Architecture]]

**Answer:**

Node.js is built on a **Single-Threaded, Event-Driven, Non-Blocking I/O** architecture, which makes it highly scalable despite using only one thread.

**Core Components:**

|Component|Description|
|---|---|
|**V8 Engine**|Google's JavaScript engine that compiles JS to machine code|
|**libuv**|C library providing event loop, thread pool, async I/O|
|**Event Loop**|Continuously checks for tasks; core of Node's async behavior|
|**Thread Pool**|Handles heavy blocking operations (file I/O, crypto)|
|**Callback Queue**|Holds callbacks ready to be executed|

**Architecture Diagram:**

```
Client Request
      │
      ▼
┌─────────────────────────────────────┐
│           Node.js Process           │
│                                     │
│  ┌──────────────────────────────┐   │
│  │    Single-Threaded           │   │
│  │    Event Loop (libuv)        │   │
│  │                              │   │
│  │  Is the task blocking? ──Yes─┼───┤──► Thread Pool (4 threads)
│  │          │                   │   │         │
│  │          No                  │   │    (file I/O, DB, DNS)
│  │          │                   │   │         │
│  │   Execute directly           │   │    Callback returned
│  └──────────────────────────────┘   │         │
│              │                      │         │
│         Callback Queue  ◄───────────┘         │
│              │                                │
│         Execute Callback                      │
└─────────────────────────────────────┘
      │
      ▼
  Send Response to Client
```

**How it works — Step by Step:**

1. Client sends request (e.g., read a file)
2. Event loop receives the request
3. If **non-blocking** (simple computation): executes immediately
4. If **blocking** (file read, DB query): offloaded to **thread pool**
5. Thread pool processes it asynchronously
6. When done, result + callback placed in **callback queue**
7. Event loop picks up callback and executes it
8. Response sent to client

**Working example:**

```js
console.log("1. Request received");

// Blocking task — sent to thread pool
fs.readFile('data.txt', (err, data) => {
    console.log("3. File read complete:", data);
});

// This runs IMMEDIATELY without waiting for file
console.log("2. Other work continues");

// Output:
// 1. Request received
// 2. Other work continues
// 3. File read complete: [file contents]
```

**Why this is powerful:**

- One thread handles thousands of concurrent connections
- While one request waits for DB, other requests are processed
- No thread context-switching overhead → high performance

---

### Q3 a) ii) Concept of Generics in TypeScript and their benefits _(3 marks)_

→ See: [[Full Stack Development Notes#2.5 Generics]]

**Answer:**

**Generics** allow writing **reusable, type-safe** code that works with **any data type**, while still maintaining type information. They use a **type parameter** (commonly `T`) as a placeholder for the actual type.

**Problem without generics:**

```ts
// Using 'any' — loses type information
function getFirst(arr: any[]): any {
    return arr[0];
}
const result = getFirst([1, 2, 3]);
result.toUpperCase();  // No error! But will crash at runtime
```

**Solution with generics:**

```ts
// Generic function — type is preserved
function getFirst<T>(arr: T[]): T {
    return arr[0];
}

const num = getFirst<number>([1, 2, 3]);   // num is typed as 'number'
const str = getFirst<string>(["a","b"]);   // str is typed as 'string'

// num.toUpperCase(); ❌ Compile-time error — 'number' has no 'toUpperCase'
str.toUpperCase();    // ✅ Fine — TypeScript knows it's a string
```

**Generic class:**

```ts
class Stack<T> {
    private items: T[] = [];

    push(item: T): void {
        this.items.push(item);
    }

    pop(): T | undefined {
        return this.items.pop();
    }

    peek(): T | undefined {
        return this.items[this.items.length - 1];
    }
}

const numStack = new Stack<number>();
numStack.push(1);
numStack.push(2);
console.log(numStack.pop());  // 2
```

**Benefits of Generics:**

|Benefit|Explanation|
|---|---|
|**Reusability**|One function/class works for all types|
|**Type safety**|Errors caught at compile time|
|**No type casting**|No need for explicit casting|
|**Better IDE support**|Autocomplete works correctly|

---

### Q3 b) Explain the significance of interactive props in dynamic forms _(5 marks)_

**Answer:**

**Interactive props** in dynamic forms refer to using **props + state + event handlers** together to create form components that **respond to user input in real time**, validate data, and communicate changes back to parent components.

**Why interactive props matter in forms:**

1. Enable **real-time validation** as user types
2. Allow **conditional rendering** based on form data
3. Support **data sharing** between form fields and other components
4. Enable **dynamic behavior** — show/hide fields, enable/disable buttons

**Complete dynamic form example:**

```jsx
import { useState } from 'react';

// Reusable Input component with interactive props
function FormInput({ label, value, onChange, error, type = "text" }) {
    return (
        <div style={{ marginBottom: '15px' }}>
            <label>{label}</label>
            <input
                type={type}
                value={value}           // prop: controlled value
                onChange={onChange}     // prop: event handler from parent
                style={{ borderColor: error ? 'red' : 'green' }}
            />
            {error && <span style={{ color: 'red' }}>{error}</span>}
        </div>
    );
}

// Submit button with interactive disabled prop
function SubmitButton({ isValid, onSubmit }) {
    return (
        <button
            onClick={onSubmit}
            disabled={!isValid}         // prop controls enabled/disabled
            style={{ opacity: isValid ? 1 : 0.5 }}
        >
            {isValid ? "Submit" : "Fill all fields"}
        </button>
    );
}

// Parent form — manages state, passes interactive props down
function RegistrationForm() {
    const [form, setForm] = useState({ name: '', email: '', password: '' });
    const [errors, setErrors] = useState({});

    // Validate in real time as user types
    const validate = (field, value) => {
        if (field === 'name' && value.length < 2)
            return "Name must be at least 2 characters";
        if (field === 'email' && !value.includes('@'))
            return "Enter a valid email";
        if (field === 'password' && value.length < 6)
            return "Password must be at least 6 characters";
        return '';
    };

    const handleChange = (field) => (e) => {
        const value = e.target.value;
        setForm({ ...form, [field]: value });
        setErrors({ ...errors, [field]: validate(field, value) });
    };

    const isFormValid = !errors.name && !errors.email && !errors.password
                     && form.name && form.email && form.password;

    const handleSubmit = () => {
        alert(`Registered: ${form.name}`);
    };

    return (
        <form>
            <FormInput
                label="Name"
                value={form.name}
                onChange={handleChange('name')}
                error={errors.name}
            />
            <FormInput
                label="Email"
                value={form.email}
                onChange={handleChange('email')}
                error={errors.email}
            />
            <FormInput
                label="Password"
                type="password"
                value={form.password}
                onChange={handleChange('password')}
                error={errors.password}
            />
            <SubmitButton isValid={isFormValid} onSubmit={handleSubmit} />
        </form>
    );
}
```

**Key interactive props used:**

- `value` → controlled value (input is controlled by parent state)
- `onChange` → function prop — child notifies parent of changes
- `error` → validation message prop
- `disabled` → dynamic button state based on form validity
- `type` → controls input behavior (text/password/email)

---

## Q4) Attempt the following — [12 marks]

---

### Q4 a) i) How event handling in React.js differs from traditional JavaScript _(4 marks)_

→ See: [[Full Stack Development Notes#4.9 Event Handling in React]]

**Answer:**

React uses a **Synthetic Event System** that wraps native browser events, providing a cross-browser compatible API. This differs significantly from traditional JavaScript DOM event handling.

**Detailed Comparison:**

|Feature|React|Traditional JavaScript|
|---|---|---|
|**Event naming**|camelCase (`onClick`, `onChange`)|lowercase (`onclick`, `onchange`)|
|**Event binding**|JSX attribute: `onClick={handler}`|`addEventListener('click', handler)`|
|**Event object**|Synthetic event (cross-browser)|Native DOM event (browser-specific)|
|**Prevent default**|`e.preventDefault()` explicitly|`return false` or `e.preventDefault()`|
|**Context (`this`)**|Arrow functions or `.bind()` needed in class|Depends on binding|
|**Performance**|Event delegation — one listener at root|Listener per element|
|**Remove listener**|Automatic (component unmounts)|Manual `removeEventListener`|

**Code Comparison:**

```html
<!-- Traditional JavaScript -->
<button id="myBtn">Click Me</button>

<script>
    // Imperative style — attach listener to DOM
    document.getElementById('myBtn')
        .addEventListener('click', function(event) {
            event.preventDefault();
            console.log("Clicked!", event.target);
        });

    // Must manually remove when done
    // element.removeEventListener('click', handler);
</script>
```

```jsx
// React — Declarative style
function MyButton() {
    const handleClick = (e) => {
        e.preventDefault();
        console.log("Clicked!", e.target);
    };

    return (
        // No need to select DOM element
        <button onClick={handleClick}>Click Me</button>
    );
}
```

**Passing arguments in React:**

```jsx
function ItemList() {
    const handleDelete = (id, e) => {
        e.stopPropagation();
        console.log("Deleting item:", id);
    };

    return (
        <ul>
            {[1, 2, 3].map(id => (
                <li key={id}>
                    Item {id}
                    <button onClick={(e) => handleDelete(id, e)}>Delete</button>
                </li>
            ))}
        </ul>
    );
}
```

**Synthetic Event pooling (important concept):**

```jsx
// React reuses synthetic events for performance
function Example() {
    const handleClick = (e) => {
        console.log(e.type);     // "click" — works
        setTimeout(() => {
            console.log(e.type); // null — event is pooled/reused
        }, 1000);
    };
}
```

---

### Q4 a) ii) How asynchronous programming improves performance in Node.js _(3 marks)_

→ See: [[Full Stack Development Notes#3.4 Asynchronous Programming in Node.js]]

**Answer:**

Asynchronous programming allows Node.js to **start a task and move on without waiting** for it to complete, handling the result later via callbacks/promises. This dramatically improves performance and scalability.

**Why it improves performance:**

```
SYNCHRONOUS (blocking):
Request 1: [========DB Query (500ms)========] → Response 1
Request 2:                                      [========DB Query (500ms)========] → Response 2
Total time: 1000ms (sequential)

ASYNCHRONOUS (non-blocking):
Request 1: [DB Query started...              ]
Request 2:          [DB Query started...     ]
           [ ... both complete ... ]
Total time: ~500ms (parallel handling)
```

**Three techniques:**

```js
// 1. Callbacks (old, can lead to "callback hell")
fs.readFile('data.txt', (err, data) => {
    if (err) { console.error(err); return; }
    console.log(data);
});
console.log("This runs WITHOUT waiting for file read");

// 2. Promises (better — chainable)
fetch('https://api.example.com/users')
    .then(res => res.json())
    .then(data => console.log(data))
    .catch(err => console.error(err));

// 3. Async/Await (best — clean, readable)
async function getUsers() {
    try {
        const response = await fetch('https://api.example.com/users');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
```

**Performance benefit:** A synchronous server can handle maybe 100 concurrent users. The same Node.js server with async can handle **thousands** — because it never sits idle waiting.

---

### Q4 b) Advantages of using Immutable Data Structures in Functional Programming _(5 marks)_

→ See: [[Full Stack Development Notes#Unit 1 – JavaScript ES6+]]

**Answer:**

**Immutable data structures** are data structures whose state **cannot be changed after creation**. Instead of modifying existing data, new data is created with the desired changes. This concept is central to functional programming.

**Detailed Advantages:**

#### 1. Thread Safety / Concurrency

Since data never changes, multiple threads/processes can read it simultaneously without race conditions or locks.

```js
// Mutable — race condition possible
let counter = 0;
// Thread 1: counter++  (reads 0, writes 1)
// Thread 2: counter++  (reads 0, writes 1) ← both write 1 instead of 2!

// Immutable — safe
const counter = 0;
const newCounter1 = counter + 1;  // new value
const newCounter2 = counter + 1;  // also safe — no conflict
```

#### 2. Predictable Behavior / No Side Effects

A function using immutable data always produces the same output for the same input.

```js
// Mutable — function changes original (surprise!)
function addItem(cart, item) {
    cart.push(item);  // ❌ mutates the original array
    return cart;
}

// Immutable — original unchanged, new array created
function addItem(cart, item) {
    return [...cart, item];  // ✅ new array, original untouched
}
```

#### 3. Easier Debugging and Testing

Since values don't change, you can trace the state at any point in time.

```js
const original = { name: "Harsh", score: 80 };
const updated = { ...original, score: 95 };  // new object

console.log(original);  // { name: "Harsh", score: 80 }  — unchanged
console.log(updated);   // { name: "Harsh", score: 95 }  — new object
```

#### 4. Undo/Redo Functionality

Applications like text editors can easily implement undo because old states are preserved.

```js
const history = [];
let state = { text: "" };

function updateText(newText) {
    history.push(state);         // save old state
    state = { text: newText };   // new state (old preserved)
}

function undo() {
    state = history.pop();       // restore previous state
}
```

#### 5. React Performance Optimization

React uses immutability to decide if a re-render is needed — comparing object references is O(1).

```js
// With immutable updates, React can do:
if (prevState !== newState) {   // reference comparison — fast!
    rerender();
}
// vs deep comparison of mutable objects — very slow
```

**Summary table:**

|Advantage|Description|
|---|---|
|Thread-safe|No race conditions in concurrent programs|
|Predictable|Same input → always same output|
|Easy debugging|State history is preserved|
|Enables undo/redo|Previous states are not destroyed|
|React optimization|Fast reference equality checks|

---

## Q5) Attempt the following — [12 marks]

---

### Q5 a) i) TypeScript OOP features vs JavaScript's prototype-based approach _(4 marks)_

→ See: [[Full Stack Development Notes#2.7 TypeScript OOP vs JavaScript Prototype]]

**Answer:**

JavaScript uses a **prototype-based** inheritance model, while TypeScript adds **class-based OOP** features on top of it, making it more intuitive for developers from Java/C++ backgrounds.

**Comparison:**

|Feature|TypeScript OOP|JavaScript Prototype|
|---|---|---|
|**Syntax**|Clean `class` keyword|Function constructors + `prototype`|
|**Typing**|Strong static types|No types|
|**Access modifiers**|`public`, `private`, `protected`|All properties are public|
|**Inheritance**|`extends` keyword|`Object.setPrototypeOf()` or `__proto__`|
|**Interfaces**|✅ Supported|❌ Not available|
|**Abstract classes**|✅ Supported|❌ Not available|
|**Readability**|✅ Clean, structured|❌ Verbose, less intuitive|
|**Error detection**|✅ Compile-time errors|❌ Runtime errors only|

**TypeScript OOP:**

```ts
// Abstract class
abstract class Animal {
    private name: string;  // private — only accessible inside class

    constructor(name: string) {
        this.name = name;
    }

    public getName(): string { return this.name; }
    abstract makeSound(): string;  // must be implemented by subclass
}

// Inheritance
class Dog extends Animal {
    private breed: string;

    constructor(name: string, breed: string) {
        super(name);   // call parent constructor
        this.breed = breed;
    }

    makeSound(): string {
        return `${this.getName()} says: Woof!`;
    }
}

const dog = new Dog("Rex", "Labrador");
console.log(dog.makeSound());  // "Rex says: Woof!"
// console.log(dog.name);      // ❌ Error: 'name' is private
```

**JavaScript prototype equivalent (older, messier):**

```js
function Animal(name) {
    // No access modifiers — name is public
    this.name = name;
}

Animal.prototype.getName = function() {
    return this.name;
};

function Dog(name, breed) {
    Animal.call(this, name);  // call parent
    this.breed = breed;
}

// Set up prototype chain manually
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.makeSound = function() {
    return this.getName() + " says: Woof!";
};

const dog = new Dog("Rex", "Labrador");
console.log(dog.makeSound());  // "Rex says: Woof!"
```

> **Conclusion:** TypeScript's OOP is significantly cleaner, type-safe, and less error-prone. The JavaScript prototype approach achieves the same result but with more complexity and no type safety.

---

### Q5 a) ii) Role of Uncontrolled Components in Form Handling _(3 marks)_

→ See: [[Full Stack Development Notes#4.10 Controlled vs Uncontrolled Components]]

**Answer:**

An **uncontrolled component** is a form element that **manages its own state internally in the DOM**, rather than through React state. The value is accessed using a `ref` (reference to the DOM element).

```jsx
import { useRef } from 'react';

function UncontrolledForm() {
    // ref holds reference to the DOM input element
    const nameRef = useRef();
    const emailRef = useRef();

    const handleSubmit = (e) => {
        e.preventDefault();
        // Access DOM values directly via ref
        console.log("Name:", nameRef.current.value);
        console.log("Email:", emailRef.current.value);
    };

    return (
        <form onSubmit={handleSubmit}>
            {/* No value prop, no onChange — DOM manages the value */}
            <input type="text" ref={nameRef} placeholder="Name" />
            <input type="email" ref={emailRef} placeholder="Email" />
            <button type="submit">Submit</button>
        </form>
    );
}
```

**When to use uncontrolled components:**

|Use Case|Reason|
|---|---|
|File inputs (`<input type="file">`)|File inputs can only be uncontrolled in React|
|Integrating with non-React code|Direct DOM access needed|
|Simple forms with no validation|Less code overhead|
|Third-party DOM libraries|Direct DOM manipulation required|

**Controlled vs Uncontrolled:**

||Controlled|Uncontrolled|
|---|---|---|
|Data location|React state|DOM|
|Access value|State variable|`ref.current.value`|
|Validation|Real-time, easy|On submit only|
|Re-renders|Yes (on every change)|No unnecessary re-renders|
|Preferred?|✅ Most cases|Only when necessary|

---

### Q5 b) WebSockets and their role in building real-time applications using Node.js _(5 marks)_

→ See: [[Full Stack Development Notes#3.7 WebSockets]]

**Answer:**

**WebSocket** is a **full-duplex, persistent communication protocol** that enables **real-time, bidirectional** communication between a client (browser) and server over a single long-lived TCP connection.

**HTTP vs WebSocket:**

|Feature|HTTP|WebSocket|
|---|---|---|
|**Communication**|Half-duplex (request → response)|Full-duplex (both directions simultaneously)|
|**Connection**|New connection per request|Single persistent connection|
|**Latency**|High (connect + disconnect each time)|Very low (connection already open)|
|**Real-time capable?**|❌ No (needs polling)|✅ Yes (push notifications)|
|**Data direction**|Client initiates|Either side can send anytime|
|**Protocol**|`http://` or `https://`|`ws://` or `wss://` (secure)|
|**Overhead**|High (HTTP headers each request)|Low (minimal framing overhead)|

**WebSocket Handshake:**

```
Client → Server: "I want to upgrade to WebSocket" (HTTP Upgrade request)
Server → Client: "OK, upgrading" (101 Switching Protocols)
─────── Connection is now persistent ───────
Client → Server: "Hello"   (any time)
Server → Client: "Hi back" (any time)
Server → Client: "New message!" (server-pushed)
```

**Real-time Chat Application with Node.js:**

```js
// === SERVER SIDE (server.js) ===
const http = require('http');
const WebSocket = require('ws');    // npm install ws

const server = http.createServer();
const wss = new WebSocket.Server({ server });

// Store connected clients
const clients = new Set();

wss.on('connection', (ws) => {
    clients.add(ws);
    console.log(`Client connected. Total: ${clients.size}`);

    // When message received from any client
    ws.on('message', (message) => {
        const data = JSON.parse(message);
        console.log(`Received: ${data.text}`);

        // Broadcast to ALL connected clients
        clients.forEach(client => {
            if (client.readyState === WebSocket.OPEN) {
                client.send(JSON.stringify({
                    sender: data.username,
                    text: data.text,
                    timestamp: new Date().toISOString()
                }));
            }
        });
    });

    ws.on('close', () => {
        clients.delete(ws);
        console.log(`Client disconnected. Total: ${clients.size}`);
    });
});

server.listen(8080, () => console.log('Server on port 8080'));
```

```js
// === CLIENT SIDE (browser JavaScript) ===
const ws = new WebSocket('ws://localhost:8080');

ws.onopen = () => {
    console.log('Connected to server!');
    ws.send(JSON.stringify({ username: 'Harsh', text: 'Hello everyone!' }));
};

ws.onmessage = (event) => {
    const data = JSON.parse(event.data);
    displayMessage(`${data.sender}: ${data.text}`);
};

ws.onclose = () => console.log('Disconnected from server');
ws.onerror = (error) => console.error('Error:', error);

function sendMessage(text) {
    ws.send(JSON.stringify({ username: 'Harsh', text }));
}
```

**Real-world use cases of WebSockets:**

|Application|How WebSockets help|
|---|---|
|**Chat apps** (WhatsApp Web)|Instant message delivery|
|**Live stock prices**|Real-time price updates pushed from server|
|**Multiplayer games**|Low-latency player position sync|
|**Collaborative editing** (Google Docs)|Changes sync instantly across users|
|**Live sports scores**|Score updates pushed without page refresh|
|**Notifications**|Server pushes alerts to browser|

---

## Q6) Attempt the following — [12 marks]

---

### Q6 a) i) Virtual DOM concept and how it enhances performance _(4 marks)_

→ See: [[Full Stack Development Notes#4.8 Virtual DOM]]

**Answer:**

The **Virtual DOM (VDOM)** is a **lightweight, in-memory JavaScript representation** of the actual browser DOM. React maintains this virtual tree and uses it to compute the **minimum number of operations** needed to update the real DOM.

**Why the Real DOM is slow:**

- Every real DOM manipulation triggers **reflow** (recalculate layout) and **repaint** (redraw on screen)
- These are expensive browser operations
- Updating many DOM nodes (like a list of 1000 items) is very slow

**Virtual DOM Process (Reconciliation):**

```
State Change (e.g., user clicks, data arrives)
         │
         ▼
Step 1: React creates new Virtual DOM tree
         │
         ▼
Step 2: DIFFING — React compares new VDOM with previous VDOM
         (finds exactly what changed — e.g., only one list item's text)
         │
         ▼
Step 3: React calculates minimal set of changes
         (batch multiple changes together)
         │
         ▼
Step 4: React updates ONLY the changed parts of the REAL DOM
         │
         ▼
Browser re-renders only what changed → Fast!
```

**Concrete example:**

```jsx
// React renders a list of 1000 items
// User updates item #500's price from $10 to $15

// Without Virtual DOM: re-render all 1000 items in DOM
// With Virtual DOM:
// 1. New VDOM has item #500 with $15
// 2. Diff finds: only item #500 changed
// 3. React updates ONLY that one DOM node
// Result: 999 DOM nodes untouched → 1000x faster
```

**Key algorithm — React's "Diffing":**

```
Two Virtual DOM trees:

OLD VDOM:              NEW VDOM:
<ul>                   <ul>
  <li>Item 1</li>        <li>Item 1</li>
  <li>Item 2</li>        <li>Item 2 UPDATED</li>  ← changed
  <li>Item 3</li>        <li>Item 3</li>
</ul>                  </ul>

React finds: only <li>Item 2</li> changed
Real DOM update: only that one <li> is updated
```

**Performance benefits:**

1. **Batched updates** — multiple state changes are batched into one DOM update
2. **Minimal DOM operations** — only changed nodes are updated
3. **Cross-browser consistent** — React handles browser differences
4. **Declarative** — developers describe desired state, React optimizes how to achieve it

---

### Q6 a) ii) Type Narrowing and its importance in TypeScript _(3 marks)_

→ See: [[Full Stack Development Notes#2.6 Type Narrowing and Guards]]

**Answer:**

**Type narrowing** is the process of **refining a variable's type** within a specific code block based on runtime checks. TypeScript's type checker uses control flow analysis to narrow types automatically.

**Why it's important:**

- Work safely with union types (`string | number`)
- Avoid runtime errors when a value could be multiple types
- TypeScript gives full type-specific autocompletion inside narrowed blocks

**Type narrowing techniques:**

```ts
// 1. typeof guard — primitive types
function process(value: string | number) {
    if (typeof value === "string") {
        // TypeScript KNOWS value is string here
        console.log(value.toUpperCase());   // ✅ string method
        console.log(value.toFixed(2));      // ❌ Error: not a number
    } else {
        // TypeScript KNOWS value is number here
        console.log(value.toFixed(2));      // ✅ number method
    }
}

// 2. instanceof guard — class types
class Circle { area() { return 3.14 * this.r * this.r; } constructor(public r: number) {} }
class Square { area() { return this.s * this.s; } constructor(public s: number) {} }

function getArea(shape: Circle | Square): number {
    if (shape instanceof Circle) {
        return shape.area();   // TypeScript knows it's Circle
    }
    return shape.area();       // TypeScript knows it's Square
}

// 3. in operator — object properties
type Admin = { role: "admin"; accessLevel: number };
type User  = { role: "user"; name: string };

function greet(person: Admin | User) {
    if ("accessLevel" in person) {
        console.log("Admin with level:", person.accessLevel);
    } else {
        console.log("User:", person.name);
    }
}

// 4. Discriminated unions (most common pattern)
type Shape =
    | { kind: "circle"; radius: number }
    | { kind: "rectangle"; width: number; height: number };

function area(shape: Shape): number {
    switch (shape.kind) {
        case "circle":    return Math.PI * shape.radius ** 2;
        case "rectangle": return shape.width * shape.height;
    }
}
```

---

### Q6 b) JSX and how it simplifies form creation in React _(5 marks)_

→ See: [[Full Stack Development Notes#4.2 JSX]]

**Answer:**

**JSX (JavaScript XML)** is a **syntax extension** for JavaScript that allows writing **HTML-like markup inside JavaScript** files. It is NOT HTML — it is syntactic sugar that Babel compiles into `React.createElement()` calls.

**JSX Transformation:**

```jsx
// What you write (JSX):
const element = <h1 className="title">Hello, {name}!</h1>;

// What Babel compiles it to (pure JavaScript):
const element = React.createElement(
    'h1',
    { className: 'title' },
    'Hello, ',
    name,
    '!'
);
```

**JSX Rules:**

```jsx
// ✅ Rule 1: Single root element
return (
    <div>          {/* wrapper element */}
        <h1>Title</h1>
        <p>Text</p>
    </div>
);

// ✅ or use Fragment (no extra DOM node)
return (
    <>
        <h1>Title</h1>
        <p>Text</p>
    </>
);

// ✅ Rule 2: className not class
<div className="container">...</div>   // ✅
<div class="container">...</div>       // ❌

// ✅ Rule 3: Self-closing tags
<img src="photo.jpg" />    // ✅
<input type="text" />      // ✅
<br />                     // ✅

// ✅ Rule 4: JavaScript expressions in {}
<p>{2 + 2}</p>             // 4
<p>{isLoggedIn ? "Welcome" : "Login"}</p>
```

**How JSX simplifies form creation:**

```jsx
// WITHOUT JSX (pure JavaScript) — verbose and hard to read
function LoginForm() {
    return React.createElement('form', { onSubmit: handleSubmit },
        React.createElement('label', null, 'Username:'),
        React.createElement('input', { type: 'text', name: 'username' }),
        React.createElement('label', null, 'Password:'),
        React.createElement('input', { type: 'password', name: 'password' }),
        React.createElement('button', { type: 'submit' }, 'Login')
    );
}

// WITH JSX — readable, looks like HTML, easy to write
function LoginForm() {
    const [form, setForm] = useState({ username: '', password: '' });

    const handleChange = (e) => {
        setForm({ ...form, [e.target.name]: e.target.value });
    };

    return (
        <form onSubmit={handleSubmit}>
            <label>Username:</label>
            <input
                type="text"
                name="username"
                value={form.username}
                onChange={handleChange}
                placeholder="Enter username"
            />

            <label>Password:</label>
            <input
                type="password"
                name="password"
                value={form.password}
                onChange={handleChange}
                placeholder="Enter password"
            />

            {/* Conditional rendering */}
            {form.username.length < 3 && (
                <span style={{ color: 'red' }}>Username too short</span>
            )}

            <button type="submit" disabled={!form.username || !form.password}>
                Login
            </button>
        </form>
    );
}
```

**Benefits of JSX for forms:**

1. **Readable** — structure of form visible at a glance
2. **Dynamic values** — `{form.username}` binds state directly
3. **Conditional rendering** — `{condition && <element>}` inline
4. **Event binding** — `onChange`, `onSubmit` directly in markup
5. **Reusable** — wrap form fields in reusable components

---

## Q7) Attempt the following — [12 marks]

---

### Q7 a) i) Async/Await in JavaScript with a comparison to Promises _(4 marks)_

→ See: [[Full Stack Development Notes#1.6 Promises and Async/Await]]

**Answer:**

**Async/Await** is syntactic sugar built on top of **Promises**, introduced in ES2017. It allows writing asynchronous code that **looks and reads like synchronous code**, making it easier to understand and maintain.

**Evolution of async JavaScript:**

```
Callbacks (ES5) → Promises (ES6) → Async/Await (ES2017)
```

**The same operation in all three styles:**

```js
// 1. CALLBACKS (old — "callback hell")
function getUserData(userId, callback) {
    fetchUser(userId, (err, user) => {
        if (err) { callback(err); return; }
        fetchPosts(user.id, (err, posts) => {
            if (err) { callback(err); return; }
            fetchComments(posts[0].id, (err, comments) => {
                if (err) { callback(err); return; }
                callback(null, { user, posts, comments });
                // deeply nested — hard to read!
            });
        });
    });
}

// 2. PROMISES (better — but chaining can get long)
function getUserData(userId) {
    return fetchUser(userId)
        .then(user => {
            return fetchPosts(user.id)
                .then(posts => ({ user, posts }));
        })
        .then(({ user, posts }) => {
            return fetchComments(posts[0].id)
                .then(comments => ({ user, posts, comments }));
        })
        .catch(err => console.error(err));
}

// 3. ASYNC/AWAIT (best — reads like synchronous code)
async function getUserData(userId) {
    try {
        const user     = await fetchUser(userId);
        const posts    = await fetchPosts(user.id);
        const comments = await fetchComments(posts[0].id);
        return { user, posts, comments };
    } catch (err) {
        console.error(err);
    }
}
```

**Detailed Comparison:**

|Feature|Promises|Async/Await|
|---|---|---|
|**Syntax**|`.then().catch()` chains|`await` keyword, try/catch|
|**Readability**|Moderate (chains)|✅ Excellent (linear)|
|**Error handling**|`.catch()` at end|`try/catch` blocks|
|**Debugging**|Harder (async stack traces)|✅ Easier (stack traces work normally)|
|**Multiple async**|`Promise.all()` needed|`await Promise.all()`|
|**Conditional logic**|Awkward in chains|✅ Natural if/else|
|**Underlying mechanism**|Promises themselves|Wraps Promises — same under the hood|

**Parallel execution with Async/Await:**

```js
// Sequential (slow — each waits for previous)
const user  = await fetchUser(1);    // wait 100ms
const posts = await fetchPosts(1);   // wait 200ms
// Total: 300ms

// Parallel (fast — both start at same time)
const [user, posts] = await Promise.all([
    fetchUser(1),     // starts immediately
    fetchPosts(1)     // also starts immediately
]);
// Total: ~200ms (longest of the two)
```

---

### Q7 a) ii) Describe Currying and provide an example _(3 marks)_

→ See: [[Full Stack Development Notes#Unit 1 – JavaScript ES6+]]

**Answer:**

**Currying** is a functional programming technique that **transforms a function with multiple arguments** into a sequence of functions that **each take a single argument**.

Named after mathematician **Haskell Curry**.

**Normal function → Curried function:**

```js
// Normal function — all args at once
function add(a, b, c) {
    return a + b + c;
}
add(1, 2, 3);  // 6

// Curried version — one arg at a time
function curriedAdd(a) {
    return function(b) {
        return function(c) {
            return a + b + c;
        };
    };
}

curriedAdd(1)(2)(3);  // 6

// Arrow function version (concise)
const add = a => b => c => a + b + c;
add(1)(2)(3);  // 6
```

**Practical use — Partial Application:**

```js
const multiply = a => b => a * b;

// Create specialized functions from general one
const double = multiply(2);   // partially applied
const triple = multiply(3);
const times10 = multiply(10);

console.log(double(5));   // 10
console.log(triple(5));   // 15
console.log(times10(5));  // 50

// Use with map
const numbers = [1, 2, 3, 4, 5];
console.log(numbers.map(double));   // [2, 4, 6, 8, 10]
console.log(numbers.map(triple));   // [3, 6, 9, 12, 15]
```

**Real-world use — Event handlers:**

```js
const handleEvent = (type) => (e) => {
    console.log(`${type} event on:`, e.target);
};

element.addEventListener('click', handleEvent('click'));
element.addEventListener('hover', handleEvent('hover'));
```

---

### Q7 b) Key differences between Props and State with suitable examples _(5 marks)_

→ See: [[Full Stack Development Notes#4.6 Props vs State]]

**Answer:**

**Props** and **State** are both used to manage data in React, but they serve completely different purposes and have different characteristics.

**Key Differences:**

|Feature|Props|State|
|---|---|---|
|**Definition**|Data passed from parent to child|Data managed inside the component|
|**Who controls it**|Parent component|The component itself|
|**Mutability**|❌ Read-only (immutable)|✅ Mutable (via `useState`/`setState`)|
|**Who can change it**|Only the parent can change|Only the component itself (via setState)|
|**Re-render trigger**|When parent passes new value|When `setState`/`useState` is called|
|**Scope**|External (from outside)|Internal (within component)|
|**Initial value**|Set by parent|Set inside the component|
|**Data flow**|Parent → Child (top-down)|Stays within component|
|**Purpose**|Component communication|Dynamic/interactive data|

**Comprehensive Example:**

```jsx
import { useState } from 'react';

// ──────────────────────────────────────────────
// CHILD COMPONENT — uses both props and state
// ──────────────────────────────────────────────
function ProductCard({ name, price, category }) {
    // STATE — managed inside this component
    const [quantity, setQuantity] = useState(1);   // local state
    const [addedToCart, setAddedToCart] = useState(false);

    const totalPrice = price * quantity;  // computed from prop + state

    const handleAddToCart = () => {
        setAddedToCart(true);  // changes local state
        console.log(`Added ${quantity} × ${name} to cart`);
    };

    return (
        <div className="product-card">
            {/* Props — read-only, from parent */}
            <h2>{name}</h2>
            <span className="category">{category}</span>
            <p>Price: ₹{price} per unit</p>

            {/* State — controlled by this component */}
            <div className="quantity-control">
                <button onClick={() => setQuantity(q => Math.max(1, q - 1))}>−</button>
                <span>{quantity}</span>
                <button onClick={() => setQuantity(q => q + 1)}>+</button>
            </div>

            <p><strong>Total: ₹{totalPrice}</strong></p>

            <button
                onClick={handleAddToCart}
                disabled={addedToCart}
            >
                {addedToCart ? "✅ Added to Cart" : "Add to Cart"}
            </button>
        </div>
    );
}

// ──────────────────────────────────────────────
// PARENT COMPONENT — passes props to children
// ──────────────────────────────────────────────
function ProductList() {
    // Parent's state — list of products
    const [products] = useState([
        { id: 1, name: "Laptop", price: 45000, category: "Electronics" },
        { id: 2, name: "Headphones", price: 2500, category: "Audio" },
        { id: 3, name: "Keyboard", price: 1500, category: "Accessories" }
    ]);

    return (
        <div>
            <h1>Products</h1>
            {products.map(product => (
                // Props — passed from parent to ProductCard
                <ProductCard
                    key={product.id}
                    name={product.name}       // prop
                    price={product.price}     // prop
                    category={product.category}  // prop
                />
            ))}
        </div>
    );
}
```

**What happens in above example:**

- `name`, `price`, `category` are **props** — set by parent `ProductList`, read-only in `ProductCard`
- `quantity`, `addedToCart` are **state** — managed inside `ProductCard`, trigger re-renders when changed
- Each `ProductCard` has its own independent `quantity` and `addedToCart` state — changing one doesn't affect others

**When to use which:**

|Use Props when...|Use State when...|
|---|---|
|Passing data to child component|Data changes over time in the component|
|Configuring a child's appearance/behavior|Tracking user interactions (clicks, typing)|
|Sharing read-only data|Storing API response data|
|Parent needs to control child|Form input values|

> **Golden rule:** If the data comes from outside the component → Props. If it's created and changed inside the component → State.

---

## 🏆 Most Repeated Topics (From This Actual Paper)

|Rank|Topic|Appeared in|
|---|---|---|
|🥇|Node.js architecture + Event loop|Q3a(i)|
|🥇|Props vs State|Q7b|
|🥇|Virtual DOM|Q6a(i)|
|🥇|Async/Await vs Promises|Q7a(i)|
|🥇|Controlled components|Q1h|
|🥈|TypeScript Generics|Q3a(ii)|
|🥈|TypeScript OOP vs JS prototype|Q5a(i)|
|🥈|JSX|Q6b|
|🥈|WebSockets|Q5b|
|🥈|Event handling React vs JS|Q4a(i)|
|🥈|Currying|Q7a(ii)|
|🥉|Enums in TypeScript|Q2a(ii)|
|🥉|Immutable data structures|Q4b|
|🥉|Interactive props|Q3b|

---

**See also:** [[Full Stack Development Notes]] | [[Full Stack Development QB]] | [[README]]