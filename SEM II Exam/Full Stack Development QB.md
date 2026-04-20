---

# 🔥 FULL STACK – DETAILED ANSWERS

---
> 📌 **Exam Strategy:** Node.js architecture + React lifecycle + TypeScript = **core scoring topics** Tags: #fullstack #react #nodejs #typescript #exam #questionbank

---

# 📋 TABLE OF CONTENTS

- [[#JSX – VERY IMPORTANT]]
- [[#Node.js – Architecture + Features]]
- [[#Event Loop – VERY IMPORTANT]]
- [[#Asynchronous Programming]]
- [[#React Components]]
- [[#Props vs State]]
- [[#React Lifecycle]]
- [[#Controlled vs Uncontrolled Components]]
- [[#Modules in Node.js]]
- [[#Streams in Node.js]]
- [[#TypeScript – Advanced]]
- [[#Virtual DOM]]
- [[#Form Validation]]
- [[#MERN Stack]]
- [[#Final Strategy]]

---

# ✅ 1. JSX `VERY IMPORTANT`

## Definition

**JSX (JavaScript XML)** is a syntax extension for JavaScript used in React that allows writing HTML-like markup inside JavaScript files.

> It is NOT HTML — it is syntactic sugar that gets compiled to `React.createElement()` calls.

## How JSX Works Internally

```jsx
// What you write (JSX):
const element = <h1 className="title">Hello, Harsh</h1>;

// What Babel compiles it to:
const element = React.createElement(
  'h1',
  { className: 'title' },
  'Hello, Harsh'
);
```

## JSX Rules (Write all in exam)

|Rule|Example|Wrong|Right|
|---|---|---|---|
|Single root element|Wrap in `<div>` or `<>`|`<h1/><p/>`|`<><h1/><p/></>`|
|Self-closing tags|Must close all tags|`<img>`|`<img />`|
|`className` not `class`|HTML attribute differs|`class="btn"`|`className="btn"`|
|`htmlFor` not `for`|Label attribute|`for="id"`|`htmlFor="id"`|
|JS expressions in `{}`|Embed variables|`<h1>name</h1>`|`<h1>{name}</h1>`|
|camelCase events|Event names|`onclick`|`onClick`|
|No `if` inside JSX directly|Use ternary|—|`{x ? A : B}`|

## JSX Examples

```jsx
// Basic JSX
const greeting = <h1>Hello, {name}</h1>;

// JSX with expression
const total = <p>Total: {2 + 3}</p>;

// Conditional rendering
const button = (
  <button className={isActive ? "btn-active" : "btn-inactive"}>
    {isLoggedIn ? "Logout" : "Login"}
  </button>
);

// List rendering
const list = (
  <ul>
    {items.map((item, index) => (
      <li key={index}>{item}</li>
    ))}
  </ul>
);

// Component in JSX
function Welcome({ name }) {
  return <h1>Welcome, {name}!</h1>;
}

const app = <Welcome name="Harsh" />;
```

## Why JSX?

|Benefit|Explanation|
|---|---|
|Readable|Looks like HTML, easy to visualize UI|
|Powerful|Full JS expressions inside markup|
|Safe|Escapes values to prevent XSS attacks|
|Performance|Compiled to optimized JS by Babel|

> 📝 **5-mark answer:** Definition + how it compiles + rules table + 2 code examples.

---

# ✅ 2. Node.js – Definition + Features + Architecture `VERY IMPORTANT`

## Definition

**Node.js** is an open-source, cross-platform **JavaScript runtime environment** built on Chrome's **V8 JavaScript engine** that allows execution of JavaScript code on the server side.

> Before Node.js, JavaScript only ran in browsers. Node.js brought JS to the server.

## Features

|Feature|Explanation|
|---|---|
|**Asynchronous**|Operations don't block — results via callbacks/promises|
|**Non-blocking I/O**|I/O operations run independently, no waiting|
|**Event-driven**|Code runs in response to events|
|**Single-threaded**|One thread handles all requests via event loop|
|**V8 Engine**|Google's high-performance JS engine (compiles to machine code)|
|**NPM**|World's largest package ecosystem|
|**Cross-platform**|Runs on Windows, macOS, Linux|
|**Scalable**|Handles thousands of concurrent connections|

## Architecture – VERY VERY IMPORTANT

```
┌─────────────────────────────────────────────────────────┐
│                    CLIENT REQUESTS                       │
│            (Req 1)  (Req 2)  (Req 3)  (Req N)           │
└─────────────────────────┬───────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────┐
│                   EVENT QUEUE                            │
│         [Req1] [Req2] [Req3] ... [ReqN]                  │
└─────────────────────────┬───────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────┐
│                   EVENT LOOP                             │
│  (Single thread – picks requests from queue)             │
│                                                          │
│   Is it blocking?                                        │
│   ┌──── NO ────┐          ┌──── YES ────┐               │
│   ▼            │          ▼             │               │
│ Process      Return     Thread Pool     │               │
│ directly     result    (libuv C++ lib)  │               │
│                          │              │               │
│                          ▼              │               │
│                    Worker Threads       │               │
│                    (file I/O, DB, etc)  │               │
│                          │              │               │
│                          ▼              │               │
│                       Callback ─────────┘               │
└─────────────────────────────────────────────────────────┘
```

**Step-by-Step Flow:**

1. Client sends HTTP request
2. Request enters the **Event Queue**
3. **Event Loop** picks up the request
4. If **non-blocking** (e.g., math, string ops) → process directly → return response
5. If **blocking** (e.g., file read, DB query) → send to **Thread Pool** (libuv)
6. Thread pool handles it in background
7. When done, **callback** is placed back in queue
8. Event loop executes the callback → sends response

## Advantages vs Limitations

|Advantages|Limitations|
|---|---|
|High performance for I/O tasks|Not suitable for CPU-heavy tasks|
|Handles thousands of concurrent connections|Single-threaded (CPU bottleneck)|
|Same language frontend & backend|Callback hell (solved by async/await)|
|Large NPM ecosystem|Less mature than Java/Python for enterprise|
|Microservices friendly|Memory-heavy for large applications|

## Code Example

```js
const http = require('http');
const fs = require('fs');

const server = http.createServer((req, res) => {
  if (req.url === '/') {
    // Non-blocking file read
    fs.readFile('index.html', (err, data) => {
      if (err) {
        res.writeHead(500);
        res.end('Server Error');
        return;
      }
      res.writeHead(200, { 'Content-Type': 'text/html' });
      res.end(data);
    });
  }
});

server.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

> 📝 **7-mark answer:** Definition + features table + architecture diagram + advantages/limitations + code example.

---

# ✅ 3. Event Loop `VERY IMPORTANT`

## Definition

The **Event Loop** is the core mechanism in Node.js that continuously monitors the call stack and the callback queue, executing callbacks when the call stack is empty. It is what makes Node.js's non-blocking I/O possible.

## Event Loop Phases (in order)

```
┌───────────────────────────────────────────────────────┐
│                     Event Loop                         │
│                                                        │
│  ┌──────────┐ → ┌──────────┐ → ┌──────────────────┐  │
│  │  timers  │   │  pending │   │  idle, prepare   │  │
│  │ (setTimeout│  │ callbacks│   │  (internal)      │  │
│  │ setInterval│  └──────────┘   └──────────────────┘  │
│  └──────────┘                                         │
│        ↓                                              │
│  ┌──────────┐ → ┌──────────┐ → ┌──────────────────┐  │
│  │  poll    │   │  check   │   │  close callbacks │  │
│  │ (I/O)   │   │(setImmediate)  │  (socket.close) │  │
│  └──────────┘   └──────────┘   └──────────────────┘  │
└───────────────────────────────────────────────────────┘
```

**Priority Order (microtasks run between each phase):**

1. `process.nextTick()` – highest priority
2. `Promise.then()` / `queueMicrotask()` – microtasks
3. `setTimeout` / `setInterval` – timers phase
4. I/O callbacks – poll phase
5. `setImmediate` – check phase

## Classic Example

```js
console.log("1 - Start");                          // Synchronous

setTimeout(() => console.log("2 - setTimeout"), 0); // Timer (async)

Promise.resolve().then(() => console.log("3 - Promise")); // Microtask

process.nextTick(() => console.log("4 - nextTick")); // nextTick (highest priority)

console.log("5 - End");                            // Synchronous
```

**Output:**

```
1 - Start
5 - End
4 - nextTick        ← process.nextTick runs first (before promises)
3 - Promise         ← Microtask queue
2 - setTimeout      ← Timer phase (runs last)
```

## Why This Matters

|Concept|Implication|
|---|---|
|Non-blocking|I/O doesn't freeze the server|
|Single thread|Only one thing runs at a time on main thread|
|Callbacks|Async results are handled via callbacks|
|Promises/Async-Await|Cleaner way to handle async operations|

> 📝 **5-mark answer:** Definition + 5 phases + code example with output explanation.

---

# ✅ 4. Asynchronous Programming in Node.js `IMPORTANT`

## Definition

**Asynchronous programming** allows code to initiate a task and continue executing other code without waiting for that task to complete. The result is handled later via callbacks, promises, or async/await.

## Three Patterns (Evolution)

### Pattern 1: Callbacks (Old style)

```js
const fs = require('fs');

fs.readFile('data.txt', 'utf8', (err, data) => {
  if (err) {
    console.error('Error:', err);
    return;
  }
  console.log('File contents:', data);
});

console.log('This runs BEFORE file is read');
```

**Problem – Callback Hell:**

```js
// Hard to read and maintain
doA((a) => {
  doB(a, (b) => {
    doC(b, (c) => {
      doD(c, (d) => {
        console.log(d); // deeply nested
      });
    });
  });
});
```

### Pattern 2: Promises (ES6)

```js
function fetchUser(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (id > 0) {
        resolve({ id, name: 'Harsh' });
      } else {
        reject(new Error('Invalid ID'));
      }
    }, 1000);
  });
}

// Usage
fetchUser(1)
  .then(user => console.log(user))
  .catch(err => console.error(err))
  .finally(() => console.log('Done'));
```

### Pattern 3: Async/Await (ES2017 – PREFERRED)

```js
async function getUser(id) {
  try {
    const user = await fetchUser(id);
    const posts = await fetchPosts(user.id);
    const comments = await fetchComments(posts[0].id);
    return comments;
  } catch (error) {
    console.error('Error:', error.message);
  }
}

// Call async function
getUser(1).then(data => console.log(data));
```

## Comparison Table

|Feature|Callback|Promise|Async/Await|
|---|---|---|---|
|Syntax|Nested functions|`.then().catch()`|Looks synchronous|
|Error handling|Manual checks|`.catch()`|`try/catch`|
|Readability|Poor (nesting)|Medium|Excellent|
|Debugging|Difficult|Moderate|Easy|
|Version|Legacy|ES6|ES2017|

> 📝 **5-mark answer:** Definition + all 3 patterns with code + comparison table.

---

# ✅ 5. React Components `VERY IMPORTANT`

## Definition

**Components** are the building blocks of React applications — independent, reusable pieces of UI that manage their own rendering and logic.

## Types of Components

### 1. Functional Components (Modern – Preferred)

```jsx
// Simple functional component
function Greeting({ name }) {
  return (
    <div className="greeting">
      <h1>Hello, {name}!</h1>
      <p>Welcome to React</p>
    </div>
  );
}

// With hooks
import { useState, useEffect } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
}
```

### 2. Class Components (Legacy)

```jsx
import React from 'react';

class Greeting extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment() {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <h1>Hello, {this.props.name}!</h1>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.increment()}>Add</button>
      </div>
    );
  }
}
```

## Functional vs Class Components

|Feature|Functional|Class|
|---|---|---|
|Syntax|Function|ES6 Class|
|State|`useState` hook|`this.state`|
|Lifecycle|`useEffect`|Lifecycle methods|
|`this` keyword|Not needed|Required|
|Performance|Better (no overhead)|Slightly heavier|
|Modern usage|✅ Preferred|⚠️ Legacy|
|Boilerplate|Minimal|More verbose|

## Component Composition

```jsx
// Atomic components
function Avatar({ src, alt }) {
  return <img src={src} alt={alt} className="avatar" />;
}

function UserName({ name }) {
  return <span className="username">{name}</span>;
}

// Composed component
function UserCard({ user }) {
  return (
    <div className="card">
      <Avatar src={user.avatar} alt={user.name} />
      <UserName name={user.name} />
      <p>{user.bio}</p>
    </div>
  );
}
```

> 📝 **5-mark answer:** Definition + types + code for both + comparison table.

---

# ✅ 6. Props vs State `VERY IMPORTANT`

## Definitions

- **Props:** External data passed into a component from its parent. Read-only.
- **State:** Internal data managed by the component itself. Mutable.

## Comparison Table

|Feature|Props|State|
|---|---|---|
|Source|Passed from parent|Managed internally|
|Mutability|Read-only (immutable)|Mutable (`setState`/`useState`)|
|Who controls|Parent component|Component itself|
|Purpose|Communicate between components|Manage dynamic UI data|
|Re-render|Re-renders when prop changes|Re-renders when state changes|
|Initial value|Set by parent|Set in constructor/useState|
|Access (class)|`this.props.name`|`this.state.name`|
|Update (class)|Cannot update directly|`this.setState({})`|
|Access (function)|`props.name` or destructured|`const [val, setVal] = useState()`|

## Code Examples

```jsx
// Props – passed from parent to child
function Parent() {
  return (
    <div>
      <Child name="Harsh" age={21} isActive={true} />
    </div>
  );
}

function Child({ name, age, isActive }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>Status: {isActive ? "Active" : "Inactive"}</p>
    </div>
  );
}

// State – managed within component
function LoginForm() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  const handleSubmit = () => {
    if (email && password) {
      setIsLoggedIn(true);
    }
  };

  return (
    <div>
      {isLoggedIn ? (
        <p>Welcome back!</p>
      ) : (
        <>
          <input value={email} onChange={e => setEmail(e.target.value)} placeholder="Email" />
          <input type="password" value={password} onChange={e => setPassword(e.target.value)} />
          <button onClick={handleSubmit}>Login</button>
        </>
      )}
    </div>
  );
}
```

## When to use Props vs State?

|Situation|Use Props|Use State|
|---|---|---|
|Display user profile data|✅||
|Toggle modal open/close||✅|
|Pass data between components|✅||
|Track form input values||✅|
|API response data||✅|
|Theme (propagated down)|✅||

> 📝 **5-mark answer:** Definitions + comparison table + code example for both.

---

# ✅ 7. React Lifecycle `VERY IMPORTANT`

## Overview

React components go through 3 lifecycle phases. Understanding these helps manage side effects, API calls, and cleanup.

## Phases Diagram

```
COMPONENT LIFECYCLE
════════════════════════════════════════════════════════════

  MOUNTING              UPDATING              UNMOUNTING
  (First render)        (Re-render)           (Removal)
  ──────────────        ──────────────        ──────────────

  constructor()         getDerivedState       componentWill-
       ↓                FromProps()           Unmount()
  getDerivedState            ↓                     ↓
  FromProps()           shouldComponent       Cleanup:
       ↓                Update()              - Clear timers
  render()                   ↓                - Cancel reqs
       ↓                render()              - Detach events
  componentDid               ↓
  Mount()               getSnapshot
  ★ Best for:           BeforeUpdate()
  - API calls                ↓
  - Subscriptions       componentDid
  - DOM setup           Update()
```

## Lifecycle Methods (Class Components)

|Method|Phase|When Called|Common Use|
|---|---|---|---|
|`constructor()`|Mounting|Before render|Initialize state, bind methods|
|`componentDidMount()`|Mounting|After first render|API calls, subscriptions|
|`shouldComponentUpdate()`|Updating|Before re-render|Performance optimization|
|`componentDidUpdate()`|Updating|After re-render|Side effects on prop/state change|
|`componentWillUnmount()`|Unmounting|Before removal|Cleanup (timers, listeners)|

## Hooks Equivalent (Functional Components)

|Class Lifecycle|Hooks Equivalent|
|---|---|
|`constructor`|`useState` initialization|
|`componentDidMount`|`useEffect(() => {...}, [])`|
|`componentDidUpdate`|`useEffect(() => {...}, [dep])`|
|`componentWillUnmount`|`useEffect(() => { return cleanup }, [])`|

## Code Example

```jsx
// Class component lifecycle
class DataFetcher extends React.Component {
  constructor(props) {
    super(props);
    this.state = { data: null, loading: true };
  }

  componentDidMount() {
    // Called after first render – perfect for API calls
    fetch('https://api.example.com/data')
      .then(res => res.json())
      .then(data => this.setState({ data, loading: false }));
  }

  componentDidUpdate(prevProps) {
    // Called when props/state change
    if (prevProps.id !== this.props.id) {
      this.fetchData(this.props.id);
    }
  }

  componentWillUnmount() {
    // Cleanup before component is removed
    this.subscription?.unsubscribe();
    clearInterval(this.timer);
  }

  render() {
    return this.state.loading ? <p>Loading...</p> : <p>{this.state.data}</p>;
  }
}

// Hooks equivalent
function DataFetcher({ id }) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    setLoading(true);
    fetch(`https://api.example.com/data/${id}`)
      .then(res => res.json())
      .then(data => {
        setData(data);
        setLoading(false);
      });

    return () => {
      // Cleanup (equivalent to componentWillUnmount)
      setData(null);
    };
  }, [id]); // Re-run when id changes

  return loading ? <p>Loading...</p> : <p>{data}</p>;
}
```

> 📝 **7-mark answer:** Phases diagram + methods table + hooks equivalent table + code example. ⭐ Drawing the diagram in exam = bonus marks!

---

# ✅ 8. Controlled vs Uncontrolled Components `IMPORTANT`

## Definitions

- **Controlled:** Form element value is controlled by React state. React is the single source of truth.
- **Uncontrolled:** Form element value is managed by the DOM itself, accessed via `ref`.

## Comparison

|Feature|Controlled|Uncontrolled|
|---|---|---|
|Data managed by|React state|DOM|
|Access value|`state.value`|`ref.current.value`|
|Validation|Easy (real-time)|On submit only|
|Re-render on change|Yes|No|
|Code complexity|More verbose|Simpler|
|Dynamic fields|Easy|Harder|
|Recommended for|Most forms|File inputs, simple forms|

## Code Examples

```jsx
// CONTROLLED COMPONENT
function ControlledForm() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log({ name, email }); // Data always current in state
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={name}                           // Value from state
        onChange={(e) => setName(e.target.value)} // Update state on change
        placeholder="Name"
      />
      <input
        type="email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        placeholder="Email"
      />
      <button type="submit">Submit</button>
    </form>
  );
}

// UNCONTROLLED COMPONENT
import { useRef } from 'react';

function UncontrolledForm() {
  const nameRef = useRef(null);
  const emailRef = useRef(null);

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log({
      name: nameRef.current.value,   // Read from DOM directly
      email: emailRef.current.value
    });
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={nameRef} placeholder="Name" />
      <input type="email" ref={emailRef} placeholder="Email" />
      <button type="submit">Submit</button>
    </form>
  );
}
```

> 📝 **5-mark answer:** Definitions + comparison table + both code examples.

---

# ✅ 9. Modules in Node.js `IMPORTANT`

## Definition

**Modules** are reusable blocks of code encapsulated in separate files. Node.js uses a module system to organize code and avoid global namespace pollution.

## Types of Modules

|Type|Description|Examples|
|---|---|---|
|**Core (Built-in)**|Pre-installed with Node.js|`fs`, `http`, `path`, `os`, `crypto`|
|**Local**|Files you create|`./utils.js`, `../config.js`|
|**Third-party**|Installed via npm|`express`, `mongoose`, `axios`|

## Core Modules Reference

|Module|Purpose|Key Methods|
|---|---|---|
|`fs`|File system operations|`readFile`, `writeFile`, `mkdir`|
|`http`|HTTP server/client|`createServer`, `request`|
|`path`|File path utilities|`join`, `resolve`, `extname`|
|`os`|OS information|`platform`, `cpus`, `freemem`|
|`events`|Event emitter|`on`, `emit`, `removeListener`|
|`crypto`|Cryptography|`hash`, `randomBytes`, `encrypt`|
|`stream`|Data streaming|`Readable`, `Writable`, `Transform`|
|`url`|URL parsing|`parse`, `format`, `URLSearchParams`|

## CommonJS vs ES Modules

```js
// CommonJS (traditional Node.js)
const fs = require('fs');             // Import
const path = require('path');
module.exports = { myFunction };      // Export
module.exports.greet = greet;        // Named export

// ES Modules (modern, use "type": "module" in package.json)
import fs from 'fs';                  // Import
import { readFile } from 'fs';       // Named import
export function greet(name) { ... }  // Named export
export default class App { ... }     // Default export
```

## Creating a Local Module

```js
// math.js – Create module
function add(a, b) { return a + b; }
function subtract(a, b) { return a - b; }
function multiply(a, b) { return a * b; }

module.exports = { add, subtract, multiply };

// app.js – Use the module
const math = require('./math');
console.log(math.add(5, 3));       // 8
console.log(math.subtract(10, 4)); // 6
```

> 📝 **3-mark answer:** Definition + 3 types + table of core modules + CommonJS example.

---

# ✅ 10. Streams in Node.js `IMPORTANT`

## Definition

**Streams** are objects that let you read or write data continuously in chunks, rather than loading everything into memory at once. Ideal for large files, network data, or real-time processing.

## Types of Streams

|Type|Description|Example|
|---|---|---|
|**Readable**|Read data from source|`fs.createReadStream()`, HTTP request|
|**Writable**|Write data to destination|`fs.createWriteStream()`, HTTP response|
|**Duplex**|Both readable and writable|TCP sockets|
|**Transform**|Modify data as it passes through|`zlib.createGzip()`, encryption|

## Code Examples

```js
const fs = require('fs');
const zlib = require('zlib');

// READABLE STREAM – Read large file
const readStream = fs.createReadStream('large-file.txt', { encoding: 'utf8' });

readStream.on('data', (chunk) => {
  console.log(`Received ${chunk.length} bytes`);
});

readStream.on('end', () => {
  console.log('File reading complete');
});

readStream.on('error', (err) => {
  console.error('Stream error:', err);
});

// WRITABLE STREAM – Write to file
const writeStream = fs.createWriteStream('output.txt');
writeStream.write('Hello, ');
writeStream.write('World!\n');
writeStream.end();

// PIPE – Connect streams (most common pattern)
// Reads input.txt, compresses it, writes to output.gz
fs.createReadStream('input.txt')
  .pipe(zlib.createGzip())           // Transform stream (compress)
  .pipe(fs.createWriteStream('output.gz'))
  .on('finish', () => console.log('Compressed!'));
```

## Why Streams?

|Without Streams|With Streams|
|---|---|
|Load entire file to memory|Process in small chunks|
|Memory: O(file size)|Memory: O(chunk size)|
|Server freezes for large files|Responsive always|
|Start only after full load|Start processing immediately|

> 📝 **3-mark answer:** Definition + 4 types table + pipe example.

---

# ✅ 11. TypeScript `IMPORTANT`

## Definition

**TypeScript** is a strongly-typed **superset of JavaScript** developed by Microsoft. It adds static type checking, interfaces, generics, and OOP features. TypeScript compiles to plain JavaScript.

> TypeScript = JavaScript + Type Safety + OOP features

## Core Features

|Feature|Description|Example|
|---|---|---|
|Static typing|Types checked at compile time|`let x: number = 5`|
|Interfaces|Define object shapes|`interface User { name: string }`|
|Generics|Reusable type-safe code|`function id<T>(x: T): T`|
|Decorators|Metadata for classes/methods|`@Component({})`|
|Enums|Named constants|`enum Color { Red, Blue }`|
|Type Aliases|Custom type names|`type ID = string \| number`|
|Tuple|Fixed-length array|`let pair: [string, number]`|
|Union types|Multiple possible types|`string \| number`|

## Basic TypeScript

```typescript
// Basic types
let name: string = "Harsh";
let age: number = 21;
let isStudent: boolean = true;
let scores: number[] = [95, 87, 92];
let tuple: [string, number] = ["Alice", 30];

// Union and intersection
type ID = string | number;        // Can be string or number
type Admin = User & { role: 'admin' };  // Must be both

// Optional and default
function greet(name: string, greeting?: string): string {
  return `${greeting ?? 'Hello'}, ${name}!`;
}

// Interface
interface User {
  id: number;
  name: string;
  email: string;
  age?: number;  // Optional
  readonly createdAt: Date; // Cannot be changed after creation
}

// Implementing interface
const user: User = {
  id: 1,
  name: "Harsh",
  email: "harsh@example.com",
  createdAt: new Date()
};
```

## ⭐ Generics `ADVANCED – IMPORTANT`

**Definition:** Generics allow creating reusable components that work with multiple types while maintaining type safety.

```typescript
// Generic function
function identity<T>(value: T): T {
  return value;
}

// Usage – type is inferred
identity<string>("hello");   // Returns string
identity<number>(42);        // Returns number

// Generic with constraint
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const user = { name: "Harsh", age: 21 };
getProperty(user, "name"); // ✅ "Harsh"
getProperty(user, "xyz");  // ❌ TypeScript error!

// Generic class
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
console.log(numStack.pop()); // 2
```

## ⭐ Decorators `ADVANCED`

**Definition:** Decorators are special functions prefixed with `@` that add metadata or modify classes, methods, properties, or parameters.

```typescript
// Class decorator
function Logger(constructor: Function) {
  console.log(`Class ${constructor.name} instantiated`);
}

// Method decorator
function readonly(target: any, key: string, descriptor: PropertyDescriptor) {
  descriptor.writable = false;
  return descriptor;
}

@Logger
class User {
  constructor(public name: string) {}

  @readonly
  greet() {
    return `Hello, ${this.name}`;
  }
}
```

## ⭐ Type Guards & Type Narrowing `ADVANCED`

```typescript
// Type guard – narrow down union types
function processInput(input: string | number) {
  if (typeof input === "string") {
    // TypeScript knows input is string here
    return input.toUpperCase();
  } else {
    // TypeScript knows input is number here
    return input * 2;
  }
}

// instanceof guard
function formatDate(date: Date | string) {
  if (date instanceof Date) {
    return date.toISOString();
  }
  return new Date(date).toISOString();
}

// Custom type guard
interface Cat { meow(): void; }
interface Dog { bark(): void; }

function isCat(animal: Cat | Dog): animal is Cat {
  return (animal as Cat).meow !== undefined;
}
```

> 📝 **7-mark answer:** Definition + features table + basic code + generics example + type guards.

---

# ✅ 12. Virtual DOM `VERY IMPORTANT`

## Definition

The **Virtual DOM (VDOM)** is a lightweight, in-memory representation of the real DOM. React uses it to efficiently determine what changes need to be made to the actual DOM.

## How Virtual DOM Works

```
User action (e.g., click button)
            │
            ▼
    State/Props change
            │
            ▼
  React creates new Virtual DOM tree
            │
            ▼
  Diffing Algorithm (Reconciliation)
  Compares new VDOM with previous VDOM
            │
            ▼
  Only differences (patches) identified
            │
            ▼
  React updates only changed real DOM nodes
            │
            ▼
      Browser re-paints (minimal)
```

## Real DOM vs Virtual DOM

|Feature|Real DOM|Virtual DOM|
|---|---|---|
|Location|Browser memory|JavaScript memory|
|Update speed|Slow (reflows, repaints)|Fast (pure JS operations)|
|Update scope|Often updates whole tree|Only changed nodes|
|Memory|Browser managed|Lightweight JS objects|
|Manipulation|Expensive|Cheap|
|Sync with UI|Always in sync|Snapshot, then batch update|

## Reconciliation Algorithm (Diffing)

React's diffing uses two key assumptions:

1. **Different element types** produce different trees (no comparison needed)
2. **Keys** help identify which items in a list changed

```jsx
// Keys help React identify list items efficiently
function ItemList({ items }) {
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>  {/* key = unique identifier */}
          {item.name}
        </li>
      ))}
    </ul>
  );
}
```

> 📝 **5-mark answer:** Definition + how it works (steps) + comparison table + mention reconciliation/diffing.

---

# ✅ 13. Form Validation `IMPORTANT`

## Definition

**Form validation** ensures user-submitted data meets required format and constraints before processing.

## Validation Types

|Type|When|Method|
|---|---|---|
|Client-side|Before submission|HTML5, JavaScript, React|
|Server-side|After submission|Node.js, Express|
|Real-time|As user types|React state + onChange|

## Validation Examples

```jsx
// React form validation
function RegistrationForm() {
  const [form, setForm] = useState({ name: '', email: '', password: '' });
  const [errors, setErrors] = useState({});

  const validate = () => {
    const newErrors = {};

    if (!form.name.trim()) {
      newErrors.name = 'Name is required';
    } else if (form.name.length < 2) {
      newErrors.name = 'Name must be at least 2 characters';
    }

    if (!form.email) {
      newErrors.email = 'Email is required';
    } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) {
      newErrors.email = 'Invalid email format';
    }

    if (!form.password) {
      newErrors.password = 'Password is required';
    } else if (form.password.length < 8) {
      newErrors.password = 'Password must be at least 8 characters';
    }

    return newErrors;
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    const validationErrors = validate();
    if (Object.keys(validationErrors).length === 0) {
      console.log('Form submitted:', form);
    } else {
      setErrors(validationErrors);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        value={form.name}
        onChange={e => setForm({...form, name: e.target.value})}
        placeholder="Full Name"
      />
      {errors.name && <span style={{color:'red'}}>{errors.name}</span>}

      <input
        type="email"
        value={form.email}
        onChange={e => setForm({...form, email: e.target.value})}
        placeholder="Email"
      />
      {errors.email && <span style={{color:'red'}}>{errors.email}</span>}

      <button type="submit">Register</button>
    </form>
  );
}
```

> 📝 **3-mark answer:** Definition + 3 types + short code example with error display.

---

# ✅ 14. Event Handling in React `IMPORTANT`

## React vs Plain JavaScript Events

|Feature|React|Plain JavaScript|
|---|---|---|
|Event type|Synthetic events (SyntheticEvent)|Native DOM events|
|Naming|camelCase (`onClick`)|lowercase (`onclick`)|
|Handler binding|`onClick={handler}`|`onclick="handler()"` (string)|
|Prevent default|`e.preventDefault()`|`return false` (old way)|
|Cross-browser|Handled automatically|Manual polyfills needed|

## Code Examples

```jsx
function EventExamples() {
  // Click event
  const handleClick = (e) => {
    e.preventDefault();
    console.log('Clicked!', e.target);
  };

  // Input change event
  const handleChange = (e) => {
    console.log('Value:', e.target.value);
  };

  // Keyboard event
  const handleKeyDown = (e) => {
    if (e.key === 'Enter') {
      console.log('Enter pressed');
    }
  };

  // Mouse events
  const handleMouseOver = () => console.log('Hovering');

  return (
    <div>
      <button onClick={handleClick}>Click me</button>
      <input onChange={handleChange} onKeyDown={handleKeyDown} />
      <div onMouseOver={handleMouseOver}>Hover area</div>
    </div>
  );
}
```

---

# ✅ 15. MERN Stack `IMPORTANT`

## Definition

**MERN Stack** is a full-stack JavaScript framework consisting of four technologies for building web applications.

## Components

|Letter|Technology|Role|Port|
|---|---|---|---|
|**M**|MongoDB|NoSQL Database|27017|
|**E**|Express.js|Backend Framework|—|
|**R**|React.js|Frontend Library|3000|
|**N**|Node.js|Runtime Environment|—|

## Architecture Flow

```
Browser (React) → HTTP Request → Express (Node.js) → MongoDB
Browser (React) ← HTTP Response ← Express (Node.js) ← MongoDB
```

## Basic MERN Setup

```js
// server.js – Express + Node.js backend
const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');

const app = express();
app.use(cors());
app.use(express.json());

// MongoDB connection
mongoose.connect('mongodb://localhost:27017/myapp')
  .then(() => console.log('MongoDB connected'));

// User Schema (MongoDB model)
const UserSchema = new mongoose.Schema({
  name: { type: String, required: true },
  email: { type: String, required: true, unique: true }
});
const User = mongoose.model('User', UserSchema);

// REST API Routes
app.get('/api/users', async (req, res) => {
  const users = await User.find();
  res.json(users);
});

app.post('/api/users', async (req, res) => {
  const user = new User(req.body);
  await user.save();
  res.status(201).json(user);
});

app.listen(5000, () => console.log('Server on port 5000'));
```

```jsx
// App.jsx – React frontend
import { useState, useEffect } from 'react';

function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch('http://localhost:5000/api/users')
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(user => <li key={user._id}>{user.name}</li>)}
    </ul>
  );
}
```

## Advantages of MERN

|Advantage|Explanation|
|---|---|
|Single language|JavaScript everywhere (frontend + backend + DB)|
|JSON everywhere|MongoDB stores JSON, Express sends JSON, React receives JSON|
|Large ecosystem|NPM packages for everything|
|Scalable|MongoDB scales horizontally, React is component-based|
|Community|Huge community, extensive documentation|

> 📝 **5-mark answer:** Definition + component table + architecture flow + basic code + advantages.

---

# 🚀 FINAL EXAM STRATEGY

## 🔥 MUST PREPARE Topics

|Topic|Marks|Priority|
|---|---|---|
|Node.js architecture + Event Loop|7|🔴 Must|
|React Lifecycle|7|🔴 Must|
|Props vs State|5|🔴 Must|
|Virtual DOM|5|🔴 Must|
|TypeScript + Generics|5–7|🔴 Must|
|Async Programming (all 3 patterns)|5|🟡 Important|
|JSX|3–5|🟡 Important|
|MERN Stack|5|🟡 Important|
|Controlled vs Uncontrolled|3–5|🟢 Good to have|
|Streams|3|🟢 Good to have|

## 📅 REVISION ORDER (Last Day)

```
Hour 1: Node.js architecture + Event Loop (draw diagrams)
Hour 2: React – Components, Props/State, Lifecycle
Hour 3: TypeScript – Basics, Generics, Type Guards
Hour 4: Virtual DOM + Async patterns + MERN
```

---

> 🔗 **Related Notes:** [[DevOps QB]] | [[Functional Programming QB]] | [[Software Project Management QB]]