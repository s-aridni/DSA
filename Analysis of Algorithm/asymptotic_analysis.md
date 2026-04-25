> Asymptotic analysis tells us how an algorithm **scales** -- not how fast it
> runs on your machine today, but how it **behaves as the problem gets bigger**.

## Why Should We Analyze an Algorithm?

There can be multiple algorithms to solve the same problem. We need a way to
determine which one is better.

**Example:** Find an element in a list of 1 million items.

- **Linear Search** -- check one by one → 1,000,000 steps worst case
- **Binary Search** (sorted list) -- halve each time → ~20 steps worst case

Both solve the problem. Analysis tells us Binary Search is massively better here.

### What do we measure?

- **Time** -- how many operations does it take?
- **Space** -- how much extra memory does it need?

### Why not just measure actual execution time?

Because actual time depends on:

- Hardware (fast laptop vs slow server)
- Programming language (C vs Python)
- Other processes running on the machine
- Input data (lucky vs unlucky order)

We need a way to compare algorithms that is **independent of machine, language,
and environment**. That's where asymptotic analysis comes in.

---

## What is Asymptotic Analysis?

Asymptotic analysis measures how an algorithm's **time or space grows** as the
**input size (n) increases toward infinity**.

It doesn't care about:
- Exact number of seconds
- Constants (`2n` vs `5n` -- both are just `n`)
- Lower-order terms (`n² + 100n` -- just `n²`)

It cares about: **the growth rate**.

**Example:**

| Algorithm | Operations for n=10 | Operations for n=1,000,000 | Growth Rate |
|-----------|---------------------|---------------------------|-------------|
| Algorithm A | 2n = 20 | 2,000,000 | O(n) |
| Algorithm B | n² = 100 | 1,000,000,000,000 | O(n²) |

At small n, the difference is minor. At large n, O(n²) becomes unusable.
Asymptotic analysis reveals this.

---

## What Are the Common Analyses We Do?

### The Three Common Notations

- **Big O (O)** -- worst case
  - "It will **never** be slower than this"
  - Most commonly used in interviews
  - Example: Linear search is `O(n)`

- **Big Omega (Ω)** -- best case
  - "It will **never** be faster than this"
  - Example: Linear search is `Ω(1)` -- element is at the first position

- **Big Theta (Θ)** -- tight bound / average case
  - "It grows **exactly** at this rate"
  - Example: Merge sort is `Θ(n log n)` -- always, regardless of input

### Common Growth Rates (slowest to fastest)
O(1) < O(log n) < O(sqrt(n)) < O(n) < O(n log n) < O(n²) < (2ⁿ) < O(n!)

<img width="1065" height="700" alt="image" src="https://github.com/user-attachments/assets/ade82127-4d3f-4824-a38c-093aaf1698c9" />


| Notation | Name | Example |
|----------|------|---------|
| O(1) | Constant | HashMap lookup |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Loop through array |
| O(n log n) | Linearithmic | Merge sort, Quick sort (avg) |
| O(n²) | Quadratic | Nested loops (bubble sort) |
| O(2ⁿ) | Exponential | Recursive Fibonacci (naive) |
| O(n!) | Factorial | Generating all permutations |


---

## Pattern to Identify Each Complexity
### O(1) -- Constant
- The operation doesn't depend on input size at all
- Direct access, no loops, no recursion
- **Pattern:** Single operation regardless of `n`
- **Examples:** Array access by index, HashMap get/put, push/pop on stack
---
### O(log n) -- Logarithmic
- The problem size gets **halved** (or divided) in each step
- You're **eliminating** a portion of the data each iteration, not scanning all of it
- **Pattern:** "How many times can I divide `n` by 2 until I reach 1?"
- **Examples:** Binary search, balanced BST lookup, exponentiation by squaring
      n = 16 → 8 → 4 → 2 → 1  (4 steps = log₂16)
---
### O(√n) -- Square Root
- You only need to check up to the **square root of n**, not all of `n`
- **Pattern:** "If I find nothing up to √n, I can stop"
- **Examples:** Checking if a number is prime (only check divisors up to √n), finding factors
      n = 100 → check 1 to 10 only (√100 = 10)
---
### O(n) -- Linear
- You touch **every element once**
- One loop through the data
- **Pattern:** Single `for` loop from 0 to n
- **Examples:** Linear search, find max/min, sum of array
      for (int i = 0; i < n; i++) { ... }
---
### O(n log n) -- Linearithmic
- You do **n work** at **each level**, and there are **log n levels**
- **Pattern:** Dividing the problem into halves (log n), but processing all elements at each level (n)
- Alternatively: sorting, then doing something linear
- **Examples:** Merge sort, Quick sort (average), heap sort
      Level 1:  [n elements]                → n work
      Level 2:  [n/2] [n/2]                 → n work
      Level 3:  [n/4] [n/4] [n/4] [n/4]     → n work
      ...
      log n levels × n work each = O(n log n)
---
### O(n²) -- Quadratic
- **Nested loops** -- for every element, you loop through all elements again
- **Pattern:** Two nested `for` loops, each going up to n
- **Examples:** Bubble sort, selection sort, comparing all pairs, brute force two-sum
      for (int i = 0; i < n; i++) {
          for (int j = 0; j < n; j++) { ... }
      }
---
### O(2ⁿ) -- Exponential
- At each step, you make **two choices** (include or exclude, left or right)
- The problem **branches into two subproblems** at every step, and both are solved
- **Pattern:** Recursive function that calls itself **twice** without eliminating work
- **Examples:** Naive recursive Fibonacci, generating all subsets, backtracking without pruning
      f(n) = f(n-1) + f(n-2)
                    f(5)
                  /      \
               f(4)      f(3)
              /    \    /    \
            f(3) f(2) f(2) f(1)
            ...   ...
---
### O(n!) -- Factorial
- You're generating **all possible orderings** (permutations) of n items
- First position has n choices, second has n-1, third has n-2...
- **Pattern:** "Arrange all elements in every possible order"
- **Examples:** Generating all permutations, brute force travelling salesman
      n = 4  → 4 × 3 × 2 × 1 = 24 permutations
      n = 10 → 3,628,800 permutations
      n = 20 → 2,432,902,008,176,640,000 (impossible)
---
## Quick Cheat Sheet
| Complexity | Pattern | Ask Yourself |
|------------|---------|--------------|
| O(1) | Direct access | "Am I doing one thing regardless of n?" |
| O(log n) | Halving each step | "Am I cutting the problem in half each time?" |
| O(√n) | Check up to square root | "Can I stop at √n?" |
| O(n) | Single loop | "Am I touching each element once?" |
| O(n log n) | Divide + process all | "Am I sorting or dividing into halves and merging?" |
| O(n²) | Nested loops | "Do I have a loop inside a loop?" |
| O(2ⁿ) | Two choices per step | "Am I branching into two recursive calls each time?" |
| O(n!) | All orderings | "Am I generating every permutation?" |
