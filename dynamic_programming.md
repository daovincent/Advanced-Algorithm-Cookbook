# Introduction

Dynamic programming is a systematic approach to optimize recursive algorithms. Indeed some algorithms can be improved, think about Fibonacci for example you might want to remember an already calculated result. This is called memoization and it basically consists in recursion + caching your results. So remember : 

```
Memoization = recursion + caching
```

With also refer to this approach as the top-down approach, you will understand later why.

## Using memoization with Fibonacci

Let’s consider the Fibonacci sequence : U0 =  0, U1 = 1, Un+1 = Un - Un-1. We can code it this way :

```python
def fib(n: int) -> int:
    # Base cases
    if n == 0:
        return 0
    if n == 1:
        return 1
        
    # Recursive Calls
    return fib(n-1) + fib(n-2)
```
Here the resulting execution tree :

![FiboTree](/Images/Dynamic_programming/FiboTree.png)

As you can see we can avoid to repeat a lot of steps by caching them, let’s consider the following algorithm :

```python
def fib(n: int, memo: [int]) -> int:
    # Base cases
    if n == 0:
        return 0
    if n == 1:
        return 1
    
    # Check if sub-recursion was already computed
    if memo[n] != 0:
        return memo[n]
    
    # Solve sub-problem and cache it
    memo[n] = fib(n-1) + fib(n-2)
    return memo[n]
```

Let’s take again the tree above and see the step we spare :

![FiboTree](/Images/Dynamic_programming/FiboTreeLess.png)

We spared 16 steps out of 24 ! So ⅔ of them which is great. In this case this works great and is easy to understand. Also remember, no solution is perfect and they all have a cost. Here **we trade memory space for time efficiency**. 

To conclude on memoization you should remember :
 * **Memoization = recursion + caching** 
   * Essentially we cached all result in order not to compute them again 
   * So we trade memory for time efficiency, but we also spare resources and avoid potential stack overflows issues 
 * We talk about top-down approach because we optimize the top steps with the “bottom ones” (as shown with the tree) (I am not sure this why we call it that way, so tell me if I am wrong)
 * To implement naively this optimization follow these **4 steps** :
   1. **Find a problem that can be solved recursively**
   2. **Define the recursion**
   3. **Practice the problem, find repetitive pattern**
   4. **Cache this patterns**
