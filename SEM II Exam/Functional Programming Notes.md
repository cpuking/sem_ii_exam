# 🧠 Functional Programming Notes

**Marks:** 60 | **Priority:** 🔴 HIGH  
**Related:** [[Functional Programming PYQ]] | [[Functional Programming QB]] | [[README]]

---

## 📌 Table of Contents

1. [[#Unit 1 – Introduction to Functional Programming]]
2. [[#Unit 2 – Lambda Calculus]]
3. [[#Unit 3 – Types in Functional Programming]]
4. [[#Unit 4 – Higher-Order Functions]]
5. [[#Unit 5 – Recursion]]
6. [[#Unit 6 – Python Functional Programming]]
7. [[#Unit 7 – Advanced Concepts]]
8. [[#🔥 Most Expected Questions]]

---

## Unit 1 – Introduction to Functional Programming

### 1.1 What is Functional Programming?

**Definition:**  
Functional Programming (FP) is a **programming paradigm** where computation is treated as the evaluation of **mathematical functions**, avoiding **changing state** and **mutable data**.

**Core Philosophy:**
- Everything is a function
- No side effects
- Data is immutable (cannot be changed)

**Languages that support FP:**
- Haskell (purely functional)
- Scala
- Python (supports FP style)
- Lisp
- Erlang
- JavaScript (partial support)

---

### 1.2 Functional vs Imperative vs OOP (⭐ VERY IMPORTANT)

| Feature | Imperative | Functional | OOP |
|---|---|---|---|
| Style | Step-by-step instructions | Function evaluation | Object interactions |
| State | Mutable state | Stateless / Immutable | Stateful objects |
| Control flow | Loops (for, while) | Recursion | Method calls |
| Data | Variables change | Immutable | Encapsulated in objects |
| Side effects | Yes | No (pure functions) | Yes |
| Example languages | C, Pascal | Haskell, Scala | Java, C++, Python |
| Focus | How to do it | What to compute | Who does what |

**Example – Sum of list:**

```python
# Imperative style
total = 0
for x in [1,2,3,4,5]:
    total += x   # state is changing

# Functional style
from functools import reduce
total = reduce(lambda x, y: x + y, [1,2,3,4,5])  # no state change
```

---

### 1.3 Core Concepts of FP (⭐ GUARANTEED QUESTION)

#### 1. Pure Functions
- Same input → always same output
- No side effects (no printing, no modifying global variables)
```python
# Pure function
def add(a, b):
    return a + b  # no side effect, same output always

# Impure function
x = 10
def add_to_x(a):
    return a + x  # depends on external variable x → impure
```

#### 2. Immutability
- Once data is created, it cannot be modified
- Instead, new data is created
```python
original = (1, 2, 3)         # tuple = immutable
new = original + (4,)        # creates new tuple, original unchanged
```

#### 3. Recursion
- Functions calling themselves
- Replaces loops in FP
```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)
```

#### 4. Higher-Order Functions
- Functions that take other functions as arguments or return functions
```python
doubled = list(map(lambda x: x * 2, [1, 2, 3]))
```

#### 5. Lazy Evaluation
- Computation is delayed until result is actually needed
- Saves memory and avoids unnecessary work

#### 6. First-Class Functions
- Functions can be assigned to variables, passed as arguments, returned from functions
```python
greet = lambda name: f"Hello {name}"
print(greet("Harsh"))
```

---

### 1.4 Advantages of FP

- **Easier to test** – pure functions are predictable
- **Thread-safe** – no shared mutable state
- **Modular** – functions are small and composable
- **Fewer bugs** – no side effects
- **Easier to reason about** – mathematical foundation

---

### 1.5 Disadvantages of FP

- Steeper learning curve
- Less intuitive for beginners
- Performance overhead (creating new data instead of modifying)
- Not ideal for I/O-heavy programs

---

## Unit 2 – Lambda Calculus

### 2.1 What is Lambda Calculus? (⭐ IMPORTANT)

**Definition:**  
Lambda Calculus is a **formal mathematical system** for expressing computation based on function abstraction and application. It forms the **theoretical foundation** of functional programming.

Invented by **Alonzo Church** in the 1930s.

**Three components:**
1. **Variables** – `x`, `y`, `z`
2. **Abstraction** – defining functions: `λx.expr`
3. **Application** – applying function to argument: `(func arg)`

---

### 2.2 Lambda Notation

```
λx. x + 1     means:  a function that takes x and returns x+1
λx.λy. x + y  means:  a function that takes x and y and returns x+y
```

**In Python:**
```python
f = lambda x: x + 1
g = lambda x, y: x + y
```

---

### 2.3 Alpha Reduction (α-reduction) (⭐ REPEATED)

**Definition:**  
Alpha reduction is the **renaming of bound variables** in a lambda expression. It does NOT change the meaning — only the variable names change.

**Example:**
```
λx.x  →  λy.y   (same function, just renamed)
λx.(x + 1)  →  λa.(a + 1)
```

**Why it matters:** Avoids naming conflicts when substituting variables.

---

### 2.4 Beta Reduction (β-reduction) (⭐ IMPORTANT)

**Definition:**  
Beta reduction is the process of **applying a lambda function to its argument** — i.e., substituting the argument into the function body.

**Example:**
```
(λx. x + 1) 5
→ 5 + 1
→ 6
```

**Step-by-step:**
```
(λx. x * x) 4
→ substitute x = 4
→ 4 * 4
→ 16
```

---

### 2.5 Eta Reduction (η-reduction)

**Definition:**  
Eta reduction simplifies `λx.(f x)` to just `f` when `x` does not appear free in `f`.

```
λx.(f x)  →  f    (if x not free in f)
```

---

### 2.6 Free vs Bound Variables (⭐ IMPORTANT)

| Type | Definition | Example |
|---|---|---|
| **Bound variable** | Defined inside the lambda (the parameter) | In `λx.x`, the `x` after the dot is bound |
| **Free variable** | Not defined inside the lambda — comes from outside | In `λx.(x + y)`, `y` is free |

**Example:**
```
λx.(x + y)
- x is bound (defined by λx)
- y is free (not defined inside, comes from outer scope)
```

---

### 2.7 Fixed-Point Combinator (⭐ REPEATED)

**Definition:**  
A fixed-point combinator is a higher-order function that enables **recursion without naming functions**. The most famous is the **Y-combinator**.

**Y-Combinator concept:**
```
Y = λf.(λx.f(x x))(λx.f(x x))
```

**Why it matters:**
- In pure lambda calculus, functions have no names
- Y-combinator allows writing recursive functions even without naming them
- Used in theoretical CS and functional language implementations

---

### 2.8 Call by Value / Name / Need (⭐ IMPORTANT)

| Strategy | Description | When argument is evaluated | Also known as |
|---|---|---|---|
| **Call by Value** | Argument evaluated before passing | Before function call | Eager evaluation |
| **Call by Name** | Argument expression passed unevaluated | Each time it is used | Lazy (re-evaluated) |
| **Call by Need** | Like call by name, but result is cached | First time it is used | Memoized lazy evaluation |

**Example:**
```python
def square(x):
    return x * x

# Call by value: square(2+3) → square(5) → 25
# Call by need: compute 2+3 only when x is used, cache result
```

---

## Unit 3 – Types in Functional Programming

### 3.1 Type Systems

**Definition:**  
A type system is a set of rules that assigns a type (int, string, bool, etc.) to every value and expression in a program.

---

### 3.2 Strong vs Weak Typing (⭐ REPEATED)

| Feature | Strong Typing | Weak Typing |
|---|---|---|
| Type rules | Strict — types must match | Loose — implicit conversion allowed |
| Error detection | Errors caught early | Errors may appear at runtime |
| Example | Python, Haskell, Java | JavaScript, PHP, C |
| Type mixing | Not allowed | Allowed with coercion |

**Example:**
```python
# Strong typing (Python)
"5" + 2    # ❌ TypeError — cannot add string and int

# Weak typing (JavaScript)
"5" + 2    # ✅ "52" — auto-converts int to string
```

---

### 3.3 Static vs Dynamic Typing

| Static | Dynamic |
|---|---|
| Types checked at compile time | Types checked at runtime |
| Haskell, Java, C++ | Python, JavaScript, Ruby |
| More performance, less flexible | More flexible, slower |

---

### 3.4 Algebraic Data Types (ADT) (⭐ IMPORTANT)

**Definition:**  
An Algebraic Data Type is a **composite type** formed by combining simpler types. They model real-world data structures.

**Two kinds:**
1. **Sum type (OR)** – one of several possibilities (like enum)
2. **Product type (AND)** – combination of multiple fields (like struct/record)

**Haskell example:**
```haskell
data Shape = Circle Float          -- sum type
           | Rectangle Float Float

area :: Shape -> Float
area (Circle r)      = pi * r * r
area (Rectangle w h) = w * h
```

**Python equivalent:**
```python
from dataclasses import dataclass
from typing import Union

@dataclass
class Circle:
    radius: float

@dataclass
class Rectangle:
    width: float
    height: float

Shape = Union[Circle, Rectangle]
```

---

### 3.5 Abstract Base Classes (ABC) vs Type Classes (⭐ REPEATED)

| Feature | ABC (Python OOP) | Type Class (Haskell FP) |
|---|---|---|
| Paradigm | Object-Oriented | Functional |
| Purpose | Define interface/structure | Define behavior for types |
| Enforcement | Subclasses must implement | Types must implement methods |
| Language | Python, Java | Haskell, Scala |
| Example | `ABC` with `abstractmethod` | `Eq`, `Ord`, `Show` |

**Python ABC:**
```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof"
```

**Haskell Type Class:**
```haskell
class Describable a where
    describe :: a -> String

data Shape = Circle | Square

instance Describable Shape where
    describe Circle = "I am a circle"
    describe Square = "I am a square"
```

---

### 3.6 Type Polymorphism (⭐ IMPORTANT)

**Definition:**  
Polymorphism allows the **same function to work with different types**.

**Types:**

#### 1. Parametric Polymorphism
Function works for any type `T`:
```python
def identity(x):
    return x  # works for int, str, list, anything
```

#### 2. Ad-hoc Polymorphism (⭐ Repeated)
Same function name behaves differently based on argument type (like overloading):
```python
def add(a, b):
    return a + b

add(1, 2)        # → 3 (int addition)
add("hi", "!")   # → "hi!" (string concatenation)
```

#### 3. Subtype Polymorphism
OOP inheritance – child class method overrides parent.

---

### 3.7 Pattern Matching (⭐ IMPORTANT)

**Definition:**  
Pattern matching checks a value against a pattern and executes code based on which pattern matches. It's a powerful FP alternative to if-else chains.

**Python 3.10+ example:**
```python
def describe(shape):
    match shape:
        case "circle":
            return "Round shape"
        case "square":
            return "Equal sides"
        case _:
            return "Unknown shape"
```

**Filtering with pattern logic:**
```python
lst = [1, 2, 222, 45, 666, 888]

# Find 3-digit numbers
result = [x for x in lst if 100 <= x <= 999]
print(result)  # [222, 666, 888]
```

**Filter countries starting with 'I':**
```python
countries = ["India", "China", "Singapore", "Indonesia", "Italy"]
result = [c for c in countries if c.startswith("I")]
print(result)  # ["India", "Indonesia", "Italy"]
```

---

## Unit 4 – Higher-Order Functions

### 4.1 What are Higher-Order Functions?

**Definition:**  
A function is called a **higher-order function** if it:
1. Takes one or more functions as arguments, OR
2. Returns a function as its result

These are the core tools of functional programming.

---

### 4.2 Map (⭐ VERY IMPORTANT)

**Definition:**  
`map()` applies a function to **every element** of an iterable and returns the transformed list.

**Syntax:** `map(function, iterable)`

```python
# Double every number
numbers = [1, 2, 3, 4, 5]
doubled = list(map(lambda x: x * 2, numbers))
print(doubled)  # [2, 4, 6, 8, 10]

# Square every number
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # [1, 4, 9, 16, 25]

# Convert strings to uppercase
words = ["hello", "world"]
upper = list(map(str.upper, words))
print(upper)  # ["HELLO", "WORLD"]
```

---

### 4.3 Filter (⭐ VERY IMPORTANT)

**Definition:**  
`filter()` applies a function to each element and **keeps only elements where the function returns True**.

**Syntax:** `filter(function, iterable)`

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8]

# Keep even numbers
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4, 6, 8]

# Keep numbers > 4
greater = list(filter(lambda x: x > 4, numbers))
print(greater)  # [5, 6, 7, 8]
```

---

### 4.4 Reduce (⭐ VERY IMPORTANT)

**Definition:**  
`reduce()` applies a function **cumulatively** to all elements of a list, reducing it to a single value.

**Syntax:** `reduce(function, iterable)`  
Must import: `from functools import reduce`

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]

# Sum all numbers
total = reduce(lambda x, y: x + y, numbers)
print(total)  # 15

# Multiply all numbers
product = reduce(lambda x, y: x * y, numbers)
print(product)  # 120

# Find max value
maximum = reduce(lambda x, y: x if x > y else y, numbers)
print(maximum)  # 5
```

**Step-by-step for sum [1,2,3,4]:**
```
Step 1: 1 + 2 = 3
Step 2: 3 + 3 = 6
Step 3: 6 + 4 = 10
Final result: 10
```

---

### 4.5 MapReduce (⭐ REPEATED QUESTION)

**Definition:**  
MapReduce is a **programming model** for processing large datasets in parallel, inspired by FP's map and reduce functions.

**Two phases:**
1. **Map Phase** – transforms input data into key-value pairs
2. **Reduce Phase** – aggregates/combines the key-value pairs into a final result

**Real-world use:** Hadoop, Apache Spark for Big Data processing

**Example – Word Count:**
```python
from functools import reduce

text = ["hello world", "hello python", "world is great"]

# Map: split each sentence into words
mapped = [word for sentence in text for word in sentence.split()]
# ['hello', 'world', 'hello', 'python', 'world', 'is', 'great']

# Reduce: count occurrences
word_count = reduce(
    lambda acc, word: {**acc, word: acc.get(word, 0) + 1},
    mapped,
    {}
)
print(word_count)
# {'hello': 2, 'world': 2, 'python': 1, 'is': 1, 'great': 1}
```

**Diagram:**
```
Input Data
    ↓ MAP
Key-Value Pairs (parallel processing)
    ↓ SHUFFLE & SORT
Grouped by Key
    ↓ REDUCE
Final Output
```

---

### 4.6 Currying (⭐ IMPORTANT)

**Definition:**  
Currying transforms a function that takes **multiple arguments** into a series of functions that each take **one argument**.

Named after mathematician **Haskell Curry**.

```python
# Normal function
def add(a, b):
    return a + b

add(2, 3)  # 5

# Curried version
def add(a):
    return lambda b: a + b

add_5 = add(5)      # returns a function
print(add_5(3))     # 8
print(add(2)(3))    # 5

# Arrow notation (conceptual)
# add = a → b → a + b
```

**Why currying is useful:**
- Create specialized functions from general ones
- Partial application
- Code reuse

```python
# Practical example
multiply = lambda a: lambda b: a * b

double = multiply(2)   # specialized function
triple = multiply(3)   # specialized function

print(double(5))  # 10
print(triple(5))  # 15
```

---

### 4.7 Function Composition

**Definition:**  
Combining two or more functions so that the output of one becomes the input of the next.

```python
def compose(f, g):
    return lambda x: f(g(x))

double = lambda x: x * 2
add_one = lambda x: x + 1

double_then_add = compose(add_one, double)
print(double_then_add(3))  # (3*2)+1 = 7
```

---

## Unit 5 – Recursion

### 5.1 What is Recursion? (⭐ IMPORTANT)

**Definition:**  
Recursion is a technique where a **function calls itself** to solve a smaller subproblem until it reaches a **base case**.

**Two essential parts:**
1. **Base case** – the condition to stop recursion
2. **Recursive case** – the function calling itself with a smaller problem

```python
def factorial(n):
    # Base case
    if n == 0:
        return 1
    # Recursive case
    return n * factorial(n - 1)

print(factorial(5))  # 120
# 5 × 4 × 3 × 2 × 1 × 1 = 120
```

---

### 5.2 Recursion vs Iteration

| Feature | Recursion | Iteration |
|---|---|---|
| Mechanism | Function calls itself | Loop (for/while) |
| State | Stack frames | Loop variables |
| Readability | Often cleaner | Can be complex |
| Risk | Stack overflow if too deep | Infinite loop |
| FP preference | ✅ Preferred | ❌ Avoided |

---

### 5.3 Common Recursive Examples

**Fibonacci:**
```python
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)

print(fib(7))  # 13
```

**Sum of list:**
```python
def sum_list(lst):
    if not lst:
        return 0
    return lst[0] + sum_list(lst[1:])

print(sum_list([1,2,3,4,5]))  # 15
```

**Power:**
```python
def power(base, exp):
    if exp == 0:
        return 1
    return base * power(base, exp - 1)

print(power(2, 8))  # 256
```

---

### 5.4 Tail Recursion

**Definition:**  
Tail recursion is when the **recursive call is the last operation** in the function. Some languages optimize this to avoid stack overflow.

```python
# Regular recursion (builds stack)
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)   # multiplication happens AFTER recursive call

# Tail recursive
def factorial_tail(n, accumulator=1):
    if n == 0:
        return accumulator
    return factorial_tail(n-1, n * accumulator)  # recursive call IS the last thing
```

---

## Unit 6 – Python Functional Programming

### 6.1 Lambda Functions

**Definition:**  
Anonymous (unnamed) functions defined using the `lambda` keyword.

**Syntax:** `lambda arguments: expression`

```python
# Regular function
def square(x):
    return x * x

# Lambda equivalent
square = lambda x: x * x

# Usage
print(square(5))       # 25
print((lambda x: x*x)(5))  # 25 — immediate invocation
```

---

### 6.2 List Comprehensions

Concise way to create lists using FP style:

```python
# Squares of even numbers from 1 to 10
result = [x**2 for x in range(1, 11) if x % 2 == 0]
print(result)  # [4, 16, 36, 64, 100]

# Numbers divisible by 3 up to 30
div3 = [x for x in range(1, 31) if x % 3 == 0]
print(div3)  # [3, 6, 9, 12, 15, 18, 21, 24, 27, 30]
```

---

### 6.3 itertools Module (⭐ IMPORTANT)

**Definition:**  
`itertools` is a Python module providing **efficient iterators** for functional-style looping.

```python
import itertools

# count() – infinite counting
for i in itertools.count(10, 2):  # start=10, step=2
    if i > 20:
        break
    print(i)  # 10, 12, 14, 16, 18, 20

# cycle() – infinite cycling through a sequence
counter = 0
for c in itertools.cycle(['A', 'B', 'C']):
    if counter == 6:
        break
    print(c)  # A B C A B C
    counter += 1

# permutations()
for p in itertools.permutations([1, 2, 3], 2):
    print(p)  # (1,2),(1,3),(2,1),(2,3),(3,1),(3,2)

# combinations()
for c in itertools.combinations([1, 2, 3], 2):
    print(c)  # (1,2),(1,3),(2,3)

# chain() – concatenate iterables
combined = list(itertools.chain([1,2,3], [4,5,6]))
print(combined)  # [1,2,3,4,5,6]
```

---

### 6.4 Java Functional Programming (Streams) (⭐ IMPORTANT)

Java 8+ supports functional programming via Streams and Lambda expressions.

**Reverse sort a list:**
```java
import java.util.*;
import java.util.stream.*;

public class Main {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("apple", "banana", "cherry", "date");

        // Reverse sort using streams
        list.stream()
            .sorted(Comparator.reverseOrder())
            .forEach(System.out::println);
        // Output: date, cherry, banana, apple
    }
}
```

**Filter + Map + Collect:**
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

List<Integer> evenSquares = numbers.stream()
    .filter(n -> n % 2 == 0)           // keep even numbers
    .map(n -> n * n)                    // square them
    .collect(Collectors.toList());      // collect to list

System.out.println(evenSquares);  // [4, 16, 36, 64, 100]
```

---

## Unit 7 – Advanced Concepts

### 7.1 Immutability in FP (⭐ IMPORTANT – 5 marks)

**Definition:**  
Immutability means that **data cannot be changed** once created. Instead of modifying data, new data is created with the change.

**Why immutability matters:**
1. **Thread-safe** – no race conditions, safe in concurrent programs
2. **Predictable behavior** – data doesn't change unexpectedly
3. **No side effects** – functions don't alter external state
4. **Easy debugging** – trace values at any point
5. **Referential transparency** – same input = same output, always

**Immutability in Python:**
```python
# Immutable types in Python
x = 5          # int (immutable)
s = "hello"    # string (immutable)
t = (1, 2, 3)  # tuple (immutable)

# List is mutable (avoid in FP)
lst = [1, 2, 3]
lst[0] = 99   # ❌ mutates the list

# FP approach: create new instead
lst = [1, 2, 3]
new_lst = [99] + lst[1:]  # ✅ original unchanged
```

**Using `final` in Java for immutability:**
```java
final int x = 10;
// x = 20;  // ❌ Error: cannot reassign final variable

final List<Integer> nums = new ArrayList<>();
nums.add(1);  // ✅ Can still modify list contents
// nums = new ArrayList<>();  // ❌ Cannot reassign reference
```

---

### 7.2 Lazy Evaluation (⭐ VERY REPEATED)

**Definition:**  
Lazy evaluation (also called **call-by-need**) delays the computation of an expression until its value is **actually needed**.

**Benefits:**
- Improves performance by avoiding unnecessary computation
- Supports **infinite data structures** (only compute as much as needed)
- Reduces memory usage

**Python generators (lazy evaluation):**
```python
# Eager (computes everything at once)
squares_eager = [x**2 for x in range(1000000)]  # ❌ computes all 1M values immediately

# Lazy (generator – computes one at a time)
def squares_lazy(n):
    for x in range(n):
        yield x**2  # computes only when asked

gen = squares_lazy(1000000)
print(next(gen))  # 0  — only computes first value
print(next(gen))  # 1  — only computes second value

# Infinite sequence (only possible with lazy evaluation)
def natural_numbers():
    n = 0
    while True:
        yield n
        n += 1

nums = natural_numbers()
print(next(nums))  # 0
print(next(nums))  # 1
print(next(nums))  # 2
```

---

### 7.3 Applicative vs Normal Order Evaluation

| Order | Description | When args are evaluated | Also called |
|---|---|---|---|
| **Applicative Order** | Evaluate arguments first, then apply function | Before function call | Eager / Call-by-value |
| **Normal Order** | Apply function first, evaluate args later | When needed | Lazy / Call-by-name |

**Example:**
```
f(x) = x + x
g()  = random number

f(g())  – which order?

Applicative: evaluate g() once → f(5) → 5+5=10
Normal:      substitute first → g()+g() → may call g() twice!
```

---

### 7.4 Pure vs Impure Functions (⭐ IMPORTANT)

| Feature | Pure Function | Impure Function |
|---|---|---|
| Same input → same output? | ✅ Always | ❌ Not guaranteed |
| Side effects? | ❌ None | ✅ Yes |
| External dependencies? | ❌ No | ✅ Yes |
| Predictable? | ✅ Yes | ❌ No |
| Testable? | ✅ Easy | ❌ Hard |

```python
import random

# Pure function
def add(a, b):
    return a + b  # ✅ same output for same input

# Impure function – depends on external state
balance = 1000
def withdraw(amount):
    global balance
    balance -= amount  # ❌ side effect: modifies external variable
    return balance

# Impure function – uses randomness
def roll_dice():
    return random.randint(1, 6)  # ❌ different output each call
```

---

## 🔥 Most Expected Questions

> From analysis of PYQ + QB combined

| Question | Marks | Frequency |
|---|---|---|
| MapReduce explanation | 2–3 | ⭐⭐⭐ |
| Lazy evaluation + example | 3–5 | ⭐⭐⭐ |
| Map/Filter/Reduce code | 5–7 | ⭐⭐⭐ |
| Currying with example | 3–5 | ⭐⭐ |
| Recursion (factorial/fibonacci) | 3–5 | ⭐⭐⭐ |
| Pure vs Impure functions | 3–5 | ⭐⭐ |
| Alpha/Beta reduction | 2–3 | ⭐⭐ |
| Strong vs Weak typing | 2–3 | ⭐⭐ |
| ABC vs Type Class | 3 | ⭐⭐ |
| Pattern matching | 3–5 | ⭐⭐ |
| Immutability (Java/Python) | 5 | ⭐⭐ |
| Imperative vs FP | 3–4 | ⭐⭐ |

---

## 📝 Quick Revision Summary

```
FP = Pure Functions + Immutability + Recursion + Higher-Order Functions + Lazy Eval

Lambda Calculus:
  - α-reduction = renaming variables (doesn't change meaning)
  - β-reduction = applying function to argument
  - Free variable = not in lambda params
  - Bound variable = defined in lambda params

Key Functions:
  - map()    → transform each element
  - filter() → keep elements matching condition
  - reduce() → collapse to single value
  - lambda   → anonymous function

Typing:
  - Strong = strict (Python, Haskell)
  - Weak = flexible (JavaScript, C)
  - Static = checked at compile time
  - Dynamic = checked at runtime
```

---

**See also:** [[Functional Programming PYQ]] | [[Functional Programming QB]] | [[README]]
