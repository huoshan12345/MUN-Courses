## Master Theorem

#### T(n) = a * T(n/b) + f(n)

(1) rewrite $f(n) = n^c({\log n})^k$

|f(n)          |rewrite             | k and c      |
|--------------|--------------------|--------------|
| n            | $n^1$              | c = 1, k = 0 |
| $n^2$        | $n^2$              | c = 2, k = 0 |
| $n {\log n}$ | $n^1 ({\log n})^1$ | c = 1, k = 1 |
| 1            | $n^0$              | c = 0, k = 0 |

(2) compute $c_{crit} = {\log_ba}$  
(3) compare $c_{crit}$ and c  
case 1: $c_{crit}$ > c, then $T(n) = Θ(n^{c_{crit}})$  
case 2: $c_{crit}$ = c, then $T(n) = Θ(n^{c_{crit}}({\log n})^{k+1})$  
case 3: $c_{crit}$ < c, then $T(n) = Θ(f(n)) = Θ(n^c({\log n})^k)$  

