# 🔥 FP – Q1 (VERY IMPORTANT – 12 marks)

You need to attempt **any 6**, but I’ll give ALL.

---

## 🔹 a) Role of MapReduce

**Answer:**  
MapReduce is used to process large datasets in parallel.

- **Map:** transforms input data
    
- **Reduce:** aggregates results
    

👉 Used in Hadoop for big data processing.

---

## 🔹 b) Define Functional Programming + Languages

**Answer:**  
Functional Programming is a paradigm where computation is done using **pure functions without changing state**.

Languages:

- Haskell
    
- Scala
    
- Python
    
- Lisp
    

---

## 🔹 c) Why Lazy Evaluation is useful

**Answer:**  
Lazy evaluation delays computation until needed.

Benefits:

- Improves performance
    
- Avoids unnecessary calculations
    
- Supports infinite data structures
    

---

## 🔹 d) Fixed Point Combinator

**Answer:**  
A fixed-point combinator (like Y-combinator) allows **recursion without naming functions**.

👉 Used in lambda calculus.

---

## 🔹 e) Alpha Reduction

**Answer:**  
Alpha reduction is renaming bound variables in lambda expressions.

Example:

```
λx.x  →  λy.y
```

---

## 🔹 f) ABC vs Type Class

**Answer:**

|ABC|Type Class|
|---|---|
|Used in OOP|Used in FP|
|Defines methods|Defines behavior|
|Python supports ABC|Haskell uses type classes|

---

## 🔹 g) Strong Typing

**Answer:**  
Strong typing means variables must follow strict type rules and cannot be mixed implicitly.

Example:

```
"5" + 2 ❌ (error)
```

---

## 🔹 h) Core Concepts of FP

**Answer:**

- Pure functions
    
- Immutability
    
- Recursion
    
- Higher-order functions
    
- Lazy evaluation
    

---

# 🎯 MOST IMPORTANT FROM Q1

👉 These WILL repeat:

- MapReduce ✅
    
- Lazy evaluation ✅
    
- Alpha reduction ✅
    
- Core concepts ✅
    

---

# 🔥 Q2 (VERY IMPORTANT THEORY)

---

## 🔹 Q2(a)(i) Imperative vs Functional Programming

**Answer:**

|Imperative|Functional|
|---|---|
|Uses state|Stateless|
|Uses loops|Uses recursion|
|Changes variables|Immutable data|
|Example: C, Java|Example: Haskell, Scala|

---

## 🔹 Q2(a)(ii) Algebraic Data Types (ADT)

**Answer:**  
ADT is a composite type formed by combining other types.

Example:

```
data Shape = Circle r | Rectangle w h
```

👉 Used to model complex data.

---

## 🔹 Q2(b) Immutability

**Answer (5 marks):**

Immutability means data cannot be changed after creation.

### Advantages:

- Thread-safe
    
- Predictable behavior
    
- No side effects
    

### In Java:

- Use final keyword
    
- Use streams and lambda
    
- Avoid modifying objects
    

---

# 🔥 Q3 (VERY SCORING – CODING + THEORY)

---

## 🔹 Q3(a)(i) Java Program (Reverse Sort using FP)

**Answer:**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("apple", "banana", "cherry");

        list.stream()
            .sorted(Comparator.reverseOrder())
            .forEach(System.out::println);
    }
}
```

---

## 🔹 Q3(a)(ii) Multiply Numbers (Python)

**Answer:**

```python
from functools import reduce

def multiply_numbers(lst):
    return reduce(lambda x, y: x * y, lst)

print(multiply_numbers([1,2,3,4]))
```

---

## 🔹 Q3(b) Pure vs Impure Functions

**Answer:**

### Pure Function:

- No side effects
    
- Same output for same input
    

Example:

```python
def add(a, b):
    return a + b
```

### Impure Function:

- Depends on external state
    

Example:

```python
x = 10
def add(a):
    return a + x
```

---

# 🔥 Q4 (VERY IMPORTANT)

---

## 🔹 Map & Reduce (VERY IMPORTANT)

**Answer:**

### Map:

Applies function to all elements

```python
list(map(lambda x: x*2, [1,2,3]))
```

### Reduce:

Combines elements

```python
from functools import reduce
reduce(lambda x,y: x+y, [1,2,3])
```

---

## 🔹 Call by Value / Name / Need

**Answer:**

|Type|Meaning|
|---|---|
|Call by Value|Value passed|
|Call by Name|Expression passed|
|Call by Need|Lazy evaluation|

---

# 🔥 Q5 (IMPORTANT)

---

## 🔹 Lazy Evaluation (again repeated!)

**Answer:**  
Execution is delayed until needed.

Example:

```python
def gen():
    yield 1
    yield 2
```

---

## 🔹 Ad-hoc Polymorphism

**Answer:**  
Same function behaves differently for different types.

Example:

```
+ operator (int vs string)
```

---

## 🔹 itertools Module

**Answer:**

Used for efficient looping.

Functions:

- `count()`
    
- `cycle()`
    
- `permutations()`
    

---

# 🔥 Q6 (VERY IMPORTANT)

---

## 🔹 Currying

**Answer:**  
Breaking function into multiple functions.

Example:

```python
def add(a):
    return lambda b: a + b
```

---

## 🔹 Filter Even Numbers

```python
def filter_even_numbers(lst):
    return list(filter(lambda x: x % 2 == 0, lst))
```

---

## 🔹 Free vs Bound Variables

- **Free:** not defined inside function
    
- **Bound:** defined inside lambda
    

---

# 🔥 Q7 (IMPORTANT)

---

## 🔹 Pattern Matching

**Answer:**  
Matching values with patterns (used in FP languages)

---

## 🔹 Strong vs Weak Typing

|Strong|Weak|
|---|---|
|Strict|Flexible|
|Example: Python|Example: JavaScript|

---

## 🔹 Recursion

**Answer:**  
Function calling itself

Example:

```python
def fact(n):
    if n == 0:
        return 1
    return n * fact(n-1)
```

---

# 🚀 FP FINAL ANALYSIS (VERY IMPORTANT)

From this PYQ:

### 🔥 MOST REPEATED TOPICS:

- Lazy evaluation ✅
    
- Map / Reduce ✅
    
- Currying ✅
    
- Recursion ✅
    
- Lambda calculus basics ✅
    

👉 If you master these → **you can score 45+ easily**

---
