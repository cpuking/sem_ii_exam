> 📌 **Exam Strategy:** Map/Reduce + Recursion + Polymorphism + Pattern Matching = **40+/60 guaranteed** Tags: #functional-programming #python #java #exam #questionbank

---

# 📋 TABLE OF CONTENTS

- [[#SHORT ANSWERS (2–3 Marks)]]
- [[#LONG ANSWERS (5–7 Marks)]]
- [[#CODING QUESTIONS – HIGH PRIORITY]]
- [[#Java Streams]]
- [[#Final Strategy]]

---

# ✅ SHORT ANSWERS (2–3 Marks)

---

## ⭐ 1. MapReduce in Functional Programming `REPEATED – VERY IMPORTANT`

### Definition

**MapReduce** is a programming model for processing and generating large datasets with a parallel, distributed algorithm.

- **Map phase:** Takes input data, applies a function, produces key-value pairs
- **Shuffle phase:** Groups all values with the same key together
- **Reduce phase:** Takes grouped key-value pairs, aggregates/combines them into result

### In Python (Functional Programming context)

```python
from functools import reduce

# MAP – transform each element
numbers = [1, 2, 3, 4, 5]
doubled = list(map(lambda x: x * 2, numbers))
# Result: [2, 4, 6, 8, 10]

# REDUCE – accumulate all elements into single value
total = reduce(lambda x, y: x + y, numbers)
# Result: 15

# COMBINED – find sum of squares
sum_of_squares = reduce(
    lambda acc, x: acc + x,
    map(lambda x: x**2, numbers)
)
# Result: 55
```

### Big Data Context (Hadoop MapReduce)

|Phase|Input|Process|Output|
|---|---|---|---|
|Map|Raw text files|Split + tokenize words|`("word", 1)` pairs|
|Shuffle|All key-value pairs|Group by key|`("word", [1,1,1,...])`|
|Reduce|Grouped pairs|Sum counts|`("word", total_count)`|

> 📝 **2-mark answer:** MapReduce processes large datasets using two operations: Map (transforms input to key-value pairs) and Reduce (aggregates results). Used in Hadoop for distributed computing.

---

## ⭐ 2. Fixed Point Combinator `IMPORTANT`

### Definition

A **Fixed Point Combinator** (specifically the **Y-combinator**) is a higher-order function that enables **recursion without naming functions**. It finds a function `f` such that `f(x) = x`.

### Mathematical definition

`Y = λf.(λx.f(x x))(λx.f(x x))`

### Python Implementation

```python
# Without named recursion (using Y-combinator concept)
Y = lambda f: (lambda x: f(lambda v: x(x)(v)))(lambda x: f(lambda v: x(x)(v)))

# Factorial without naming the recursive function
factorial = Y(lambda f: lambda n: 1 if n == 0 else n * f(n - 1))
print(factorial(5))  # 120

# Fibonacci without naming
fib = Y(lambda f: lambda n: n if n <= 1 else f(n-1) + f(n-2))
print(fib(10))  # 55
```

### Why it matters

- Enables recursion in lambda calculus (which has no named functions)
- Theoretical foundation of functional languages
- Demonstrates that recursion is not a primitive need

> 📝 **2-mark answer:** A fixed point combinator (Y-combinator) enables recursion without naming functions by finding a fixed point `f(x) = x`. Used in lambda calculus.

---

## ⭐ 3. Algebraic Data Types (ADT) `IMPORTANT`

### Definition

**Algebraic Data Types** are composite types formed by combining other types. Two kinds:

- **Sum types (OR):** Value is one of several types (like `Either`, `Maybe`, `Option`)
- **Product types (AND):** Value contains multiple fields together (like tuples, records)

### Types

|ADT Type|Description|Example|
|---|---|---|
|**Sum type**|One of several alternatives|`Circle \| Rectangle \| Triangle`|
|**Product type**|Combination of fields|`(Int, String, Bool)` — a tuple|
|**Recursive type**|Type defined in terms of itself|Linked list, binary tree|

### Python Examples

```python
from dataclasses import dataclass
from typing import Union

# Sum type – Shape can be Circle OR Rectangle
@dataclass
class Circle:
    radius: float

@dataclass
class Rectangle:
    width: float
    height: float

@dataclass
class Triangle:
    base: float
    height: float

Shape = Union[Circle, Rectangle, Triangle]

# Pattern match on ADT (Python 3.10+)
def area(shape: Shape) -> float:
    match shape:
        case Circle(radius=r):
            return 3.14159 * r * r
        case Rectangle(width=w, height=h):
            return w * h
        case Triangle(base=b, height=h):
            return 0.5 * b * h

# Usage
shapes = [Circle(5), Rectangle(4, 6), Triangle(3, 8)]
for s in shapes:
    print(f"Area: {area(s)}")
```

> 📝 **2-mark answer:** ADT is a composite type system. Sum types hold one of several alternatives (Circle | Rectangle); Product types combine multiple fields (width, height). Examples: `Maybe`, `Either`.

---

## ⭐ 4. ABC vs Type Class `IMPORTANT`

### Definitions

- **ABC (Abstract Base Class):** OOP concept in Python — defines interface that subclasses must implement
- **Type Class:** FP concept (Haskell) — defines behavior/operations that types can support

### Comparison

|Feature|ABC (Python OOP)|Type Class (Haskell/FP)|
|---|---|---|
|Paradigm|Object-Oriented|Functional Programming|
|Mechanism|Inheritance|Parametric polymorphism|
|Focus|Object structure|Type behavior/operations|
|Runtime|Enforces at class definition|Enforced at compile-time|
|Example|`from abc import ABC`|`class Eq a where`|
|Usage|Must inherit|Instances declared separately|

### Python ABC Example

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def speak(self) -> str:
        pass

    @abstractmethod
    def move(self) -> str:
        pass

class Dog(Animal):
    def speak(self): return "Woof!"
    def move(self): return "Runs on 4 legs"

class Bird(Animal):
    def speak(self): return "Tweet!"
    def move(self): return "Flies with wings"

# Dog() → works
# Animal() → raises TypeError (can't instantiate ABC)
```

### Haskell Type Class (for reference)

```haskell
-- Type class definition
class Describable a where
  describe :: a -> String

-- Instance for different types
instance Describable Int where
  describe n = "Integer: " ++ show n

instance Describable Bool where
  describe True  = "It's true"
  describe False = "It's false"
```

> 📝 **2-mark answer:** ABC is an OOP concept in Python that defines abstract interfaces for subclasses to implement. Type Class is an FP concept that defines behavior/operations a type must support, used in Haskell for ad-hoc polymorphism.

---

## ⭐ 5. Strong vs Weak Typing `IMPORTANT`

### Definitions

- **Strong typing:** Type rules are strictly enforced. You cannot mix incompatible types without explicit conversion.
- **Weak typing:** Implicit type coercion is allowed. Types can be mixed, often causing unexpected results.

### Comparison

|Feature|Strong Typing|Weak Typing|
|---|---|---|
|Type coercion|Explicit only|Implicit (automatic)|
|Mixing types|Raises error|Auto-converts|
|Safety|Higher|Lower|
|Predictability|More predictable|Surprising results|
|Examples|Python, Java, Haskell|JavaScript, PHP, C|

### Code Examples

```python
# Python – STRONG typing
x = "5"
y = 2
# print(x + y)  → TypeError: can only concatenate str to str
print(int(x) + y)  # Must explicitly convert → 7

# Type checking
print(type("hello"))  # <class 'str'>
print(type(42))       # <class 'int'>

# Python DOES have dynamic typing (types checked at runtime)
# But it is STRONGLY typed (no implicit coercion)
```

```javascript
// JavaScript – WEAK typing
let x = "5";
let y = 2;
console.log(x + y);  // "52" (string concatenation – surprising!)
console.log(x - y);  // 3   (numeric subtraction – auto-coerced!)
console.log(x * y);  // 10  (numeric multiplication)

// Type coercion table
console.log(null == undefined);  // true (loose equality)
console.log(null === undefined); // false (strict equality)
```

### Dynamic vs Static Typing (different axis)

||Static|Dynamic|
|---|---|---|
|**Strong**|Java, Haskell, C++|Python, Ruby|
|**Weak**|C (somewhat)|JavaScript, PHP|

> 📝 **2-mark answer:** Strong typing enforces strict type rules and raises errors on incompatible type operations (Python: `"5" + 2` → TypeError). Weak typing allows implicit coercion (JavaScript: `"5" + 2` → `"52"`).

---

## ⭐ 6. itertools Module `IMPORTANT`

### Definition

Python's **`itertools`** module provides fast, memory-efficient tools for working with iterators, inspired by functional programming constructs.

### Key Functions

|Function|Description|Example Output|
|---|---|---|
|`count(start, step)`|Infinite counter|10, 12, 14, 16...|
|`cycle(iterable)`|Infinite cycle|A, B, C, A, B, C...|
|`repeat(val, n)`|Repeat value|5, 5, 5|
|`chain(*iterables)`|Chain iterables|[1,2] + [3,4] → 1,2,3,4|
|`islice(iter, n)`|Slice iterator|First 5 of infinite|
|`product(*iters)`|Cartesian product|All combinations|
|`permutations(iter, r)`|All orderings|(A,B), (A,C), (B,A)...|
|`combinations(iter, r)`|All unique groups|(A,B), (A,C), (B,C)...|
|`groupby(iter, key)`|Group by key|Group by first letter|
|`takewhile(pred, iter)`|Take while True|[1,2,3] from [1,2,3,7,0]|
|`dropwhile(pred, iter)`|Drop while True|[7,0] from [1,2,3,7,0]|
|`filterfalse(pred, iter)`|Filter inverse|Odd numbers|

### Code Examples

```python
import itertools

# count – infinite counter
for i in itertools.islice(itertools.count(10, 2), 5):
    print(i, end=' ')  # 10 12 14 16 18

# cycle – repeat sequence
colors = list(itertools.islice(itertools.cycle(['R', 'G', 'B']), 7))
print(colors)  # ['R', 'G', 'B', 'R', 'G', 'B', 'R']

# permutations
perms = list(itertools.permutations([1, 2, 3], 2))
print(perms)  # [(1,2), (1,3), (2,1), (2,3), (3,1), (3,2)]

# combinations
combs = list(itertools.combinations([1, 2, 3, 4], 2))
print(combs)  # [(1,2), (1,3), (1,4), (2,3), (2,4), (3,4)]

# product – cartesian product (like nested for loops)
grid = list(itertools.product([1, 2], ['A', 'B']))
print(grid)  # [(1,'A'), (1,'B'), (2,'A'), (2,'B')]

# groupby
data = [{'name': 'Alice', 'dept': 'Eng'}, {'name': 'Bob', 'dept': 'Eng'}, {'name': 'Carol', 'dept': 'HR'}]
for dept, members in itertools.groupby(data, key=lambda x: x['dept']):
    print(dept, list(members))
```

> 📝 **2-mark answer:** `itertools` provides efficient iterator-based tools. Key functions: `count()` (infinite counter), `cycle()` (infinite repeat), `permutations()` (all orderings), `combinations()` (unique groups), `product()` (cartesian product).

---

## ⭐ 7. Pattern Matching `IMPORTANT`

### Definition

**Pattern matching** is a mechanism to check a value against a series of patterns and execute code based on the first matching pattern. More powerful than `if-else` or `switch`.

### Python 3.10+ `match-case`

```python
# Basic structural matching
def describe_type(value):
    match value:
        case int():
            return f"Integer: {value}"
        case str():
            return f"String: '{value}'"
        case list():
            return f"List with {len(value)} items"
        case None:
            return "It's None"
        case _:
            return "Unknown type"

# Match on value
def http_status(code):
    match code:
        case 200:
            return "OK"
        case 404:
            return "Not Found"
        case 500 | 503:            # OR pattern
            return "Server Error"
        case code if code >= 400:  # Guard
            return f"Client Error: {code}"
        case _:
            return "Unknown"

# Match on structure (destructuring)
def process_command(command):
    match command.split():
        case ["quit"]:
            return "Quitting"
        case ["go", direction]:
            return f"Going {direction}"
        case ["get", obj] | ["pick", "up", obj]:
            return f"Getting {obj}"
        case ["drop", *objects]:  # Capture rest
            return f"Dropping: {objects}"
        case _:
            return "Unknown command"
```

### From Question Bank: Filter 3-digit numbers

```python
# Pattern matching to filter numbers
lst = [1, 2, 222, 45, 666, 888]

# Method 1: List comprehension
result = [x for x in lst if 100 <= x <= 999]
print(result)  # [222, 666, 888]

# Method 2: filter + lambda
result = list(filter(lambda x: 100 <= x <= 999, lst))
print(result)  # [222, 666, 888]

# Method 3: match-case (Python 3.10+)
def is_three_digit(n):
    match n:
        case n if 100 <= n <= 999:
            return True
        case _:
            return False

result = [x for x in lst if is_three_digit(x)]
```

> 📝 **2-mark answer:** Pattern matching checks values against patterns and executes matching code. Python 3.10+ uses `match-case`. Simpler and more readable than complex if-elif chains.

---

## ⭐ 8. Type Polymorphism `IMPORTANT`

### Definition

**Type Polymorphism** is the ability of a function or operator to work with values of different types.

### Types of Polymorphism

|Type|Description|Example|
|---|---|---|
|**Parametric**|Single function works with any type (generics)|`def identity(x): return x`|
|**Ad-hoc**|Same name, different behavior per type (overloading)|`+` for int and str|
|**Subtype**|Derived type used where base type expected (inheritance)|`Animal` ref = `Dog` obj|
|**Duck typing**|If it behaves like a duck, it is a duck|Python's default approach|

```python
# Parametric polymorphism – works for any type
def first(lst):
    return lst[0]

first([1, 2, 3])       # Returns 1 (int)
first(["a", "b"])      # Returns "a" (str)
first([(1,2), (3,4)])  # Returns (1,2) (tuple)

# Ad-hoc polymorphism – operator overloading
class Vector:
    def __init__(self, x, y):
        self.x, self.y = x, y

    def __add__(self, other):  # Overloads +
        return Vector(self.x + other.x, self.y + other.y)

    def __str__(self):
        return f"Vector({self.x}, {self.y})"

v1 = Vector(1, 2)
v2 = Vector(3, 4)
print(v1 + v2)  # Vector(4, 6) – using overloaded +

# Duck typing – Python's polymorphism
def make_sound(animal):
    animal.speak()  # Works for any object with speak() method

class Dog:
    def speak(self): print("Woof")

class Cat:
    def speak(self): print("Meow")

make_sound(Dog())  # Woof
make_sound(Cat())  # Meow
```

> 📝 **2-mark answer:** Type polymorphism allows functions to work with multiple types. Types: parametric (generics), ad-hoc (overloading), subtype (inheritance), duck typing (Python). Example: `def first(lst)` works for any list type.

---

# 🔥 LONG ANSWERS (5–7 Marks)

---

## ⭐ 1. Pure Functions `VERY IMPORTANT`

### Definition

A **pure function** is a function where:

1. **Deterministic:** Same input always produces same output
2. **No side effects:** Does not modify external state, I/O, global variables

### Characteristics

|Property|Description|Test|
|---|---|---|
|Deterministic|Same args → same result always|Call 1000 times, same output|
|No side effects|Doesn't modify external state|No global vars, no I/O|
|Referential transparency|Can replace call with its result|`add(2,3)` = `5` always|
|Immutable inputs|Does not modify its arguments|Input unchanged after call|

### Pure vs Impure Examples

```python
# ✅ PURE FUNCTIONS
def add(a, b):
    return a + b

def square(x):
    return x * x

def get_max(lst):
    return max(lst)  # Doesn't modify lst

def format_name(first, last):
    return f"{first} {last}".strip().title()

# ❌ IMPURE FUNCTIONS – why they're impure
counter = 0

def impure_increment():
    global counter          # Modifies external state
    counter += 1
    return counter

def impure_random():
    import random
    return random.randint(1, 10)  # Different output each time

def impure_log(msg):
    print(msg)              # Side effect: I/O
    return msg

def impure_modify_list(lst):
    lst.append(0)           # Mutates input
    return lst
```

### Benefits of Pure Functions

|Benefit|Explanation|
|---|---|
|**Testable**|No mocks needed — just test input/output|
|**Memoizable**|Results can be cached (same input → cache)|
|**Parallelizable**|No shared state → safe to run in parallel|
|**Composable**|Combine pure functions: `f(g(x))`|
|**Debuggable**|Easier to trace — no hidden state changes|
|**Refactorable**|Safe to reorder or replace function calls|

### Memoization (caching pure functions)

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# First call computes; subsequent calls use cache
print(fibonacci(100))  # Fast because of memoization
```

> 📝 **5-mark answer:** Definition + characteristics table + pure vs impure examples + benefits table + mention memoization.

---

## ⭐ 2. Map & Reduce (Detailed) `VERY VERY IMPORTANT`

### Map

**Definition:** `map()` applies a function to every element of an iterable, returning an iterator of results.

```python
# Syntax: map(function, iterable)

# Double all numbers
numbers = [1, 2, 3, 4, 5]
doubled = list(map(lambda x: x * 2, numbers))
print(doubled)  # [2, 4, 6, 8, 10]

# Square all numbers
squares = list(map(lambda x: x**2, numbers))
print(squares)  # [1, 4, 9, 16, 25]

# Convert to strings
str_nums = list(map(str, numbers))
print(str_nums)  # ['1', '2', '3', '4', '5']

# Map with custom function
def celsius_to_fahrenheit(c):
    return (c * 9/5) + 32

temps_c = [0, 20, 37, 100]
temps_f = list(map(celsius_to_fahrenheit, temps_c))
print(temps_f)  # [32.0, 68.0, 98.6, 212.0]

# Map with multiple iterables
a = [1, 2, 3]
b = [10, 20, 30]
sums = list(map(lambda x, y: x + y, a, b))
print(sums)  # [11, 22, 33]
```

### Reduce

**Definition:** `reduce()` applies a function cumulatively to elements, reducing the iterable to a single value.

```python
from functools import reduce

# Sum all numbers
numbers = [1, 2, 3, 4, 5]
total = reduce(lambda x, y: x + y, numbers)
print(total)  # 15  (((((1+2)+3)+4)+5))

# Product of all numbers
product = reduce(lambda x, y: x * y, numbers)
print(product)  # 120

# Find maximum
maximum = reduce(lambda x, y: x if x > y else y, numbers)
print(maximum)  # 5

# Flatten nested list
nested = [[1, 2], [3, 4], [5, 6]]
flat = reduce(lambda acc, x: acc + x, nested, [])
print(flat)  # [1, 2, 3, 4, 5, 6]

# Build dictionary from pairs
pairs = [('a', 1), ('b', 2), ('c', 3)]
d = reduce(lambda acc, kv: {**acc, kv[0]: kv[1]}, pairs, {})
print(d)  # {'a': 1, 'b': 2, 'c': 3}
```

### Map + Filter + Reduce Pipeline

```python
from functools import reduce

data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

result = reduce(
    lambda acc, x: acc + x,           # Step 3: Sum them
    map(
        lambda x: x ** 2,             # Step 2: Square each
        filter(lambda x: x % 2 == 0, data)  # Step 1: Even only
    )
)
print(result)  # 4+16+36+64+100 = 220
```

> 📝 **5-mark answer:** Map definition + 3 map examples + Reduce definition + 3 reduce examples + pipeline example.

---

## ⭐ 3. Recursion `VERY IMPORTANT`

### Definition

**Recursion** is a programming technique where a function calls itself to solve smaller instances of the same problem. Every recursive function must have a **base case** (stop condition) and a **recursive case**.

### Structure

```python
def recursive_function(input):
    # BASE CASE – stop recursion
    if base_condition:
        return base_value

    # RECURSIVE CASE – reduce problem, call self
    return recursive_function(smaller_input)
```

### Classic Examples

```python
# 1. FACTORIAL
def factorial(n):
    if n == 0 or n == 1:  # Base case
        return 1
    return n * factorial(n - 1)  # Recursive case

# Trace: factorial(4)
# = 4 * factorial(3)
# = 4 * 3 * factorial(2)
# = 4 * 3 * 2 * factorial(1)
# = 4 * 3 * 2 * 1 = 24


# 2. FIBONACCI
def fibonacci(n):
    if n <= 1:          # Base case
        return n
    return fibonacci(n-1) + fibonacci(n-2)  # Recursive case

# 3. SUM OF LIST
def sum_list(lst):
    if not lst:         # Base case: empty list
        return 0
    return lst[0] + sum_list(lst[1:])  # First + rest

# 4. BINARY SEARCH (recursive)
def binary_search(arr, target, low, high):
    if low > high:      # Base case: not found
        return -1
    mid = (low + high) // 2
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search(arr, target, mid+1, high)
    else:
        return binary_search(arr, target, low, mid-1)

# 5. FLATTEN NESTED LIST
def flatten(lst):
    if not lst:
        return []
    if isinstance(lst[0], list):
        return flatten(lst[0]) + flatten(lst[1:])
    return [lst[0]] + flatten(lst[1:])

print(flatten([1, [2, [3, 4]], 5]))  # [1, 2, 3, 4, 5]
```

### Tail Recursion (Optimization)

```python
# Regular recursion – builds call stack
def factorial_normal(n):
    if n == 0: return 1
    return n * factorial_normal(n-1)  # Stack grows with each call

# Tail recursive – accumulator pattern
def factorial_tail(n, acc=1):
    if n == 0: return acc
    return factorial_tail(n-1, n * acc)  # Last operation is the call
```

### Recursion vs Iteration

|Feature|Recursion|Iteration|
|---|---|---|
|Readability|Often cleaner|Can be verbose|
|Memory|Stack frames (risk of overflow)|O(1) extra space|
|Speed|Slightly slower (function calls)|Faster|
|Best for|Trees, graphs, divide & conquer|Simple loops|
|Python limit|`sys.setrecursionlimit` default 1000|No limit|

> 📝 **5-mark answer:** Definition + structure + factorial example with trace + one more example + recursion vs iteration table.

---

## ⭐ 4. Type Classes & Ad-hoc Polymorphism `IMPORTANT`

_(See detailed coverage in Short Answers section above)_

```python
# Protocol-based type classes in Python (modern approach)
from typing import Protocol

class Printable(Protocol):
    def to_string(self) -> str: ...

class Comparable(Protocol):
    def __lt__(self, other) -> bool: ...
    def __eq__(self, other) -> bool: ...

# Any class implementing these methods satisfies the Protocol
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius

    def to_string(self):
        return f"{self.celsius}°C"

    def __lt__(self, other):
        return self.celsius < other.celsius

    def __eq__(self, other):
        return self.celsius == other.celsius
```

---

## ⭐ 5. Applicative Order vs Normal Order `IMPORTANT`

### Definitions

|Feature|Applicative Order (Eager)|Normal Order (Lazy)|
|---|---|---|
|Evaluation|Arguments evaluated FIRST before passing|Arguments evaluated only when needed|
|Also known as|Call by value, strict evaluation|Call by name, lazy evaluation|
|Used in|Python, Java, C|Haskell, Scheme's `delay`|
|Infinite structures|❌ Cannot handle|✅ Can work with infinite lists|
|Performance|May compute unused values|Only computes what's needed|

### Python Example (Eager by default)

```python
# Python is EAGER (applicative order)
def always_one(x):
    return 1

# In Python, argument IS evaluated even if unused
# always_one(1/0) → ZeroDivisionError (arg evaluated first)

# Simulating LAZY evaluation with lambda
def lazy_always_one(x_thunk):
    return 1

lazy_always_one(lambda: 1/0)  # ✅ No error – lambda delays evaluation
```

### Haskell Lazy Evaluation Example

```haskell
-- Haskell is lazy – this works!
take 5 [1..]  -- Takes first 5 from infinite list [1,2,3,4,5,...]
-- Result: [1,2,3,4,5]

-- head of infinite list
head [1..]   -- Result: 1 (only evaluates what's needed)
```

### Python generators (lazy evaluation)

```python
# Generator = lazy sequence (values computed on demand)
def infinite_counter(start=0):
    while True:
        yield start
        start += 1

counter = infinite_counter()
first_5 = [next(counter) for _ in range(5)]
print(first_5)  # [0, 1, 2, 3, 4]

# itertools.count is also lazy
import itertools
import itertools
first_10_evens = list(itertools.islice(
    filter(lambda x: x % 2 == 0, itertools.count(1)),
    10
))
print(first_10_evens)  # [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

> 📝 **3-mark answer:** Applicative order evaluates arguments before function call (eager). Normal order evaluates arguments only when needed (lazy). Haskell uses lazy; Python uses eager by default but generators provide lazy evaluation.

---

# 🔥 CODING QUESTIONS (HIGH PRIORITY)

---

## ⭐ 1. Multiply All Numbers in List `REPEATED`

```python
from functools import reduce

def multiply_numbers(lst):
    return reduce(lambda x, y: x * y, lst)

# Test
print(multiply_numbers([1, 2, 3, 4, 5]))  # 120
print(multiply_numbers([2, 5, 10]))        # 100

# Alternative with initial value (handles empty list)
def safe_multiply(lst):
    return reduce(lambda x, y: x * y, lst, 1)

print(safe_multiply([]))  # 1 (empty list returns identity)
```

---

## ⭐ 2. Reverse a List `IMPORTANT`

```python
# Method 1: Slicing (most Pythonic)
def reverse_list(lst):
    return lst[::-1]

# Method 2: reversed() function
def reverse_list_v2(lst):
    return list(reversed(lst))

# Method 3: Recursive
def reverse_recursive(lst):
    if not lst:
        return []
    return [lst[-1]] + reverse_recursive(lst[:-1])

# Method 4: reduce
from functools import reduce
def reverse_reduce(lst):
    return reduce(lambda acc, x: [x] + acc, lst, [])

# Test
lst = [1, 2, 3, 4, 5]
print(reverse_list(lst))      # [5, 4, 3, 2, 1]
print(reverse_recursive(lst)) # [5, 4, 3, 2, 1]
```

---

## ⭐ 3. Filter Even Numbers `IMPORTANT`

```python
# Method 1: filter + lambda
def filter_even(lst):
    return list(filter(lambda x: x % 2 == 0, lst))

# Method 2: list comprehension
def filter_even_v2(lst):
    return [x for x in lst if x % 2 == 0]

# Method 3: filter odd (complement)
def filter_odd(lst):
    return list(filter(lambda x: x % 2 != 0, lst))

# Test
numbers = list(range(1, 11))
print(filter_even(numbers))   # [2, 4, 6, 8, 10]
print(filter_odd(numbers))    # [1, 3, 5, 7, 9]
```

---

## ⭐ 4. Squares of Even Numbers `IMPORTANT`

```python
# List comprehension (most Pythonic)
squares_of_evens = [x*x for x in range(1, 11) if x % 2 == 0]
print(squares_of_evens)  # [4, 16, 36, 64, 100]

# Using map + filter
from functools import reduce
squares_of_evens_v2 = list(
    map(lambda x: x**2,
        filter(lambda x: x % 2 == 0, range(1, 11)))
)
print(squares_of_evens_v2)  # [4, 16, 36, 64, 100]

# Sum of squares of even numbers
total = sum(x*x for x in range(1, 11) if x % 2 == 0)
print(total)  # 220
```

---

## ⭐ 5. Numbers Divisible by 3 `IMPORTANT`

```python
# List comprehension
divisible_by_3 = [x for x in range(1, 31) if x % 3 == 0]
print(divisible_by_3)
# [3, 6, 9, 12, 15, 18, 21, 24, 27, 30]

# Using filter
divisible_v2 = list(filter(lambda x: x % 3 == 0, range(1, 31)))

# Generalized function
def divisible_by(n, limit):
    return [x for x in range(1, limit + 1) if x % n == 0]

print(divisible_by(5, 50))  # [5, 10, 15, 20, 25, 30, 35, 40, 45, 50]
```

---

## ⭐ 6. Filter Countries Starting with 'I' `IMPORTANT`

```python
countries = ["India", "China", "Singapore", "Indonesia", "Italy", "Iran", "Israel"]

# Method 1: filter + lambda
result = list(filter(lambda c: c.startswith("I"), countries))
print(result)  # ['India', 'Indonesia', 'Italy', 'Iran', 'Israel']

# Method 2: list comprehension
result_v2 = [c for c in countries if c.startswith("I")]

# Method 3: regex (for complex patterns)
import re
result_v3 = [c for c in countries if re.match(r'^I', c)]

# More complex: countries with more than 5 characters starting with 'I'
long_i_countries = [c for c in countries if c.startswith("I") and len(c) > 5]
print(long_i_countries)  # ['Indonesia']
```

---

## ⭐ 7. Check if String Exists in List `IMPORTANT`

```python
lst = ["apple", "banana", "cherry", "date", "elderberry"]
s = "banana"

# Method 1: in operator (O(n))
print(s in lst)   # True
print("grape" in lst)  # False

# Method 2: any() with condition
print(any(item == s for item in lst))  # True

# Method 3: filter
found = list(filter(lambda x: x == s, lst))
print(len(found) > 0)  # True

# Method 4: for search with custom matching
def find_similar(lst, target):
    """Find strings containing the target"""
    return [item for item in lst if target.lower() in item.lower()]

print(find_similar(lst, "an"))  # ['banana']

# Set lookup (O(1) average)
lst_set = set(lst)
print("banana" in lst_set)  # True – faster for large lists
```

---

## ⭐ 8. Higher-Order Functions `IMPORTANT`

```python
# Function that returns a function
def multiplier(n):
    return lambda x: x * n

double = multiplier(2)
triple = multiplier(3)
print(double(5))   # 10
print(triple(5))   # 15

# Function that takes a function
def apply_twice(f, x):
    return f(f(x))

print(apply_twice(lambda x: x + 3, 10))  # 16 (10+3+3)
print(apply_twice(lambda x: x * 2, 3))   # 12 (3*2*2)

# Function composition
def compose(*fns):
    from functools import reduce
    return reduce(lambda f, g: lambda x: f(g(x)), fns)

add1 = lambda x: x + 1
double = lambda x: x * 2
square = lambda x: x ** 2

# Apply right to left: square, then double, then add1
pipeline = compose(add1, double, square)
print(pipeline(3))  # add1(double(square(3))) = add1(double(9)) = add1(18) = 19
```

---

# 🔥 JAVA STREAMS (IMPORTANT)

---

## ⭐ Java Streams – Core Operations `IMPORTANT`

```java
import java.util.*;
import java.util.stream.*;

List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

// 1. FILTER – keep elements matching condition
List<Integer> evens = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
// [2, 4, 6, 8, 10]

// 2. MAP – transform each element
List<Integer> squares = numbers.stream()
    .map(n -> n * n)
    .collect(Collectors.toList());
// [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

// 3. REDUCE – accumulate to single value
int sum = numbers.stream()
    .reduce(0, Integer::sum);
// 55

// 4. SORTED – sort ascending
List<Integer> sorted = numbers.stream()
    .sorted()
    .collect(Collectors.toList());

// 5. REVERSE SORT
List<Integer> reverseSorted = numbers.stream()
    .sorted(Comparator.reverseOrder())
    .collect(Collectors.toList());
// [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]

// 6. COLLECT – various collectors
long count = numbers.stream().filter(n -> n > 5).count(); // 5

String joined = Stream.of("a", "b", "c")
    .collect(Collectors.joining(", ", "[", "]")); // [a, b, c]

// 7. PIPELINE – chained operations
int sumOfSquaresOfEvens = numbers.stream()
    .filter(n -> n % 2 == 0)
    .map(n -> n * n)
    .reduce(0, Integer::sum);
// 4+16+36+64+100 = 220
```

## ⭐ Check Prime with Java Streams `IMPORTANT`

```java
import java.util.stream.IntStream;

// isPrime function
static boolean isPrime(int n) {
    if (n < 2) return false;
    if (n == 2) return true;
    if (n % 2 == 0) return false;
    return IntStream.rangeClosed(3, (int) Math.sqrt(n))
                    .filter(i -> i % 2 != 0)
                    .noneMatch(i -> n % i == 0);
}

// Find all primes in a list
List<Integer> numbers = Arrays.asList(2, 3, 4, 5, 7, 9, 11, 13, 15, 17);

List<Integer> primes = numbers.stream()
    .filter(n -> isPrime(n))
    .collect(Collectors.toList());
// [2, 3, 5, 7, 11, 13, 17]

// Check if ANY number in list is prime
boolean anyPrime = numbers.stream()
    .anyMatch(n -> isPrime(n));  // true

// Check if ALL numbers are prime
boolean allPrime = numbers.stream()
    .allMatch(n -> isPrime(n));  // false
```

---

# 🚀 FINAL EXAM STRATEGY

## 🔥 MOST REPEATED TOPICS (PYQ + QB)

|Topic|Marks|Priority|
|---|---|---|
|Map + Reduce (Python)|5–7|🔴 Must|
|Recursion (factorial/fibonacci)|5–7|🔴 Must|
|Pattern Matching|3–5|🔴 Must|
|Polymorphism (types)|3–5|🔴 Must|
|MapReduce (definition)|2–3|🟡 Important|
|Strong vs Weak typing|2–3|🟡 Important|
|Pure Functions|3–5|🟡 Important|
|Java Streams (sort/prime)|5–7|🟡 Important|
|itertools|2–3|🟢 Good to have|
|ADT|2–3|🟢 Good to have|

## 🎯 MINIMUM VIABLE PREP

Prepare only these 4 topics → score **40+/60 easily**:

1. **Map/Reduce** – Python examples memorized
2. **Recursion** – factorial, fibonacci with trace
3. **Polymorphism** – all 4 types with examples
4. **Pattern Matching** – list comprehension + match-case

## 📅 REVISION ORDER (Last Day)

```
Hour 1: Map + Filter + Reduce (Python) + pipeline
Hour 2: Recursion (factorial trace + fibonacci)
Hour 3: Polymorphism types + Pure functions
Hour 4: Pattern matching + Java Streams
```

---

> 🔗 **Related Notes:** [[DevOps_QB_Enhanced]] | [[Full_Stack_Development_QB_Enhanced]] | [[Software_Project_Management_QB_Enhanced]]