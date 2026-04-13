#  Complexity of algorithms and problems

## Question 1 – Asymptotic Notation (20 points) 

For each pair of functions, state whether $f(n) = O(g(n)),\ f(n) = Ω(g(n)),\ f(n) = Θ(g(n))$, or none of these. Briefly justify. 

(a) $f(n) = n^2 + 100n,\quad g(n) = n^2$ &emsp;(10 points)  
(b) $f(n) = 2^n,\quad g(n) = 3^n$ &emsp;&emsp;&emsp;&emsp;&emsp;(10 points)

## Question 2 – Analyzing Algorithm Complexity (35 points)

Consider the following algorithm (pseudocode): 

```
function mysterious(A[1..n]) 
  if n <= 1 return A[1] 
  mid = floor(n/2) 
  L = mysterious(A[1..mid]) 
  R = mysterious(A[mid+1..n]) 
  i = 1; j = 1; k = 1 
  while k <= n: 
    if i <= mid and (j > n-mid or L[i] <= R[j]): 
      A[k] = L[i]; i = i+1 
    else: 
      A[k] = R[j]; j = j+1 
    k = k+1 
  return A
```

(a) What does this algorithm compute? (5 points)  
(b) Derive a recurrence relation for its running time $T(n)$. (10 points)   
(c) Solve the recurrence using the Master Theorem or iteration, giving a tight asymptotic bound in $Θ(·)$. (10 points)   
(d) State the **space complexity** (extra memory) of this algorithm in $Θ(·)$ notation. (10 points)   

## Question 3 – Lower Bounds & Problem Complexity (20 points)

(a) Explain the difference between an upper bound and a lower bound for a computational problem. (10 points) 
(b) The comparison-based sorting problem has a known lower bound of $Ω(n log n)$. Mergesort runs in $O(n log n)$. What can you conclude about Mergesort’s optimality? (10 points) 

## Question 4 – The Classes P and NP (25 points)

(a) Give one example of a problem in P and one example of a problem in NP that is **not known** to be in P (other than SAT). (10 points)  
(b) What is the practical consequence for an engineer if $P = NP$? What if $P ≠ NP$? (15 points)