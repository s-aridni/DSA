> DSA is about solving problems using the right data structure and the right algorithm to minimize computational resources (time and space).

---

## What is a Data Structure?

A data structure is a way of organizing, storing, and managing data so that
it can be accessed and modified efficiently.

- **Data** is the "stuff"
- **Data structure** is the "container" that determines how you store, find,
  and manipulate that stuff

### Why Do We Need Data Structures?

Different problems need different ways of organizing data.
The choice of data structure affects:

- **Speed** -- how fast you can search, insert, delete
- **Memory** -- how much space it uses

### Quick Example

Suppose you need to check if a username already exists among 1 million users:

- Array: scan all 1M entries → O(n) → slow
- Sorted Array + Binary Search: O(log n) → faster
- Hash Set: O(1) average → fastest

---

## What is an Algorithm?

An algorithm is a step-by-step set of instructions to solve a specific problem.
It takes an **input**, follows a defined set of steps, and produces an **output**.

### Algorithm vs Data Structure

| | Data Structure | Algorithm |
|---|---|---|
| **What** | How data is organized | How a problem is solved |
| **Analogy** | A bookshelf | The method to find a book on it |
| **Example** | Array, HashMap, Tree | Binary Search, BFS, Sorting |


They work together -- choosing the right data structure often makes the
algorithm faster. For example, searching in an unsorted array is O(n), but
searching in a HashMap is O(1).




**NOTE:**
- Explanation should be concise and clear. With example if possible
- Understanding the pattern is the key
