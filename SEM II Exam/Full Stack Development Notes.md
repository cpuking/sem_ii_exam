# 🌐 Full Stack Development Notes

**Marks:** 60 | **Priority:** 🔴 HIGH  
**Related:** [[Full Stack Development PYQ]] | [[Full Stack Development QB]] | [[README]]

---

## 📌 Table of Contents

1. [[#Unit 1 – JavaScript ES6+]]
2. [[#Unit 2 – TypeScript]]
3. [[#Unit 3 – Node.js]]
4. [[#Unit 4 – React.js]]
5. [[#Unit 5 – Forms and Validation]]
6. [[#Unit 6 – MERN Stack Overview]]
7. [[#🔥 Most Expected Questions]]

---

## Unit 1 – JavaScript ES6+

### 1.1 let and const (⭐ IMPORTANT)

ES6 introduced `let` and `const` as better alternatives to `var`.

| Feature | `var` | `let` | `const` |
|---|---|---|---|
| Scope | Function-scoped | Block-scoped | Block-scoped |
| Hoisting | Yes (undefined) | Yes (TDZ error) | Yes (TDZ error) |
| Reassignable | ✅ Yes | ✅ Yes | ❌ No |
| Re-declarable | ✅ Yes | ❌ No | ❌ No |

```js
// var – function scoped (old way, avoid)
var x = 10;
if (true) {
    var x = 20;  // same variable!
}
console.log(x);  // 20 — unexpected!

// let – block scoped
let y = 10;
if (true) {
    let y = 20;  // different variable
}
console.log(y);  // 10 — correct

// const – cannot be reassigned
const PI = 3.14;
// PI = 3.15;  ❌ TypeError
const arr = [1, 2, 3];
arr.push(4);    // ✅ OK — content can change, reference cannot
```

---

### 1.2 Arrow Functions (⭐ IMPORTANT)

**Definition:**  
Arrow functions provide a **shorter syntax** for writing functions using `=>`. They also **do not have their own `this`**.

```js
// Traditional function
function add(a, b) {
    return a + b;
}

// Arrow function – single expression (implicit return)
const add = (a, b) => a + b;

// Arrow function – multiple lines (explicit return)
const multiply = (a, b) => {
    const result = a * b;
    return result;
};

// Single parameter – parentheses optional
const square = x => x * x;

// No parameters
const greet = () => "Hello World";

// With array methods (very common)
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(n => n * 2);      // [2,4,6,8,10]
const evens   = numbers.filter(n => n % 2 === 0);  // [2,4]
```

**`this` behavior:**
```js
// Traditional function – has its own 'this'
const obj = {
    name: "Harsh",
    greet: function() {
        setTimeout(function() {
            console.log(this.name);  // undefined — 'this' is window
        }, 100);
    }
};

// Arrow function – inherits 'this' from parent scope
const obj2 = {
    name: "Harsh",
    greet: function() {
        setTimeout(() => {
            console.log(this.name);  // "Harsh" — correct!
        }, 100);
    }
};
```

---

### 1.3 Template Literals (⭐ IMPORTANT)

**Definition:**  
Template literals use **backticks** (`` ` ``) and allow embedded expressions using `${}`.

```js
const name = "Harsh";
const age = 20;

// Old way (string concatenation)
const msg1 = "Hello, my name is " + name + " and I am " + age + " years old.";

// Template literal (modern, cleaner)
const msg2 = `Hello, my name is ${name} and I am ${age} years old.`;

// Multi-line strings
const html = `
    <div>
        <h1>${name}</h1>
        <p>Age: ${age}</p>
    </div>
`;

// Expressions inside ${}
const result = `2 + 2 = ${2 + 2}`;       // "2 + 2 = 4"
const upper  = `${name.toUpperCase()}`;   // "HARSH"
```

---

### 1.4 Destructuring

```js
// Array destructuring
const [a, b, c] = [1, 2, 3];
console.log(a, b, c);  // 1 2 3

// Object destructuring
const person = { name: "Harsh", age: 20, city: "Pune" };
const { name, age } = person;
console.log(name, age);  // "Harsh" 20

// With renaming
const { name: fullName } = person;
console.log(fullName);  // "Harsh"

// Default values
const { country = "India" } = person;
console.log(country);  // "India"

// Function parameter destructuring
function greet({ name, age }) {
    return `${name} is ${age} years old`;
}
greet(person);
```

---

### 1.5 Spread and Rest Operators

```js
// Spread – expand elements
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2];  // [1,2,3,4,5,6]

const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 };  // { a:1, b:2, c:3 }

// Rest – collect remaining elements
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4, 5);  // 15

const [first, ...rest] = [1, 2, 3, 4];
// first = 1, rest = [2,3,4]
```

---

### 1.6 Promises and Async/Await (⭐ VERY IMPORTANT)

#### Promises
**Definition:**  
A Promise represents a **future value** — a computation that hasn't completed yet but will eventually succeed or fail.

```js
// Creating a promise
const myPromise = new Promise((resolve, reject) => {
    const success = true;
    if (success) {
        resolve("Data loaded successfully!");
    } else {
        reject("Error: failed to load");
    }
});

// Using a promise
myPromise
    .then(result => console.log(result))   // success
    .catch(error => console.log(error))    // failure
    .finally(() => console.log("Done"));   // always runs
```

#### Async/Await
**Definition:**  
`async/await` is **syntactic sugar** over Promises, making asynchronous code look and behave like synchronous code.

```js
// Promise style
function fetchData() {
    return fetch("https://api.example.com/data")
        .then(res => res.json())
        .then(data => console.log(data))
        .catch(err => console.error(err));
}

// Async/Await style (cleaner)
async function fetchData() {
    try {
        const response = await fetch("https://api.example.com/data");
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
```

**Comparison:**

| Feature | Callbacks | Promises | Async/Await |
|---|---|---|---|
| Readability | ❌ Callback hell | 🟡 Chain of .then() | ✅ Clean, linear |
| Error handling | ❌ Hard | 🟡 .catch() | ✅ try/catch |
| Debugging | ❌ Hard | 🟡 Moderate | ✅ Easy |
| Modern? | ❌ Old | ✅ Modern | ✅ Most modern |

---

### 1.7 Modules (import/export)

```js
// math.js – named exports
export const PI = 3.14;
export function add(a, b) { return a + b; }
export function subtract(a, b) { return a - b; }

// Default export
export default function multiply(a, b) { return a * b; }

// main.js – importing
import multiply from './math.js';           // default import
import { add, subtract, PI } from './math.js';  // named imports
import * as Math from './math.js';          // import all
```

---

## Unit 2 – TypeScript

### 2.1 What is TypeScript? (⭐ IMPORTANT)

**Definition:**  
TypeScript is a **superset of JavaScript** developed by Microsoft that adds **static typing** and other features. TypeScript code compiles down to JavaScript.

**Key features:**
- Static type checking (errors caught at compile time, not runtime)
- Supports OOP (classes, interfaces, inheritance)
- Better IDE support and autocomplete
- Improved code maintainability
- Optional typing (can be as strict or loose as needed)

```ts
// JavaScript
function add(a, b) { return a + b; }
add("hello", 2);  // no error in JS — gives "hello2" (bug!)

// TypeScript
function add(a: number, b: number): number { return a + b; }
add("hello", 2);  // ❌ Compile error — caught early!
```

---

### 2.2 Basic Types in TypeScript

```ts
// Primitive types
let name: string = "Harsh";
let age: number = 20;
let isStudent: boolean = true;

// Arrays
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob"];

// Tuple – fixed-length array with specific types
let person: [string, number] = ["Harsh", 20];

// Union type – one of several types
let id: string | number = "abc123";
id = 42;  // ✅ both valid

// Any type – disables type checking (avoid when possible)
let anything: any = "hello";
anything = 42;  // ✅

// Void – for functions that return nothing
function log(msg: string): void {
    console.log(msg);
}

// Never – function that never returns (throws error or infinite loop)
function throwError(msg: string): never {
    throw new Error(msg);
}
```

---

### 2.3 Interfaces (⭐ IMPORTANT)

```ts
// Interface definition
interface User {
    id: number;
    name: string;
    email: string;
    age?: number;  // optional property
    readonly createdAt: Date;  // cannot be changed
}

// Using interface
const user: User = {
    id: 1,
    name: "Harsh",
    email: "harsh@example.com",
    createdAt: new Date()
};

// Interface for function
interface AddFn {
    (a: number, b: number): number;
}

const add: AddFn = (a, b) => a + b;
```

---

### 2.4 Enums (⭐ IMPORTANT)

**Definition:**  
Enums define a set of **named constants**. They make code more readable.

```ts
// Numeric enum (default – starts at 0)
enum Direction {
    Up,     // 0
    Down,   // 1
    Left,   // 2
    Right   // 3
}

console.log(Direction.Up);     // 0
console.log(Direction[0]);     // "Up"

// String enum
enum Color {
    Red = "RED",
    Green = "GREEN",
    Blue = "BLUE"
}

// Usage
let c: Color = Color.Red;
console.log(c);  // "RED"

// Enum in function
function move(direction: Direction) {
    if (direction === Direction.Up) {
        console.log("Moving up!");
    }
}
```

---

### 2.5 Generics (⭐ IMPORTANT)

**Definition:**  
Generics allow writing **reusable, type-safe** functions and classes that work with any data type.

```ts
// Without generics – loses type info
function identity(value: any): any {
    return value;
}

// With generics – preserves type
function identity<T>(value: T): T {
    return value;
}

identity<string>("Hello");   // returns string
identity<number>(42);        // returns number

// Generic array function
function firstElement<T>(arr: T[]): T {
    return arr[0];
}

firstElement<number>([1, 2, 3]);   // 1 (typed as number)
firstElement<string>(["a","b"]);   // "a" (typed as string)

// Generic interface
interface Container<T> {
    value: T;
    getValue(): T;
}

// Generic class
class Stack<T> {
    private items: T[] = [];

    push(item: T): void {
        this.items.push(item);
    }

    pop(): T | undefined {
        return this.items.pop();
    }
}

const stack = new Stack<number>();
stack.push(1);
stack.push(2);
stack.pop();  // 2
```

---

### 2.6 Type Narrowing and Guards

**Definition:**  
Type narrowing is the process of **refining a variable's type** within a conditional block at runtime.

```ts
// typeof guard
function printLength(value: string | number) {
    if (typeof value === "string") {
        console.log(value.length);   // TS knows it's string here
    } else {
        console.log(value.toFixed(2));  // TS knows it's number here
    }
}

// instanceof guard
class Dog { bark() { return "Woof"; } }
class Cat { meow() { return "Meow"; } }

function speak(animal: Dog | Cat) {
    if (animal instanceof Dog) {
        animal.bark();  // safe
    } else {
        animal.meow();  // safe
    }
}
```

---

### 2.7 TypeScript OOP vs JavaScript Prototype

| Feature | TypeScript / Class-based | JavaScript / Prototype-based |
|---|---|---|
| Syntax | `class` keyword, clean | Function constructors, `prototype` |
| Typing | Strong static types | No types |
| Inheritance | `extends` keyword | Prototype chain |
| Access modifiers | `public`, `private`, `protected` | All properties public |
| Readability | ✅ Clean | ❌ Complex |

```ts
// TypeScript OOP
class Animal {
    private name: string;

    constructor(name: string) {
        this.name = name;
    }

    public speak(): string {
        return `${this.name} makes a sound`;
    }
}

class Dog extends Animal {
    speak(): string {
        return `${super.speak()} — Woof!`;
    }
}

const dog = new Dog("Rex");
console.log(dog.speak());  // "Rex makes a sound — Woof!"
```

```js
// JavaScript prototype-based (old way)
function Animal(name) {
    this.name = name;
}

Animal.prototype.speak = function() {
    return this.name + " makes a sound";
};
```

---

## Unit 3 – Node.js

### 3.1 What is Node.js? (⭐ VERY IMPORTANT)

**Definition:**  
Node.js is an **open-source, cross-platform JavaScript runtime environment** that executes JavaScript code **outside the browser**, on the server side. It is built on Chrome's **V8 JavaScript engine**.

**Key characteristics:**
- JavaScript on the server (previously only possible in browser)
- **Asynchronous** and **non-blocking I/O**
- **Event-driven** architecture
- **Single-threaded** (but handles many requests efficiently)
- Fast execution using V8 engine

**Use cases:**
- REST APIs
- Real-time applications (chat, gaming)
- Streaming services
- Microservices
- CLI tools

---

### 3.2 Node.js Architecture (⭐ VERY VERY IMPORTANT)

Node.js uses the **Event Loop** architecture:

```
                    ┌─────────────────────────────┐
                    │         Node.js Process      │
                    │                              │
  Client Requests   │   ┌──────────────────────┐   │
  ──────────────►   │   │      Event Loop       │  │
                    │   │  (single-threaded)    │  │
                    │   └──────────┬───────────┘   │
                    │              │               │
                    │    ┌─────────▼────────┐      │
                    │    │   Is I/O task?   │      │
                    │    └────┬────────┬────┘      │
                    │         │No      │Yes         │
                    │         ▼        ▼            │
                    │    Execute    Thread Pool     │
                    │    directly   (libuv)         │
                    │         │        │            │
                    │         └────────┘            │
                    │              │                │
                    │         Callback              │
                    │         Queue                 │
                    │              │                │
                    │         Send Response         │
                    └─────────────────────────────┘
```

**Flow:**
1. Client sends a request
2. Event loop receives it
3. If non-blocking → execute directly
4. If blocking (file I/O, DB query) → send to **thread pool (libuv)**
5. When done → result goes to **callback queue**
6. Event loop picks up callback and executes
7. Response sent to client

---

### 3.3 Event Loop in Detail (⭐ VERY IMPORTANT)

**Definition:**  
The event loop is the **core mechanism** in Node.js that continuously checks the callback queue and executes callbacks when the call stack is empty.

**Phases of event loop (simplified):**
1. **timers** – executes `setTimeout`, `setInterval` callbacks
2. **I/O callbacks** – network, file I/O callbacks
3. **idle/prepare** – internal use
4. **poll** – wait for new I/O events
5. **check** – `setImmediate` callbacks
6. **close callbacks** – cleanup

**Classic example:**
```js
console.log("Start");

setTimeout(() => {
    console.log("Timeout (async)");
}, 0);

Promise.resolve().then(() => {
    console.log("Promise (microtask)");
});

console.log("End");

// Output:
// Start
// End
// Promise (microtask)     ← runs before setTimeout
// Timeout (async)
```

**Why this order?**
- `console.log` runs synchronously (call stack)
- Promises go to **microtask queue** (higher priority)
- `setTimeout` goes to **macro-task queue** (lower priority)
- Event loop: call stack → microtasks → macrotasks

---

### 3.4 Asynchronous Programming in Node.js (⭐ VERY IMPORTANT)

**Definition:**  
Asynchronous programming allows Node.js to **start a task and move on** without waiting for it to finish, handling the result later via callbacks/promises.

#### Method 1: Callbacks (old way)
```js
const fs = require('fs');

fs.readFile('file.txt', 'utf8', (err, data) => {
    if (err) {
        console.error("Error:", err);
        return;
    }
    console.log("Data:", data);
});

console.log("This runs FIRST (before file is read)");
```

#### Method 2: Promises
```js
const fs = require('fs').promises;

fs.readFile('file.txt', 'utf8')
    .then(data => console.log(data))
    .catch(err => console.error(err));
```

#### Method 3: Async/Await (recommended)
```js
const fs = require('fs').promises;

async function readMyFile() {
    try {
        const data = await fs.readFile('file.txt', 'utf8');
        console.log(data);
    } catch (err) {
        console.error(err);
    }
}

readMyFile();
```

---

### 3.5 Modules in Node.js (⭐ IMPORTANT)

**Definition:**  
Modules are **reusable blocks of code** that can be imported and exported between files.

**Types:**

| Type | Description | Examples |
|---|---|---|
| **Core modules** | Built into Node.js | `fs`, `http`, `path`, `os` |
| **Local modules** | Your own files | `./myModule.js` |
| **Third-party** | Installed via npm | `express`, `mongoose` |

```js
// Core module
const fs = require('fs');
const path = require('path');
const http = require('http');

// Reading a file (sync)
const content = fs.readFileSync('file.txt', 'utf8');

// Path utilities
const fullPath = path.join(__dirname, 'files', 'data.txt');

// Create local module (math.js)
function add(a, b) { return a + b; }
function subtract(a, b) { return a - b; }

module.exports = { add, subtract };

// Use it (app.js)
const { add, subtract } = require('./math');
console.log(add(5, 3));  // 8
```

---

### 3.6 Streams in Node.js

**Definition:**  
Streams are objects for **handling large amounts of data** efficiently by processing it in chunks instead of loading all at once.

**Types:**
- **Readable** – read data (e.g., `fs.createReadStream`)
- **Writable** – write data (e.g., `fs.createWriteStream`)
- **Duplex** – both read and write (e.g., TCP socket)
- **Transform** – modify data while reading/writing (e.g., compression)

```js
const fs = require('fs');

// Without streams (loads entire file into memory)
const data = fs.readFileSync('bigfile.txt');  // ❌ memory issue

// With streams (reads chunk by chunk)
const readStream = fs.createReadStream('bigfile.txt');
const writeStream = fs.createWriteStream('output.txt');

readStream.pipe(writeStream);  // ✅ efficient, low memory

readStream.on('data', (chunk) => {
    console.log('Received chunk:', chunk.length, 'bytes');
});

readStream.on('end', () => {
    console.log('Done reading');
});
```

---

### 3.7 WebSockets (⭐ VERY IMPORTANT)

**Definition:**  
WebSockets provide a **full-duplex, persistent communication channel** between client and server over a single TCP connection.

**How it differs from HTTP:**

| Feature | HTTP | WebSocket |
|---|---|---|
| Communication | One-way (request/response) | Two-way (full-duplex) |
| Connection | New connection per request | Persistent connection |
| Real-time? | ❌ No (polling needed) | ✅ Yes |
| Use cases | Static pages, APIs | Chat, games, live data |
| Protocol | `http://` or `https://` | `ws://` or `wss://` |

**Use cases:**
- Real-time chat applications
- Live stock prices
- Multiplayer games
- Collaborative editing (Google Docs)
- Live notifications

```js
// Server side (using 'ws' library)
const WebSocket = require('ws');
const wss = new WebSocket.Server({ port: 8080 });

wss.on('connection', (ws) => {
    console.log('Client connected');

    ws.on('message', (message) => {
        console.log('Received:', message);
        ws.send(`Echo: ${message}`);  // send back to client
    });

    ws.on('close', () => {
        console.log('Client disconnected');
    });
});

// Client side
const ws = new WebSocket('ws://localhost:8080');

ws.onopen = () => ws.send('Hello Server!');
ws.onmessage = (event) => console.log(event.data);
```

---

## Unit 4 – React.js

### 4.1 What is React? (⭐ IMPORTANT)

**Definition:**  
React is an **open-source JavaScript library** developed by Facebook for building **user interfaces**. It allows building complex UIs from small, isolated, reusable pieces called **components**.

**Key features:**
- Component-based architecture
- Virtual DOM for efficient rendering
- Unidirectional data flow
- JSX syntax
- Large ecosystem

---

### 4.2 JSX (⭐ VERY IMPORTANT)

**Definition:**  
JSX (JavaScript XML) is a **syntax extension** for JavaScript that allows writing HTML-like code inside JavaScript files. JSX is converted to regular JavaScript by **Babel**.

**Rules of JSX:**
1. Must return a **single parent element**
2. Use `className` instead of `class`
3. Use `{}` for JavaScript expressions
4. Self-closing tags must end with `/>`
5. All tags must be closed

```jsx
// Basic JSX
const element = <h1>Hello, World!</h1>;

// With expression
const name = "Harsh";
const greeting = <h1>Hello, {name}!</h1>;

// Multi-line JSX (needs a wrapper)
const card = (
    <div className="card">
        <h2>{name}</h2>
        <p>Age: {20}</p>
        <p>Result: {2 + 2}</p>
    </div>
);

// Using fragment (no extra div)
const fragment = (
    <>
        <h1>Title</h1>
        <p>Paragraph</p>
    </>
);
```

---

### 4.3 Components (⭐ VERY IMPORTANT)

**Definition:**  
Components are **independent, reusable pieces of UI**. They accept inputs (props) and return React elements (JSX).

**Types:**

#### 1. Functional Component (modern, preferred)
```jsx
function Welcome(props) {
    return <h1>Hello, {props.name}!</h1>;
}

// Arrow function style
const Welcome = ({ name }) => <h1>Hello, {name}!</h1>;

// Usage
<Welcome name="Harsh" />
```

#### 2. Class Component (older style)
```jsx
import React, { Component } from 'react';

class Welcome extends Component {
    render() {
        return <h1>Hello, {this.props.name}!</h1>;
    }
}
```

---

### 4.4 Props (⭐ VERY IMPORTANT)

**Definition:**  
Props (properties) are **read-only inputs** passed from a **parent component to a child component**.

```jsx
// Parent component
function App() {
    return (
        <div>
            <UserCard name="Harsh" age={20} city="Pune" />
            <UserCard name="Rahul" age={21} city="Mumbai" />
        </div>
    );
}

// Child component receives props
function UserCard({ name, age, city }) {
    return (
        <div className="card">
            <h2>{name}</h2>
            <p>Age: {age}</p>
            <p>City: {city}</p>
        </div>
    );
}
```

**Key points about props:**
- Props flow **one direction: parent → child**
- Props are **read-only** (cannot be modified by child)
- Used for component **communication**

---

### 4.5 State (⭐ VERY IMPORTANT)

**Definition:**  
State is **mutable data** managed **inside a component**. When state changes, React re-renders the component.

```jsx
import { useState } from 'react';

function Counter() {
    // useState returns [currentValue, setterFunction]
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
            <button onClick={() => setCount(count - 1)}>Decrement</button>
            <button onClick={() => setCount(0)}>Reset</button>
        </div>
    );
}
```

---

### 4.6 Props vs State (⭐ GUARANTEED QUESTION)

| Feature | Props | State |
|---|---|---|
| Source | Passed from parent | Defined inside component |
| Mutability | Read-only (immutable) | Mutable (via `setState`/`useState`) |
| Control | Controlled by parent | Controlled by component itself |
| Purpose | Pass data between components | Manage dynamic/changing data |
| Re-render trigger | When parent changes | When state is updated |
| Access | `props.name` or `{ name }` | `count`, `setCount` |

```jsx
// Props example – data flows down
<UserCard name="Harsh" />  // parent passes name

// State example – component manages its own data
const [name, setName] = useState("Harsh");
```

---

### 4.7 React Lifecycle (⭐ VERY IMPORTANT)

**Phases:**
1. **Mounting** – component is created and inserted into DOM
2. **Updating** – component re-renders due to props/state change
3. **Unmounting** – component is removed from DOM

**Class component lifecycle methods:**

| Phase | Method | When called |
|---|---|---|
| Mounting | `constructor()` | Before component mounts |
| Mounting | `render()` | Required – renders JSX |
| Mounting | `componentDidMount()` | After component mounts (good for API calls) |
| Updating | `componentDidUpdate(prevProps, prevState)` | After update |
| Unmounting | `componentWillUnmount()` | Before component removed (good for cleanup) |

**Functional equivalent using `useEffect`:**
```jsx
import { useState, useEffect } from 'react';

function DataFetcher() {
    const [data, setData] = useState(null);

    // componentDidMount equivalent
    useEffect(() => {
        fetch('/api/data')
            .then(res => res.json())
            .then(data => setData(data));

        // componentWillUnmount equivalent (cleanup)
        return () => {
            console.log('Component unmounted — cleanup here');
        };
    }, []);  // [] = run once on mount

    // componentDidUpdate equivalent
    useEffect(() => {
        console.log('data changed:', data);
    }, [data]);  // runs when 'data' changes

    return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
}
```

---

### 4.8 Virtual DOM (⭐ MOST EXPECTED)

**Definition:**  
Virtual DOM is a **lightweight in-memory copy** of the real DOM. React uses it to determine what has changed and make **minimal updates** to the actual DOM.

**How it works:**
```
User action (state change)
        ↓
React updates Virtual DOM (in memory — fast)
        ↓
React compares new Virtual DOM with previous
(this is called "diffing")
        ↓
React calculates minimal set of changes
        ↓
React updates ONLY the changed parts of real DOM
(this is called "reconciliation")
        ↓
UI updates efficiently
```

**Why it matters:**
- Real DOM manipulation is **slow**
- Virtual DOM updates are **fast** (just JavaScript objects in memory)
- React batches updates to minimize real DOM operations
- Result: React apps are **fast and efficient**

---

### 4.9 Event Handling in React (⭐ IMPORTANT)

| Feature | React | Traditional JavaScript |
|---|---|---|
| Syntax | camelCase (`onClick`) | lowercase (`onclick`) |
| Event type | Synthetic events (cross-browser) | Native DOM events |
| Handler | JSX `{handleClick}` | `addEventListener` |
| Prevent default | `e.preventDefault()` | `return false` (old) |

```jsx
// React event handling
function Button() {
    const handleClick = (e) => {
        e.preventDefault();
        console.log("Clicked!", e.target);
    };

    return (
        <button onClick={handleClick}>Click Me</button>
    );
}

// Passing arguments
function ItemList() {
    const handleDelete = (id) => {
        console.log("Delete item:", id);
    };

    return (
        <ul>
            <li>Item 1 <button onClick={() => handleDelete(1)}>Delete</button></li>
            <li>Item 2 <button onClick={() => handleDelete(2)}>Delete</button></li>
        </ul>
    );
}
```

---

### 4.10 Controlled vs Uncontrolled Components (⭐ IMPORTANT)

#### Controlled Component
**Definition:** Form element value is controlled by **React state**.

```jsx
function ControlledForm() {
    const [name, setName] = useState('');

    const handleSubmit = (e) => {
        e.preventDefault();
        console.log("Submitted:", name);
    };

    return (
        <form onSubmit={handleSubmit}>
            <input
                type="text"
                value={name}                     // controlled by state
                onChange={(e) => setName(e.target.value)}
            />
            <button type="submit">Submit</button>
        </form>
    );
}
```

#### Uncontrolled Component
**Definition:** Form element value is managed by the **DOM** directly, accessed via `ref`.

```jsx
import { useRef } from 'react';

function UncontrolledForm() {
    const nameRef = useRef();

    const handleSubmit = (e) => {
        e.preventDefault();
        console.log("Value:", nameRef.current.value);  // access DOM directly
    };

    return (
        <form onSubmit={handleSubmit}>
            <input type="text" ref={nameRef} />
            <button type="submit">Submit</button>
        </form>
    );
}
```

**Comparison:**

| Feature | Controlled | Uncontrolled |
|---|---|---|
| Data location | React state | DOM |
| Access value | `state` variable | `ref.current.value` |
| Validation | ✅ Easy (check state) | ❌ Harder |
| React control | ✅ Full control | ❌ Limited |
| Preferred? | ✅ Yes (most cases) | Only for simple cases |

---

## Unit 5 – Forms and Validation

### 5.1 Form Handling in React

```jsx
function RegistrationForm() {
    const [form, setForm] = useState({
        name: '',
        email: '',
        password: ''
    });
    const [errors, setErrors] = useState({});

    const handleChange = (e) => {
        setForm({ ...form, [e.target.name]: e.target.value });
    };

    const validate = () => {
        const newErrors = {};
        if (!form.name) newErrors.name = "Name is required";
        if (!form.email.includes('@')) newErrors.email = "Invalid email";
        if (form.password.length < 6) newErrors.password = "Min 6 characters";
        return newErrors;
    };

    const handleSubmit = (e) => {
        e.preventDefault();
        const newErrors = validate();
        if (Object.keys(newErrors).length > 0) {
            setErrors(newErrors);
        } else {
            console.log("Form submitted:", form);
        }
    };

    return (
        <form onSubmit={handleSubmit}>
            <input name="name" value={form.name} onChange={handleChange} />
            {errors.name && <span className="error">{errors.name}</span>}

            <input name="email" value={form.email} onChange={handleChange} />
            {errors.email && <span className="error">{errors.email}</span>}

            <input type="password" name="password" value={form.password} onChange={handleChange} />
            {errors.password && <span className="error">{errors.password}</span>}

            <button type="submit">Register</button>
        </form>
    );
}
```

---

## Unit 6 – MERN Stack Overview

### 6.1 What is MERN Stack? (⭐ IMPORTANT)

**Definition:**  
MERN Stack is a **JavaScript-based full-stack development framework** using four technologies:

| Letter | Technology | Role |
|---|---|---|
| **M** | MongoDB | NoSQL Database |
| **E** | Express.js | Backend web framework (runs on Node.js) |
| **R** | React.js | Frontend UI library |
| **N** | Node.js | JavaScript runtime for server |

**Advantages:**
- **Full JavaScript** – same language across all layers
- JSON data flows seamlessly between all layers
- Large community and ecosystem
- Scalable and fast

**Architecture:**
```
[Browser] ←→ [React (Frontend)]
                    ↕ HTTP/REST API
[Node.js + Express (Backend)]
                    ↕ Mongoose/MongoDB Driver
              [MongoDB (Database)]
```

---

## 🔥 Most Expected Questions

| Question | Marks | Frequency |
|---|---|---|
| Node.js architecture + Event loop | 5–7 | ⭐⭐⭐ |
| Props vs State | 4–5 | ⭐⭐⭐ |
| Virtual DOM | 3–5 | ⭐⭐⭐ |
| Async/Await vs Promises | 3–5 | ⭐⭐⭐ |
| Controlled vs Uncontrolled | 4–5 | ⭐⭐ |
| React Lifecycle | 5–7 | ⭐⭐⭐ |
| TypeScript + Generics | 3–5 | ⭐⭐ |
| JSX explanation | 2–3 | ⭐⭐ |
| WebSockets | 3–5 | ⭐⭐ |
| MERN Stack | 3–5 | ⭐⭐ |
| let/const/arrow functions | 2 | ⭐⭐ |
| Enums in TypeScript | 2–3 | ⭐⭐ |

---

## 📝 Quick Revision Summary

```
JavaScript ES6+:
  let/const (block scoped) | arrow functions (no own 'this')
  template literals | destructuring | spread/rest
  Promises → async/await

TypeScript:
  Superset of JS with static types
  Interfaces, Enums, Generics, Type Guards
  Compiles to JavaScript

Node.js:
  JS runtime on server (V8 engine)
  Single-threaded + Event Loop + Non-blocking I/O
  Async: callbacks → Promises → async/await

React:
  Components (functional > class)
  Props = passed down (read-only)
  State = managed inside (mutable, triggers re-render)
  Virtual DOM = lightweight copy, diffing, reconciliation
  Lifecycle: Mount → Update → Unmount
  JSX = HTML in JS, compiled by Babel
```

---

**See also:** [[Full Stack Development PYQ]] | [[Full Stack Development QB]] | [[README]]
