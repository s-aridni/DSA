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

| Notation | Name | Example |
|----------|------|---------|
| O(1) | Constant | HashMap lookup |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Loop through array |
| O(n log n) | Linearithmic | Merge sort, Quick sort (avg) |
| O(n²) | Quadratic | Nested loops (bubble sort) |
| O(2ⁿ) | Exponential | Recursive Fibonacci (naive) |
| O(n!) | Factorial | Generating all permutations |
