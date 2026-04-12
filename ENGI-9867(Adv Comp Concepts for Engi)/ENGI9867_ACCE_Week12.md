# Computational Complexity Theory:
- How Fast is My Algorithm? 
- From Big-O to the Edge of Feasibility

## The Engineer's Question(s)

You've written an algorithm. Now what?
- Will it finish in a second? An hour? A year?!
- Will it work when my dataset doubles? Triples? Goes from 1,000 to 1,000,000 points?

We need:
- A language to talk about efficiency, independent of hardware or coding tricks.
  - Learn how to mathematically describe and compare the efficiency of different algorithms.
- A mathematical notation used to classify the rate of growth of operations as the input size (n) increases, providing a theoretical framework to evaluate how an algorithm scales.
  - Direct time measurement is unreliable (depends on CPU, load, etc.).

## I. The Big-O Notation (Asymptotic Upper Bound)

In the Worst Case... (The Upper Bound)
- Definition: $f(n) = O(g(n))$ if there exist constants c and $n_0$ such that $0 ≤ f(n) ≤ c*g(n)$ for all $n ≥ n_0$.

Example: $f(n) = 2n + 10$ is $O(n)$ because for $c=3, n_0=10, 2n+10 ≤ 3n$ for all $n≥10$.  
→ other values, $c=4, n₀=1 , c=2.5, n_0 = 20$ → condition requires existence

- **Interpretation:** "f grows no faster than g." It's the **upper bound** on the growth rate.
- **Engineering View:** This is our guarantee. The algorithm will not be slower than this.
- We focus on the **dominant term** (the fastest growing part) and ignore constant factors.
  - Example: $3n^2+5n+10$ is simplified to $O(n^2)$.

## $O(1)$ - Constant Time

- **Definition:** The number of operations is fixed and does not change with input size (n).
- **Speed:** The fastest possible time complexity.
- **Examples:**
  - Array/List index access (my_list[5]), 
  - Dictionary/Set key lookup (average case).

## $O(logn)$ - Logarithmic Time

- Definition: The time required increases slowly as the input size increases exponentially.
- The algorithm typically cuts the problem size in half with each step.
- **Speed:** Extremely fast, highly scalable. 
- **Example:** Searching for an element in a **Binary Search Tree** 
(BST) or using **Binary Search** on a sorted array/list.

## $O(n)$ - Linear Time

- **Definition:** The time taken grows directly proportional to the 
input size (n). If the input doubles, the runtime doubles.
- **Speed:** Good performance, common for single-pass algorithms.
- **Examples:** Iterating every element in a list, searching an unsorted 
list, insertion/deletion at the start of a Python list.

## $O(nlogn)$ - Linearithmic Time

- **Definition:** Slightly slower than linear time, typically involving a 
loop (O(n)) that executes a logarithmic operation (O(logn)).
- **Speed:** Very efficient for large-scale processing.
- **Examples:** Most efficient **sorting algorithms** like Merge Sort and Heap Sort.

## $O(n^2)$ - Quadratic Time

- **Definition:** The time taken grows proportional to the square of the input size (n).
- **Cause:** Usually involves **nested loops** over the same input.
- **Speed:** Avoid for large datasets; performance degrades rapidly.
- **Example:** Simple, brute-force sorting algorithms like **Bubble Sort**.

# $O(2^n)$ - Exponential Time

- Definition: The time required doubles with every single added element.
- Speed: The slowest complexity; only feasible for tiny inputs.
- Example: Algorithms that check every possible subset or combination, 
such as brute-force solution to the Traveling Salesperson Problem.

## The Big-O Family Portrait: Hierarchy of Complexity

| Notation    | Name         | Growth Rate  |
|-------------|--------------|--------------|
| O(1)        | Constant     | Fastest      |
| O(logn)     | Logarithmic  | Very Fast    |
| O(n)        | Linear       | Good         |
| O(nlogn)    | Linearithmic | Decent       |
| O(n2)       | O(2n)        | Quadratic    |
| Exponential | Slow         | Slowest      |

## II. The Big-Ω Notation (Asymptotic Lower Bound)

In the Best Case... (The Lower Bound)

- Definition: $f(n) = Ω(g(n))$ if there exist constants c and $n_0$ such that $0 ≤ c * g(n) ≤ f(n)$ for all $n ≥ n_0$.
- Check the values $c=1$ and $n_0=1$ for the previous example!
- **Interpretation:** "f grows at least as fast as g." It's the lower bound on the growth rate.
- **Engineering View:** The best-case scenario. Useful but often not as critical as the guarantee.

Note: There are infinitely many valid upper and lower bounds for any given function.

## III. The Big-Θ Notation (Asymptotic Tight Bound)

The Sweet Spot (The Tight Bound)

- **Definition:** $f(n) = Θ(g(n)) \text{ if } f(n) = O(g(n)) \text{ and } f(n) = Ω(g(n))$.
- **Interpretation:** "f grows exactly like g (within constant factors)."
- **Engineering View:** This is the most informative notation. 
It tells us the algorithm's behavior is tightly bounded by g(n) for all but the smallest inputs.
  - Example: Mergesort is $Θ(nlogn)$.

| Notation      | Tells Us                                                               | Example (Mergesort)                         |
|---------------|------------------------------------------------------------------------|---------------------------------------------|
| O (Big-O)     | Upper bound — algorithm won't be worse than this                       | Mergesort is $O(n^2)$ (true, but not tight) |
| Ω (Big-Omega) | Lower bound — algorithm won't be better than this                      | Mergesort is $Ω(𝑛)$ (true, but not tight)   |
| Θ (Theta)     | Tight bound — algorithm's growth is exactly this<br>(within constants) | Mergesort is $Θ(nlogn)$                     |

## Example: Analyzing a Simple Loop

Putting it All Together

```python
def find_max(arr):
  max_val = arr[0]        # O(1)    
  for num in arr:         # loop runs n times  
    if num > max_val:     # O(1)
      max_val = num       # O(1)
  return max_val          # O(1)
```

- Analysis:
  - Best case: $Ω(n)$ (still have to check every element)
  - Worst case: $O(n)$
  - Therefore: $Θ(n)$

## Complexity of Algorithms

Moving from Code to Analysis

- Time Complexity: Number of elementary operations (comparisons, assignments, etc.) as a function of input size.
- Space Complexity: Amount of memory used as a function of input size.
  - O(1) Space: Algorithms that sort "in place" (like Heap Sort), requiring only a few temporary variables.
  - O(n) Space: Algorithms that must create a copy of the input or use another data structure proportional to the input size (like Merge Sort).

## Time-Space Trade-off

- **Principle:** Algorithms often achieve faster time complexity by using more memory, or vice versa.
- **Example (Memorization):** Storing the results of expensive function calls (using a Dictionary/Hash Map) 
costs $O(n)$ space but reduces future calls to $O(1)$ time.
- The choice of data structure is fundamentally about balancing time complexity, space complexity, 
and how that structure interacts with your computer's memory architecture.
- **Question:** Given the trade-offs, why would a developer ever choose an O(n2) Bubble Sort algorithm over a more efficient O(nlogn) Merge Sort? 
  - (Hint: Think about code simplicity and small datasets).

