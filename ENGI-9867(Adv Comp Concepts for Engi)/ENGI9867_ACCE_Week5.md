# Practice Session

## Example#5

Consider the following grammar:  
S → aA  
A → bbA | c

**(a)** Which type does this grammar correspond to in Chomsky hierarchy? Why?  
**(b)** Heuristically give the regular expression for the language of this grammar.  
**(c)** Heuristically give an equivalent grammar which correspond to a one level less restrictive Chomsky type.  
**(d)** Draw the NFA/DFA for the regular expression in (b).

#### Answer

**(a)** Type-3. because all its productions are of the right-linear form:  
A → σB, A → σ  
A,B ∈ N, σ ∈ $Σ^+$  
**(b)** a(bb)*c  
**(c)** Type-2. Let a nonterminal appears in the middle (of the production).
S → aBc  
B → bbB | λ  
**(d)** DFA:  
$(q_0, a) → q_1$  
$(q_1, b) → q_2$  
$(q_2, b) → q_1$  
$(q_1, c) → q_3$  
start: $q_0$  
final: $q_3$

##　Example#6

Consider the following BNF grammars that belong to the languages $L_1$ and $L_2$ respectively  

$L_1$:  
$\langle S \rangle$ ::= $\langle A \rangle \langle B \rangle$  
$\langle A \rangle$ ::= $aa \langle A \rangle b$ | aab  
$\langle B \rangle$ ::= $b \langle B \rangle cc$ | bcc  

$L_2$:  
$\langle S \rangle$ ::= $a \langle S \rangle c$ | $a \langle B \rangle c$  
$\langle B \rangle$ ::= $b \langle B \rangle b$ | bb  


Provide a shortest word from the following sets (answer might be ∅)
- $L_1 ∪ L_2$
- $L_1 ∩ L_2$
- $L_1 - L_2$
- $L_2 - L_1$

#### Answer
- $L_1 ∪ L_2$:   
(1) for $L_1$:  
let A = aab  
let B = bcc  
Shortest word: aabbcc  
(2) for $L_2$:  
let B = bb  
let S = aBc = abbc  
Shortest word: abbc  
(3) for $L_1 ∪ L_2$: abbc

- $L_1 ∩ L_2$  
(1) for $L_1$:  
A ⇒ $a^{2n}b^n$ (n > 0)  
B ⇒ $b^mc^{2m}$ (m > 0)   
$L_1$: $a^{2n}b^{n+m}c^{2m}$ (m,n > 0)  
(2) for $L_2$:  
B ⇒ $b^{2p}$ (p > 0)  
S ⇒ $a^qb^{2p}c^q$ (p,q > 0)  
let 2n = q, n + m = 2p, 2m = q  
Thus: m = n = p = 1/2q  
let q = 2, so m = n = p = 1  
Shortest word: aabbcc

- $L_1 - L_2$ (i.e. strings that are in $L_1$ but not in $L_2$)  
$L_1$: $a^{2n}b^{n+m}c^{2m}$ (m,n > 0)  
$L_2$: $a^qb^{2p}c^q$ (p,q > 0)  
let m = 1, n = 1, $L_1$ accepts aabbcc, but it is in $L_2$.
let m = 1, n = 2, $L_1$ accepts aaaabbbcc, it is not in $L_2$, length = 9  
let m = 2, n = 1, $L_1$ accepts aabbbcccc, it is not in $L_2$, length = 9  
So shortest word: aaaabbbcc or aabbbcccc

- $L_2 - L_1$ (i.e. strings that are in $L_2$ but not in $L_1$)  
$L_1$: $a^{2n}b^{n+m}c^{2m}$ (m,n > 0)  
$L_2$: $a^qb^{2p}c^q$ (p,q > 0)  
let p = 1, q = 1, $L_2$ accepts abbc, it is not in $L_1$.
So shortest word: abbc

# Recognizing Regular Expressions and Regular Language’s Properties

## Systematic way to find the regular language recognized by a DFA

Remember the theorem that states the one and only solution to the equation

X = AX ∪ B ∧ λ ∉ A.  