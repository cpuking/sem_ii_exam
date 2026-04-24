# 📝 🧠 Functional Programming — MOCK TEST

**Time:** 30–40 mins  
**Marks:** 30

👉 Rule:

- Answer properly (like exam)
    
- Don’t skip explanations
    
- I will check strictly
    

---

# 🧩 SECTION A — Short Answers (2 × 5 = 10 marks)

👉 Answer **any 5 (but try all)**

### Q1. Define **map()** with example
map() is a function in python that applies a function to an iterable and returns a iterable
example 
``` python3
nums = [1,2,3,4]
print(list(map(lambda x : x * x, nums))
```

### Q2. What is **lazy evaluation**?
lazy evaluation is a technique in functional programming that delays the result  of the computation and returns only when it is needed
``` python3
def squares(n):
	for i in range(n):
		yield i * i
gen = squares(5)
print(next(gen))
```

### Q3. Define **pure function**
A pure function is a function which returns same output for same input and doesn't affect global/state variables
```python3
def add(a, b):
	return a + b
```

### Q4. What is **alpha reduction**?
Alpha reduction is a technique in lambda calculus where we simply rename the variables for better understanding

### Q5. What is **strong typing**?
strong typing in functional programming means a function will only take the input type it is meant to, strict type checking

### Q6. What is **currying**?
function currying is a technique in which we seperate a function with multiple parameter into functions with one parameter each, output of each function becomes input for other function

---

# 💻 SECTION B — Coding (10 marks)

### Q7. (5 marks)

Write a Python program to:

- filter even numbers
    ```python3
    nums = [1,2,3,4,5,6,7]
    res = list(filter(lambda x : x % 2 == 0, nums))
    print(res)
    ```
- square them
    ``` python3
    nums = [1,2,3,4,5,6,7]
    res = list(filter(lambda x : x * x, nums))
    print(res)
    ```
- find their sum
    ```python3
    from functools import reduce
    nums = [1,2,3,4,5,6,7]
    res = reduce(lambda x, y : x + y, nums)
    print(res)
    ```

👉 (Use functional programming)

---

### Q8. (5 marks)

Write a recursive function to find **factorial of a number**
```python3
def fact(n):
	if n == 0:
		return 1
	return n * fact(n-1)
```
- show trace for `n = 4`
    fact(4)
    4 * fact(3)
    4 * 3 * fact(2)
	4 * 3 * 2 * fact(1)
	4 * 3 * 2 * 1 * fact(0)
	4 * 3 * 2 * 1 * 1
	24 

---

# 🧠 SECTION C — Theory (10 marks)

### Q9. (5 marks)

Explain:  
👉 **map vs filter vs reduce**  
(with examples)
map() is a higher order function in python that applies a function to a iterable and returns an iterable 
example - map(lambda x : x * x, [1,2,3,4,5])
filter() is also a higher order function in python that takes a function as an input to select the items in the list as per the condition passed in a function
example  - filter(lambda x :  x % 2 == 0, [1,2,3,4,5])
while reduce() applies function cumulatively to elements and reduces them to single value
reduce is not built in python we need to import it from functools library for others we dont need to import them 
example - 
```python3 
from functools import reduce
nums = [1,2,3,4,5]
res = reduce(lambda x, y: x+y, nums)
print(res)
```

---

### Q10. (5 marks)

Explain:  
👉 **Recursion with example**
Recursion is a technique where function calls itself
it basically has to parts
1. Base case-  condition written to stop the execution of the recursion other we keep recursing through it until we get stack overflow error
2. Recursive case - smaller subproblems of the bigger problem basically function breaks down the input into smaller versions of it
```python3
def sum_of_list(lst):
	if not lst: #base case
		return 0
	return lst[0] + sum_of_list(lst[1:]) #Recursive case
```

---

# ⚠️ Instructions

👉 Write answers like exam (not just code)  
👉 Use definitions + examples  
👉 Be clear and structured

---

## 🚀 Start now

Answer **Section A first**.  
I’ll check and give feedback before moving ahead.