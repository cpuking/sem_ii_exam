# 🔥 FP QUESTION BANK – HIGH-YIELD SET

We’ll do this smartly:

- Short answers (2–3 marks)
    
- Long answers (5+ marks)
    
- Coding (VERY IMPORTANT)
    

---

# ✅ 🔹 VERY IMPORTANT SHORT ANSWERS

---

## ⭐ 1. MapReduce in Functional Programming (REPEATED)

**Answer:**

MapReduce is a programming model used to process large datasets.

- **Map:** transforms input into key-value pairs
    
- **Reduce:** combines results
    

👉 Used in big data (Hadoop)

---

## ⭐ 2. Fixed Point Combinator

**Answer:**  
A fixed point combinator enables recursion without naming functions.

Example:

- Y-combinator
    

---

## ⭐ 3. Algebraic Data Type (ADT)

**Answer:**  
ADT is a combination of multiple types.

Example (Python-like):

```python
class Shape:
    pass
```

👉 Better example (write in exam):

- Circle, Rectangle
    

---

## ⭐ 4. ABC vs Type Class

**Answer:**

|ABC|Type Class|
|---|---|
|OOP concept|FP concept|
|Defines structure|Defines behavior|

---

## ⭐ 5. Strong Typing

**Answer:**  
Strong typing means strict type rules.

Example:

```python
"5" + 2  # error
```

---

## ⭐ 6. itertools Module

**Answer:**  
Module used for efficient iteration.

Functions:

- count()
    
- cycle()
    
- permutations()
    

---

## ⭐ 7. Pattern Matching

**Answer:**  
Matches data with patterns to simplify logic.

---

## ⭐ 8. Type Polymorphism

**Answer:**  
Ability of function to work with multiple types.

---

# 🎯 MOST EXPECTED SHORT QUESTIONS

From your QB:

- MapReduce ✅
    
- Strong typing ✅
    
- ADT ✅
    
- Type class ✅
    
- Pattern matching ✅
    

---

# 🔥 🔹 LONG ANSWERS (VERY IMPORTANT)

---

## ⭐ 1. Pure Functions

**Answer:**

A pure function:

- No side effects
    
- Same output for same input
    

Example:

```python
def add(a, b):
    return a + b
```

👉 No external dependency

---

## ⭐ 2. Map & Reduce (VERY VERY IMPORTANT)

**Answer:**

### Map:

```python
list(map(lambda x: x*2, [1,2,3]))
```

### Reduce:

```python
from functools import reduce
reduce(lambda x,y: x+y, [1,2,3])
```

👉 Write both examples = full marks

---

## ⭐ 3. Pattern Matching

**Answer:**

Pattern matching is used to check data structure patterns.

### Example:

```python
lst = [1,2,222,45,666,888]

result = [x for x in lst if 100 <= x <= 999]
```

Output:

```
[222, 666, 888]
```

---

## ⭐ 4. Type Classes & Ad-hoc Polymorphism

**Answer:**

Type classes allow same function to behave differently.

Example:

```python
def add(a, b):
    return a + b
```

👉 Works for int and string

---

## ⭐ 5. Recursion (VERY IMPORTANT)

**Answer:**

Recursion is when function calls itself.

Example:

```python
def fact(n):
    if n == 0:
        return 1
    return n * fact(n-1)
```

---

## ⭐ 6. Strong vs Weak Typing

**Answer:**

|Strong|Weak|
|---|---|
|Strict rules|Flexible|
|Less errors|More errors|

---

## ⭐ 7. Applicative vs Normal Order

**Answer:**

|Applicative|Normal|
|---|---|
|Evaluate arguments first|Evaluate when needed|
|Eager|Lazy|

---

# 🔥 🔹 CODING QUESTIONS (HIGH PRIORITY)

---

## ⭐ 1. Multiply Numbers (REPEATED)

```python
from functools import reduce

def multiply_numbers(lst):
    return reduce(lambda x, y: x*y, lst)
```

---

## ⭐ 2. Reverse List

```python
def reverse_list(lst):
    return lst[::-1]
```

---

## ⭐ 3. Even Numbers Filter

```python
def filter_even(lst):
    return list(filter(lambda x: x % 2 == 0, lst))
```

---

## ⭐ 4. Squares of Even Numbers

```python
[x*x for x in range(1,11) if x%2==0]
```

---

## ⭐ 5. Numbers divisible by 3

```python
[x for x in range(1,31) if x%3==0]
```

---

## ⭐ 6. Filter Countries (IMPORTANT)

```python
countries = ["India","China","Singapore","Indonesia","Italy"]

result = [c for c in countries if c.startswith("I")]
```

---

## ⭐ 7. Check String in List

```python
lst = ["apple","banana","cherry"]
s = "banana"

print(s in lst)
```

---

## ⭐ 8. Java Stream – Reverse Sort

```java
list.stream()
    .sorted(Comparator.reverseOrder())
    .forEach(System.out::println);
```

---

## ⭐ 9. Check Prime (Java Streams)

```java
list.stream()
    .anyMatch(n -> isPrime(n));
```

---

# 🚀 🔥 FINAL ANALYSIS (VERY IMPORTANT)

From PYQ + Question Bank:

### 🔥 MOST REPEATED TOPICS:

- MapReduce ✅
    
- Map/Reduce functions ✅
    
- Recursion ✅
    
- Pattern matching ✅
    
- Polymorphism ✅
    
- Typing (strong/weak) ✅
    

---

# ⚠️ REALITY CHECK

If you prepare ONLY:

- Map/Reduce
    
- Recursion
    
- Polymorphism
    
- Pattern matching
    

👉 You can score **40+/60 easily**

---
