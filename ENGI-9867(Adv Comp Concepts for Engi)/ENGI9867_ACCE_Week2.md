## Formal Languages and Alphabet

#### Theorems

Let ∅ denote empty language; A,B,C,D denote di↵erent languages defined over the alphabet Σ.

1. A∅ = ∅A = ∅
2. A{λ} = {λ}A = A
3. (AB)C = A(BC)
4. (A $\subseteq$ B) ∧ (C $\subseteq$ D) ⇒ AC $\subseteq$ BD
5. A(B ∪ C) = AB ∪ AC
6. (B ∪ C)A = BA ∪ CA
7. A(B ∩ C) $\subseteq$ AB ∩ AC
8. (B ∩ C)A $\subseteq$ BA ∩ CA

#### Selected Proofs.

- A∅ = {xy | (x ∈ A) ∧ (y ∈ ∅)} doesn’t hold since ∀y, y ∉ ∅.  
Since there doesn’t exist any x,y couples satisfying the condition A∅ = ∅

- (A $\subseteq$ B) ∧ (C $\subseteq$ D) ⇒ AC $\subseteq$ BD  
We are going to use a direct proof. We assume  
(A $\subseteq$ B) ∧ (C $\subseteq$ D) and z ∈ AC  
z = xy ⇔ x ∈ A ∧ y ∈ C  
((A $\subseteq$ B) ∧ (x ∈ A) ⇒ (x ∈ B)) ∧ ((C $\subseteq$ D) ∧ (y ∈ C) ⇒ y ∈ D)  
((x ∈ B) ∧ (y ∈ D)) ⇒ xy ∈ BD  
(xy ∈ AC ⇒ xy ∈ BD) ⇔ AC $\subseteq$ BD

- A(B ∩ C) $\subseteq$ AB ∩ AC  
∀z[z ∈ A(B ∩ C)] ⇔ ∃x,y[(z = xy) ∧ (x ∈ A) ∧ (y ∈ B ∩ C)]  
(x ∈ A) ∧ (y ∈ B ∩ C)  
⇔ (x ∈ A) ∧ (y ∈ B) ∧ (y ∈ C)  
⇔ (x ∈ A) ∧ (y ∈ B) ∧ (x ∈ A) ∧ (y ∈ C)  
⇔ (xy ∈ AB) ∧ (xy ∈ AC)  
⇔ (xy ∈ AB ∩ AC)  
∀z[z ∈ A(B ∩ C) ⇒ z ∈ AB ∩ AC]  

- AB ∩ AC $\subseteq$ A(B ∩ C) ❌  
∀z[z ∈ AB ∩ AC ⇔ z ∈ AB ∩ z ∈ AC]  
z ∈ AB ⇔ ∃$x_1,y_1$[(z = $x_1y_1$) ∧ ($x_1$ ∈ A) ∧ ($y_1$ ∈ B)]  
z ∈ AC ⇔ ∃$x_2,y_2$[(z = $x_2y_2$) ∧ ($x_2$ ∈ A) ∧ ($y_2$ ∈ C)]  
($x_1$ = $x_2$) ∧ ($y_1$ = $y_2$) ❌

- Let’s give a counter example to show that AB ∩ AC $\not\subseteq$ A(B ∩ C)  
A = {$a^n$ | n ∈ N}  
B = {$a^nb^n$ | n ∈ N}  
C = {$b^n$ | n ∈ N}  
Let’s take z = $a^5b^2$.  
z = $a^3a^2b^2$  
z ∈ AB ∩ AC  
However B ∩ C = {λ} therefore  
z ∉ A(B ∩ C).

#### $A^n$ : Let language A be defined over Σ
1. $A^0$ = {λ}
2. $A^{n+1}$ = $A^nA^1$;∀n ∈ N  

For example:  
Σ = {a,b}  
A = {λ,a,b}  
$A^1$ = A  
$A^2$ = {λ,a,b,aa,ab,ba,bb}  

#### Theorems

Let A and B denote di↵erent languages defined over the alphabet Σ.
1. $A^mA^n$ = $A^{m+n}$
2. $(A^m)^n$ = $A^{mn}$
3. A $\subseteq$ B ⇒ $A^n$ $\subseteq$ $B^n$ ...

#### Proof.
1. $A^mA^n$ = $A^{m+n}$  
We are going to use induction.  
For the base case, we use the previous definition: n = 1: $A^mA^1$ = $A^{m+1}$  
Inductive step: $A^mA^{n+1}$ = $A^mA^nA^1$  
Concat op. is associative: $A^m(A^nA^1)$ = $(A^mA^n)A^1$ = $A^{m+n}A^1$ = $A^{m+n+1}$

2. $(A^m)^n$ = $A^{mn}$  
We are going to use induction.  
For the base case n = 1: $A^m$ = $A^m$  
Inductive step: $(A^m)^{n+1}$ = $(A^m)^n(A^m)^1$ = $A^{mn+m}$ = $A^{m(n+1)}$

3. A $\subseteq$ B ⇒ $A^n$ $\subseteq$ $B^n$ ...  
Let’s remember $A^2$ = A × A, $B^2$ = B × B and A $\subseteq$ B ⇒ (∀x(x ∈ A → x ∈ B))  
For n = 2:  
$A^2$ = {xy | x ∈ A ∧ y ∈ A}  
A $\subseteq$ B ⇒ (x ∈ A → x ∈ B)  
A $\subseteq$ B ⇒ (y ∈ A → y ∈ B)  
(∀xy(xy ∈ $A^2$ → xy ∈ $B^2$)) ⇒ $A^2$ $\subseteq$ $B^2$  
Proof continues similarly for n := n +1

## Star closure (Kleene Star, Kleen Closure)

#### Positive Closure

$A^+$: $∪_{n=1}A^n$ = $A^1$ ∪ $A^2$ ∪ $A^3$ ...

#### Star Closure

$A^{\ast}$: $∪_{n=0}A^n$ = $A^0$ ∪ $A^1$ ∪ $A^2$ ∪ $A^3$ ...

#### Theorems

Let A and B denote di↵erent languages defined over the alphabet Σ and let n ∈ N.
1. $A^{\ast}$ = {λ} ∪ $A^+$. Derived from the definition
2. $A^n$ $\subseteq$ $A^{\ast}$, n ≥ 0. Derived from the definition
3. $A^n$ $\subseteq$ $A^+$, n ≥ 1. Derived from the definition
4. A $\subseteq$ $AB^{\ast}$ Proof tip: $A^0$ $\subseteq$ $B^{\ast}$ ⇒ A $\subseteq$ $AB^{\ast}$
5. A $\subseteq$ $B^{\ast}A$
6. A $\subseteq$ B ⇒ $A^{\ast}$ $\subseteq$ $B^{\ast}$. Can be proven by using A $\subseteq$ B ⇒ $A^n$ $\subseteq$ $B^n$. Once true for all n, then
it is true for union of all n.
7. A $\subseteq$ B ⇒ $A^+$ $\subseteq$ $B^+$
8. $AA^{\ast}$ = $A^{\ast}A$ = $A^+$
9. λ ∈ A ⇔ $A^+$ = $A^{\ast}$
10. $(A^{\ast})^{\ast}$ = $A^{\ast}A^{\ast}$ = $A^{\ast}$
11. $(A^{\ast})^+$ = $(A^+)^{\ast}$ = $A^{\ast}$
12. $A^{\ast}A^+$ = $A^+A^{\ast}$ = $A^+$ 
13. $(A^{\ast}B^{\ast})^{\ast}$ = $(A ∪ B)^{\ast}$ = $(A^{\ast} ∪ B^{\ast})^{\ast}$