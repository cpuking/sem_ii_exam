# 🔥 Functional Programming – Previous Year Questions

**Subject:** Functional Programming | **Marks:** 60  
**Related:** [[Functional Programming Notes]] | [[Functional Programming QB]] | [[README]]

> 💡 **Strategy:** Attempt best answers, not all. Quality > Quantity.

---

## Q1 – Short Answers (12 marks) — Attempt any 6

*Each worth 2 marks. Write: definition + 1 example/point*

---

### a) Role of MapReduce *(2 marks)*
→ See: [[Functional Programming Notes#4.5 MapReduce]]

**Answer:**  
MapReduce processes large datasets in parallel using two phases:
- **Map:** transforms input data into key-value pairs
- **Reduce:** aggregates key-value pairs into final result

Used in Hadoop for Big Data processing.

---

### b) Define Functional Programming + Languages *(2 marks)*
→ See: [[Functional Programming Notes#1.1 What is Functional Programming?]]

**Answer:**  
Functional Programming is a paradigm where computation is done using **pure functions without changing state**.

Languages: Haskell, Scala, Python, Lisp

---

### c) Why Lazy Evaluation is useful *(2 marks)*
→ See: [[Functional Programming Notes#7.2 Lazy Evaluation]]

**Answer:**  
Lazy evaluation delays computation until result is actually needed.

Benefits:
- Improves performance by skipping unnecessary computation
- Supports infinite data structures (e.g., generators in Python)
- Reduces memory usage

---

### d) Fixed Point Combinator *(2 marks)*
→ See: [[Functional Programming Notes#2.7 Fixed-Point Combinator]]

**Answer:**  
A fixed-point combinator (e.g., Y-combinator) allows **recursion without naming functions**.

`Y = λf.(λx.f(x x))(λx.f(x x))`

Used in lambda calculus for defining recursive functions.

---

### e) Alpha Reduction *(2 marks)*
→ See: [[Functional Programming Notes#2.3 Alpha Reduction]]

**Answer:**  
Alpha reduction is **renaming bound variables** in a lambda expression without changing its meaning.

```
λx.x  →  λy.y   (same function, different variable name)
λx.(x+1)  →  λa.(a+1)
```

---

### f) ABC vs Type Class *(2 marks)*
→ See: [[Functional Programming Notes#3.5 Abstract Base Classes ABC vs Type Classes]]

**Answer:**

| ABC (Python OOP) | Type Class (Haskell FP) |
|---|---|
| Defines structure/interface | Defines behavior for types |
| Object-oriented | Functional programming |
| `abstractmethod` decorator | `Eq`, `Ord`, `Show` |

---

### g) Strong Typing *(2 marks)*
→ See: [[Functional Programming Notes#3.2 Strong vs Weak Typing]]

**Answer:**  
Strong typing means variables must follow **strict type rules** and types cannot be mixed implicitly.

```python
"5" + 2   # ❌ TypeError in Python (strongly typed)
"5" + 2   # ✅ "52" in JavaScript (weakly typed)
```

---

### h) Core Concepts of FP *(2 marks)*
→ See: [[Functional Programming Notes#1.3 Core Concepts of FP]]

**Answer:**
- Pure functions (no side effects)
- Immutability (data cannot change)
- Recursion (instead of loops)
- Higher-order functions
- Lazy evaluation

---

## Q2 – Theory Questions (10 marks)

---

### Q2(a)(i) Imperative vs Functional Programming *(4 marks)*
→ See: [[Functional Programming Notes#1.2 Functional vs Imperative vs OOP]]

**Answer:**

| Feature | Imperative | Functional |
|---|---|---|
| State | Mutable | Stateless/Immutable |
| Control | Loops | Recursion |
| Data | Variables change | Data is immutable |
| Side effects | Yes | No (pure functions) |
| Example | C, Java | Haskell, Scala |
| Readability | Procedural steps | Declarative expressions |

**Code example:**
```python
# Imperative — state changes
total = 0
for x in [1,2,3]: total += x

# Functional — no state change
from functools import reduce
total = reduce(lambda x, y: x + y, [1,2,3])
```

---

### Q2(a)(ii) Algebraic Data Types (ADT) *(3 marks)*
→ See: [[Functional Programming Notes#3.4 Algebraic Data Types ADT]]

**Answer:**  
ADT is a **composite type** formed by combining simpler types.

**Two kinds:**
- **Sum type** – one of several options (OR)
- **Product type** – combination of multiple fields (AND)

```haskell
-- Haskell ADT
data Shape = Circle Float | Rectangle Float Float

area :: Shape -> Float
area (Circle r)      = pi * r * r
area (Rectangle w h) = w * h
```

---

### Q2(b) Immutability *(5 marks)*
→ See: [[Functional Programming Notes#7.1 Immutability in FP]]

**Answer:**  
Immutability means **data cannot be changed** after creation. Instead of modifying, new data is created.

**Advantages:**
1. **Thread-safe** – no race conditions in concurrent programs
2. **Predictable behavior** – values don't change unexpectedly
3. **No side effects** – functions don't alter external state
4. **Easier debugging** – trace values at any point
5. **Referential transparency** – same input always gives same output

**Achieving immutability in Java:**
```java
// Using final keyword
final int x = 10;
// x = 20;  ❌ Error

// Using immutable collections
List<Integer> immutable = Collections.unmodifiableList(
    Arrays.asList(1, 2, 3)
);

// Using streams (functional style)
List<Integer> doubled = nums.stream()
    .map(n -> n * 2)
    .collect(Collectors.toList());  // creates new list, original unchanged
```

---

## Q3 – Coding Questions (10 marks)

---

### Q3(a)(i) Java – Reverse Sort using FP *(4 marks)*
→ See: [[Functional Programming Notes#6.4 Java Functional Programming Streams]]

**Answer:**
```java
import java.util.*;
import java.util.stream.*;

public class ReverseSortDemo {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("apple", "banana", "cherry", "date");

        System.out.println("Reverse sorted:");
        list.stream()
            .sorted(Comparator.reverseOrder())
            .forEach(System.out::println);
        // Output: date, cherry, banana, apple
    }
}
```

---

### Q3(a)(ii) Multiply Numbers (Python) *(3 marks)*
→ See: [[Functional Programming Notes#4.4 Reduce]]

**Answer:**
```python
from functools import reduce

def multiply_numbers(lst):
    return reduce(lambda x, y: x * y, lst)

print(multiply_numbers([1, 2, 3, 4]))   # 24
print(multiply_numbers([2, 5, 10]))      # 100
```

---

### Q3(b) Pure vs Impure Functions *(5 marks)*
→ See: [[Functional Programming Notes#7.4 Pure vs Impure Functions]]

**Answer:**

**Pure Function:**
- No side effects
- Same output for same input
- No dependency on external state

```python
def add(a, b):
    return a + b   # ✅ pure: predictable, testable
```

**Impure Function:**
- Has side effects (modifies external state, does I/O)
- Output may vary for same input

```python
import random
x = 10

def add_to_x(a):      # ❌ impure: depends on external x
    return a + x

def roll_dice():       # ❌ impure: random output
    return random.randint(1, 6)

def save_to_file(data):  # ❌ impure: side effect (I/O)
    with open('file.txt', 'w') as f:
        f.write(data)
```

**Comparison table:**

| Feature | Pure | Impure |
|---|---|---|
| Same output? | ✅ Always | ❌ Not guaranteed |
| Side effects | ❌ None | ✅ Yes |
| Testable? | ✅ Easy | ❌ Harder |
| Predictable? | ✅ Yes | ❌ No |

---

## Q4 – Higher-Order Functions (10 marks)

---

### Map & Reduce *(5 marks)*
→ See: [[Functional Programming Notes#4.2 Map]] and [[Functional Programming Notes#4.4 Reduce]]

**Answer:**

**Map** – apply function to every element:
```python
numbers = [1, 2, 3, 4, 5]
doubled = list(map(lambda x: x * 2, numbers))
print(doubled)   # [2, 4, 6, 8, 10]
```

**Reduce** – collapse list to single value:
```python
from functools import reduce
total = reduce(lambda x, y: x + y, numbers)
print(total)     # 15

product = reduce(lambda x, y: x * y, numbers)
print(product)   # 120
```

---

### Call by Value / Name / Need *(5 marks)*
→ See: [[Functional Programming Notes#2.8 Call by Value Name Need]]

**Answer:**

| Type | When evaluated | Also known as |
|---|---|---|
| Call by Value | Before function call (eager) | Applicative order |
| Call by Name | Each time arg is used | Lazy (re-evaluated) |
| Call by Need | First use, then cached | Memoized lazy |

---

## Q5 – Advanced Topics (10 marks)

---

### Lazy Evaluation *(4 marks)*
→ See: [[Functional Programming Notes#7.2 Lazy Evaluation]]

**Answer:**
```python
# Generator = lazy evaluation
def squares_lazy(n):
    for x in range(n):
        yield x ** 2   # computed only when requested

gen = squares_lazy(1000000)
print(next(gen))  # 0  — only first is computed
print(next(gen))  # 1  — then second
```

---

### Currying *(3 marks)*
→ See: [[Functional Programming Notes#4.6 Currying]]

**Answer:**
```python
# Curried add function
add = lambda a: lambda b: a + b

add_5 = add(5)     # partially applied
print(add_5(3))    # 8
print(add(2)(3))   # 5
```

---

### itertools Module *(3 marks)*
→ See: [[Functional Programming Notes#6.3 itertools Module]]

**Answer:**
```python
import itertools

# count() – infinite counter
for i in itertools.count(1, 2):   # 1,3,5,7,...
    if i > 9: break
    print(i)

# permutations()
list(itertools.permutations([1,2,3], 2))
# [(1,2),(1,3),(2,1),(2,3),(3,1),(3,2)]
```

---

## Q6 – Coding (10 marks)

---

### Filter Even Numbers *(3 marks)*
```python
def filter_even_numbers(lst):
    return list(filter(lambda x: x % 2 == 0, lst))

print(filter_even_numbers([1,2,3,4,5,6,7,8]))
# [2, 4, 6, 8]
```

---

### Currying Example *(4 marks)*
```python
# Currying with practical use
multiply = lambda a: lambda b: a * b

double = multiply(2)
triple = multiply(3)

print(list(map(double, [1,2,3,4,5])))  # [2,4,6,8,10]
print(list(map(triple, [1,2,3,4,5])))  # [3,6,9,12,15]
```

---

### Free vs Bound Variables *(3 marks)*
→ See: [[Functional Programming Notes#2.6 Free vs Bound Variables]]

**Answer:**
- **Bound variable:** defined by the lambda parameter
- **Free variable:** comes from outside the lambda

```
λx.(x + y)
  x = bound (defined by λx)
  y = free (from outer scope)
```

---

## Q7 – Final Questions (10 marks)

---

### Pattern Matching *(4 marks)*
→ See: [[Functional Programming Notes#3.7 Pattern Matching]]

```python
lst = [1, 2, 222, 45, 666, 888]

# Find 3-digit numbers using pattern logic
result = [x for x in lst if 100 <= x <= 999]
print(result)  # [222, 666, 888]

# Filter countries starting with 'I'
countries = ["India", "China", "Singapore", "Indonesia", "Italy"]
result = [c for c in countries if c.startswith("I")]
print(result)  # ['India', 'Indonesia', 'Italy']
```

---

### Strong vs Weak Typing *(3 marks)*

| Feature | Strong Typing | Weak Typing |
|---|---|---|
| Type rules | Strict | Flexible |
| Type mixing | ❌ Error | ✅ Auto-converted |
| Example | Python, Haskell | JavaScript, PHP |
| Error detection | Early | Late / Runtime |

---

### Recursion *(3 marks)*
→ See: [[Functional Programming Notes#5.1 What is Recursion?]]

```python
def factorial(n):
    if n == 0:           # base case
        return 1
    return n * factorial(n - 1)  # recursive case

print(factorial(5))  # 120
```

---

## 🏆 Most Repeated Topics (Ranked)

1. 🥇 **Map / Filter / Reduce** – code + explanation
2. 🥇 **Lazy Evaluation** – concept + generator example
3. 🥇 **Recursion** – factorial or fibonacci
4. 🥈 **Currying** – example
5. 🥈 **MapReduce** – theory
6. 🥈 **Alpha reduction** – definition + example
7. 🥉 **Strong vs Weak typing**
8. 🥉 **ABC vs Type class**

---

**See also:** [[Functional Programming Notes]] | [[Functional Programming QB]] | [[README]]
