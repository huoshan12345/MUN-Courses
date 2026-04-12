# Computational Complexity Theory:
- From Algorithm to Problem

## Merge Sort Algorithm

- **Merge sort** is a popular sorting algorithm known for its efficiency and stability. 
- It follows the Divide and Conquer approach.
- The algorithm follows three main steps:
  1. Divide: Split the array into two halves until each subarray contains only one element
  2. Conquer: Recursively sort each subarray
  3. Merge: Combine sorted subarrays while maintaining order.

- Time Complexity:
  - Best Case: $Ω(n log n)$, when the array is already sorted or nearly sorted.
  - Average Case: $Θ(n log n)$, when the array is randomly ordered.
  - Worst Case: $O(n log n)$, when the array is sorted in reverse order.

- Auxiliary Space:
  - $O(n)$, additional space is required for the temporary array used during merging.

## A Crucial Shift in Perspective

- In last lecture, we've been analyzing algorithms.
- Now, let's think about the problem itself.
- **Question:** What is the inherent difficulty of a problem, independent of the algorithm we use to solve it?
- Example: Sorting a list of n numbers.
  - We have $O(n log n)$ algorithms (e.g., Mergesort).
  - Is it possible to have an O(n) sorting algorithm? (No, not for comparison-based sorting).

## Complexity of Problems: Upper Bounds

The Upper Bound: "We Can Do This Well"

- **Definition:** An **upper bound** for a problem is the complexity of the best known algorithm that solves it.
- **Engineering View:** The upper bound is a guarantee of feasibility. "We have a solution that runs in $O(f(n))$."
- *Example (Sorting):* Upper bound is $O(n log n)$

## Complexity of Problems: Lower Bounds

The Lower Bound: "No Algorithm Can Do Better"

- **Definition:** A **lower bound** for a problem is a proof that no algorithm 
(current or future) can solve it faster than $Ω(g(n))$.
- Example (Comparison-based Sorting): The lower bound is $Ω(n log n)$.  
Any algorithm that sorts by comparing elements must take at least this long.

## Algorithms vs. Problems

- Upper and lower bounds in algorithms describe performance;   
in problems, they describe inherent difficulty.

| Focus     | Upper Bound (O)                                     | Lower Bound (Ω)                                                 |
|-----------|-----------------------------------------------------|-----------------------------------------------------------------|
| Algorithm | Worst Case: "It won't get slower than this."        | Best Case: "It won't get faster than this."                     |
| Problem   | Feasibility: "We have already achieved this speed." | Impossibility: "It is mathematically impossible to go faster."  |

## Putting It Together: The "Optimal" Algorithm

When Upper Bound = Lower Bound

- An algorithm is **optimal** if its worst-case complexity (the upper bound for the problem) 
matches the known lower bound for the problem.
- *Example (Comparison-based Sorting):*
  - Lower bound: $Ω(n log n)$
  - Upper bound (Mergesort): $O(n log n)$
  - Therefore, Mergesort is an optimal algorithm.
- **Key Question:** For many problems, our upper and lower bounds do not match. This gap represents our ignorance.

## The Central Question of Complexity Theory

The $1,000,000 Question: P vs. NP

- P (Polynomial Time): Problems that can be solved quickly (in polynomial time) 
by a deterministic computer. (e.g., sorting, shortest path, matrix multiplication).
- NP (Nondeterministic Polynomial Time): Problems whose solutions can be verified quickly (in polynomial time). 
(e.g., a Sudoku solution, a factoring of a large number, a Hamiltonian path).
- **The Question:** Is P = NP? Can every problem whose solution can be verified quickly also be solved quickly?

## P vs. NP: The Engineering Consequence

Why You (as an Engineer) Should Care

- If $P = NP$: For every problem we can check a solution for (like finding the optimal layout for a circuit or the best schedule for a factory), 
there exists a fast algorithm to find that solution. A revolution in optimization, AI, logistics.
- If $P ≠ NP$ (widely believed): There exists a class of problems for which we can never find fast, exact algorithms. 
We must use heuristics, approximations, or accept exponential time for exact solutions.

The consensus is that $P ≠ NP$.

## The Frontier of Hard Problems

Welcome to the Hardest Problems in NP

- If $P ≠ NP$, then there is a set of problems within NP that are the *most difficult*.
- These are the NP-complete problems.
- They are all "equivalently hard." If you find a polynomial-time algorithm for one NP-complete problem, 
you have solved every NP-complete problem (proving $P=NP$).

## The Traveling Salesman Problem (TSP)

A Classic NP-Complete Problem

- Problem: Given a list of cities and the distances between each pair, 
find the shortest possible route that visits each city exactly once and returns to the origin city.
- Why it's Hard:
  - Brute-force: $(n-1)! / 2$ possibilities.
  - For 60 cities, that's more than the number of atoms in the observable universe.
  - No known polynomial-time algorithm.

## The Satisfiability Problem (SAT)

The "Grandfather" of NP-Completeness!

- **Problem:** Given a Boolean formula, is there an assignment of TRUE/FALSE values to the variables that makes the entire formula TRUE?
- *Example:* (x₁ OR x₂) AND (NOT x₁ OR x₂)
- **Significance:** The first problem proven to be NP-complete (Cook-Levin Theorem, 1971). 
Every NP-complete problem can be reduced to SAT.

## The Engineering Dilemma

So What Do I Do With a Hard Problem

- If your problem is NP-complete, a fast, exact, and optimal algorithm is almost certainly impossible (assuming $P ≠ NP$).
- Your options as an engineer:
  1. Brute-force: Accept exponential time for small problem instances (n < 30-50).
  2. Heuristics & Approximations: Find "good enough" solutions quickly (e.g., genetic algorithms, simulated annealing, greedy approaches).
  3. Exploit Problem Structure: Is your instance a special case? (e.g., TSP on a grid might be easier).
  4. Use Parameterized Algorithms: Find an algorithm exponential in a small parameter, but polynomial in the overall size (e.g., $O(2^k * n)$).
