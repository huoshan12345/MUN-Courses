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
$X = XA ∪ B ∧ λ ∉ A$ is $X = BA^{\ast}$  
Let’s rewrite the statement using regular expressions:  
$x = xa ∨ b ∧ λ ≠ a ⇒ x = ba^{\ast}$  
We shall use this theorem in finding the regular language recognized by a DFA

## Example

$q_1 = q_1x ∨ q_2x ∨ q_3x ∨ λ$  
$q_2 = q_1y$  
$q_3 = q_2y ∨ q_3y$  

We can use the theorem for $q_3$  
$(q_3) = (q_3)y ∨ q_2y$ then we have $q_3 = q_2yy^{\ast} ⇒ q_3 = q_1yy^+$   
Using this equality:  
$q_1 = q_1x ∨ q_1yx ∨ q_1yy^+x ∨ λ$  
$q_1 = q_1(x ∨ yx ∨ yy^+x) ∨ λ$  
$q_1 = (x ∨ yx ∨ yy^+x)^{\ast} = (y^{\ast}x)^{\ast}$  
$q_3 = (y^{\ast}x)^{\ast}yy^+$

The example automaton is actually the DFA equivalent of the NFA given in the previous examples. Heuristically we have found $(x ∨ y)^{\ast}yy^+$ as the language of the NFA. Let’s show
that these two are equivalent.

##　Proof of Example#1
We need to show　$(y^{\ast}x)^{\ast}yy^+ = (x ∨ y)^{\ast}yy^+$

Try 1  
(a) Draw the DFA of $(x ∨ y)^{\ast}$ and NFA of $(y^{\ast}x)^{\ast}$  
(b) Transform the NFA to DFA  
(c) FAIL!!!

Try 2  
(a) Draw the NFA of $(y^{\ast}x)^{\ast}yy^+$ and NFA of $(x ∨ y)^{\ast}yy^+$  
(b) Transform each NFA to DFA  
(c) Wait... but how???  

Try 3  
(a) Draw the NFA of $(y^{\ast}x)^{\ast}y^{\ast}$ and DFA of $(x ∨ y)^{\ast}$  
(b) Transform the NFA to DFA
(c) Simplify the resulting DFA
(d) Surprise!!!

## Example#2

Construct an automaton recognizing strings containing 3k+1 b symbols and discover the corresponding regular expression. Σ = {a,b}

$q_0 = q_0a ∨ q_2b ∨ λ$  
$q_1 = q_0b ∨ q_1a$  
$q_2 = q_1b ∨ q_2a$

$q_2 = q_2a ∨ q_1b ⇒ q_2 = q_1ba^{\ast}$  
NOTE: $X = XA ∪ B ⇒ X = BA^{\ast}$  
$q_1 = q_1a ∨ q_0b ⇒ q_1 = q_0ba^{\ast}$  
$q_2 = q_0(ba^{\ast})(ba^{\ast})$

$q_0 = q_0a ∨ q_0(ba^{\ast})^2b ∨ λ$  
$q_0 = q_0(a ∨ (ba^{\ast})^2b) ∨ λ$   
$q_0 = (a ∨ (ba^{\ast})^2b)^{\ast}$  
$q_1 = (a ∨ (ba^{\ast})^2b)^{\ast}ba^{\ast}$  
Another possible reg-ex might be: $a^{\ast}ba^{\ast}[(ba^{\ast})^3]^{\ast}$

#### Kleene Theorem

Any language is regular which is constructed by applying closed language operations on regular
languages. e.g. if we know $L_1$ and $L_2$ are regular languages, any language built by applying a
closed operation on them produces a new regular language.

Regular languages recognized by a finite automaton is closed under the following operations:
- Union, Intersection, Complement, Difference
- Concatenation
- Kleene star
- Reversal
- Homomorphism, Inverse Homomorphism (will not be discussed in detail.)

#### Union (Non-deterministic)
$M_1 = (S_1,Σ,Δ_1,s_{01},F_1) ← L(M_1)$  
$M_2 = (S_2,Σ,Δ_2,s_{02},F_2) ← L(M_2)$

$M = (S,Σ,δ,s_0,F) ← L(M_1) ∪ L(M_2)$

$S = S_1 ∪ S_2 ∪ \{s_0\}$  
$F = F_1 ∪ F_2$  
$F = F_1 ∪ F_2$  
$δ = Δ_1 ∪ Δ_2 ∪ \{\{s_0,λ,s_{01}\},\{s_0,λ,s_{02}\}\}$

#### Concatenation (Non-deterministic)

$L(M_1) · L(M_2) = L(M)$

$S = S_1 ∪ S_2$  
$s_0 = s_{01}$  (NOTE: use $L(M_1)$'s start state)  
$F = F_2$  (NOTE: use $L(M_2)$'s final state)   
$δ = Δ_1 ∪ Δ_2 ∪ (F_1 × \{λ\} × \{s_{02}\})$ (NOTE: add a λ trasition that is from $F_1$ to $s_{02}$)  

#### Kleene Star (Non-deterministic)

$L(M_1)^{\ast} = L(M)$

$S = S_1 ∪ \{s_0\}$  
$F = \{f_0\}$  
$δ = Δ_1 ∪ (F_1 × \{λ\} × \{s_{01}\}) ∪ (s_0 × λ × s_{01}) ∪ (F_1 × \{λ\} × F) ∪ (s_0 × λ × f_0)$  

#### Complement (deterministic)

$\overline{L(M_1)} = L(M)$  
$F = \{S_1 - F_1\}$  
NOTE: The new final states are all the original states except the original final states.

#### Intersection (Deterministic)

$L(M_1) ∩ L(M_2) = L(M)$

$S \subseteq S_1 × S_2$  
NOTE: The state set of M consists of ordered pairs of states formed by the **Cartesian product** of $M_1$ and $M_2$

$s_0 = (s_{01},s_{02})$  
NOTE: The new start state combines the start states of $M_1$ and $M_2$

$F \subseteq F_1 × F_2$ where $[(p_1,p_2) ∈ F] ⇔ [[p_1 ∈ F_1] ∧ [p_2 ∈ F_2]]$  
NOTE: A new state is accepting only if both component states are accepting.  

$Δ \subseteq Δ_1 × Δ_2$ where $[((p_1,p_2),σ,(q_1,q_2)) ∈ Δ] ⇔ [[(p_1,σ,q_1) ∈ Δ_1] ∧ [(p_2,σ,q_2) ∈ Δ_2]]$  
NOTE: M moves from $(p_1,p_2)$ to $(q_1,q_2)$ on input σ  
⇔ This transition occurs exactly when both $M_1$ and $M_2$ move accordingly on the same input σ

#### Difference (Deterministic)

$L_1 - L_2 = L1 ∩ \overline{L_2}$  
NOTE: The difference of $L_1$ and $L_2$ is the set of strings that are in $L_1$ but not in $L_2$, i.e. $L_1 ∩ \overline{L_2}$

#### Reversal (Non-deterministic)

$L(M) = L(M')^R$

$S = S' ∪ \{s_0\}$  
NOTE: The new state set consists of all original states plus a new start state
$s_0$.  
A new start $s_0$ is added to enable ε-transitions to all original accepting states, as only one start state is allowed.

$F = s'_0$  
NOTE: The new final state is the original start state.

$δ = \{[(p,σ,q) ∈ Δ] ⇔ [(q,σ,p) ∈ Δ']\}$  
$∪$  
$\{[(s_0,λ,f_i) ∈ Δ ∀f_i ∈ F']\}$  
NOTE: Each transition is the reverse of an original transition.  
Add ε-transitions from the new start state to every original final state.
