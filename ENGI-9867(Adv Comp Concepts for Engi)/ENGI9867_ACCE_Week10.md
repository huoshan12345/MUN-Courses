# PDAs (cont.) and CFL Properties

## Recap

Can the following languages be recognized by PDAs?

(1) $L_1 = \lbrace a^k$ \# $w\ |\ k > 0, w ∈ {\lbrace a,b \rbrace}^{\ast}, and\ |w|=k \rbrace$  
(2) $L_2 = \lbrace a^ib^jc^k\ |\ i = j\ or\ j = k \rbrace$  
(3) $L_3 = \lbrace w$ \# $w\ |\ w ∈ {\lbrace a,b \rbrace}^{\ast} \rbrace$  
<!-- GitHub KaTeX does not support # in math mode, so this is split as a workaround -->
<!-- Spaces are added around # to avoid breaking the inline math parsing. -->
## Closure of CFLs

- CFL’s are closed under  
(a) Union  
(b) Concatenation  
(c) Kleene star  
(d) Reversal  
(e) Homomorphism and inverse Homomorphism  

- CFL’s are not closed under    
(a) Intersection  
(b) Complement  
(c) Difference  

## Closure Under Union

#### Union

$G1 = \lbrace N_1,Σ_1,n_{01},↦_1 \rbrace$  
$G2 = \lbrace N_2,Σ_2,n_{02},↦_2 \rbrace$  

$G = L(G_1) ∪ L(G_2)$  

$G = \lbrace N,Σ,n_0,↦ \rbrace$  

$N = N_1 ⊎^a N_2$  (NOTE: disjoint union with α-renaming to avoid name conflicts)  
$Σ = Σ_1 ⊎ Σ_2$  (NOTE: disjoint union without renaming)  
$↦ = ↦_1 ⊎ ↦_2 ∪ \lbrace n_0 → n_{01}\ |\ n_{02} \rbrace$ (NOTE: include all productions and add a new start rule to choose G1 or G2)

## Closure Under Concatenation

#### Concatenation

$G1 = \lbrace N_1,Σ_1,n_{01},↦_1 \rbrace$  
$G2 = \lbrace N_2,Σ_2,n_{02},↦_2 \rbrace$  

$G = L(G_1)L(G_2)$  

$G = \lbrace N,Σ,n_0,↦ \rbrace$  

$N = N_1 ⊎ N_2$  
$Σ = Σ_1 ⊎ Σ_2$  
$↦ = ↦_1 ⊎ ↦_2 ∪ \lbrace n_0 → n_{01}n_{02} \rbrace$  

## Closure Under Kleene Star

#### Kleene Star

$G1 = \lbrace N_1,Σ_1,n_{01},↦_1 \rbrace$  

$G = L(G_1)^{ast}$  

$G = \lbrace N,Σ,n_0,↦ \rbrace$  

$N = N_1$  
$Σ = Σ_1$  
$↦ = ↦_1 ∪ \lbrace n_0 → n_{01}n_0\ |\ λ \rbrace$  

## Closure Under Reversal

#### Reversal

$G1 = \lbrace N_1,Σ_1,n_{01},↦_1 \rbrace$  

$G = L(G_1)^R$  

$G = \lbrace N,Σ,n_0,↦ \rbrace$  

$N = N_1$  
$Σ = Σ_1$  
$n_0 = n_{01}$  
$↦ = ∀[(ω_l → ω_r) ∈ ↦_1] ↔ [(ω_l → ω_r^R) ∈ ↦]$  

#### CFG for $\langle 0^m1^n\ |\ m ≥ n \rangle$  

$\langle S \rangle ::= 0 \langle S \rangle 1\ |\ \langle A \rangle$  
$\langle A \rangle ::= 0 \langle A \rangle \ |\ λ$  

#### CFG for $\langle 1^n0^m\ |\ n ≤ m \rangle$  

$\langle S \rangle ::= 1 \langle S \rangle 0\ |\ \langle A \rangle$  
$\langle A \rangle ::= \langle A \rangle 0\ |\ λ$  

## Closure Under Homomorphism

#### Homomorphism

$G1 = \lbrace N_1,Σ_1,n_{01},↦_1 \rbrace$  

$G = h(L(G_1))$  

$G = \lbrace N,Σ,n_0,↦ \rbrace$  

$N = N_1$  
$Σ = h(Σ_1)$  
$n_0 = n_{01}$  
$↦ = {↦_1}^a$  


## Closure Under Inverse Homomorphism

#### Inverse Homomorphism

$M_1 = (S_1,Σ_1,Γ_1,δ_1,s_{01},F_1)$  

$L(M) = h^{-1}(L(M_1))$  

$M = (S,Σ,Γ,δ,s_0,F)$  

- There is no simpler way to demonstrate this property using CFGs so we will use PDAs.
- M accepts symbols from h()’s range set where each symbol correspond to a string in $Σ_1$
- We need to transform the states and transitions $M_1$ likewise (*will be skipped, but you may research it if you are interested in it*).

## Closure Under Intersection

- Unlike the regular languages, the CFLs are not closed under intersection
- We may prove it with a counterexample
- $L_1 = \lbrace 0^n1^n2^i\ |\ n ≥ 1,i ≥ 1 \rbrace$ 
- $L_2 = \lbrace 0^i1^n2^n\ |\ n ≥ 1,i ≥ 1 \rbrace$ 
- $L = L_1 ∩ L_2$
- $L = \lbrace 0^n1^n2^n\ |\ n ≥ 1 \rbrace$ which is not a CFL.

## Closure Under Difference

- Any class of languages that is closed under difference is closed under intersection
- $L_1 - (L_1 - L_2) = L_1 ∩ L_2$
- If CFLs were closed under difference then they would have been closed under intersection as well
- But they are not closed under intersection, nor they do under difference.

## Closure Under Complement

- If CFLs were closed under complement then they would have been closed under intersection as well
- $\overline{\overline{L_1} ∪ \overline{L_2}} = L_1 ∩ L_2$  
- CFLs are closed under union but they are not closed under intersection, nor they do under complement.

## Unsolvable (Undecidable) CFL Problems

- For a given grammar/PDA belonging to a CFL, an algorithm can be devised to answer (decide) the following questions:
  - String ω is in L(G)
  - L(G) is empty
  - L(G) is infinite
- There are also questions which are proven to be unsolvable by an algorithm, such as:
  - Is a given CFG G ambiguous?
  - Is it possible to provide an unambiguous grammar for a given ambiguous CFL?
  - Are two CFL’s the same?
  - Are two CFL’s disjoint? (Empty intersection)
  - For a given CFG G, is L(G) equal to $Σ^{\ast}$?

---

# Turing Machine

Classical automata (a.k.a. language recognizers(DFA,NFA,PDA)) sometimes is incapable of recognizing very simple language(e.g. $a^nb^nc^n : n ≥ 0$).  
There exists more general language recognizers which perform transformation between chains of tokens. Turing machine is an example to this kind of language recognizers.

#### Church-Turing Thesis

In computability theory, the Church-Turing thesis is a combined hypothesis about the nature of functions whose values are effectively calculable; or, in more modern terms, functions whose values are algorithmically computable. In simple terms, the Church-Turing thesis states that a function is algorithmically computable if and only if it is computable by a Turing machine.  
Informally the Church-Turing thesis states that if some method (algorithm) exists to carry out a calculation, then the same calculation can also be carried out by a Turing machine (as well as by a recursively definable function, and by a λ-function).

The Church-Turing thesis is a statement that characterizes the nature of computation and cannot be formally proven. Even though the three processes mentioned above proved to be equivalent, the fundamental premise behind the thesis- the notion of what it means for a function to be effectively calculable- is “a somewhat vague intuitive one”. Thus, the “thesis” remains a conjecture.

Read/write head reads the corresponding symbol on the tape and according to the state of the control machine it either writes a new symbol, or it moves left(L) or right(R). If the machine attempts to move further left from the leftmost symbol on the tape than this situation is denoted as the “machine hangs”. Head may move as much as possible towards right.

Symbols:
- h: End of computation. Machine halts. Halt is not included in input, output and state alphabet.
- #: blank symbol
- L,R: Symbols indicating left and right movement. Those are not included in input or output alphabet.
- Input symbols are written on the leftmost side by convention.

## Formal Definition of a TM

- A turing machine(TM) is a quadruple $M = (S,Σ,δ,s_0)$, where:
- S: A finite, non-empty set of states. Usually h ∉ S.
- Σ: Input/output alphabet. ${\\\#} ∈ Σ$ but $L,R ∉ Σ$
- $s_0 ∈ S$: An initial state, an element of S.
- δ: The state-transition function $S × Σ → (S ∪ \{h\}) × (Σ ∪ \{L,R\})$  
NOTE: (current state, tape symbol) → (the next state or halt, writes a symbol or moves left/right)

$q ∈ S ∧ a ∈ Σ ∧ δ(q,a) = (p,b)$  
$q → p$

1. (Read) $a → b ∈ Σ$ (write on tape, in place of a)
2. $b = L$ (head left)
3. $b = R$ (head right)

We can match modern computers with Turing Machines; RAM can be matched with the tape, computer programs can be matched with the state table, microprocessor(excluding I/O units) can be matched with control unit of the TM. In order to improve understandability of the state table, following notion can be used:  
$q,σ,q',σ',HM$ where
- $q$ stands for current state of the machine
- $q'$ stands for the next state
- $σ$ stands for read symbol
- $σ'$ stands for symbol to be written (same with σ for no write)
- $HM$ stands for head move where $HM ∈ −1:L,0:None,1:R$

## Example 1

A machine that erases all the symbols from left to right.

$S = \{q_0,q_1\}$  
$Σ = \{a,{\\\#}\}$  
$s_0 = q_0$  

| q     | σ | $δ(q,σ)$       |
|-------|---|----------------|
| $q_0$ | a | $(q_1,{\\\#})$ |
| $q_0$ | # | $(h,{\\\#})$   |
| $q_1$ | a | $(q_0,a)^1$    |
| $q_1$ | # | $(q_0,R)$      |

$^1$: This row is to conform to the formal definition of a function

Now the same machine with a different notion and fewer lines

| q     | σ | $δ(q,σ)$,HM      |
|-------|---|------------------|
| $q_0$ | a | $(q_0,{\\\#}),1$ |
| $q_0$ | # | $(h,{\\\#}),0$   |

## Example 2

A machine that moves towards left and recognizes a symbols, halting with the first # symbol

$S = \{q_0\}$  
$Σ = \{a,{\\\#}\}$  
$s_0 = q_0$  

| q     | σ | $δ(q,σ)$       |
|-------|---|----------------|
| $q_0$ | a | $(q_0,L)$      |
| $q_0$ | # | $(h,{\\\#})$   |

## Configuration of a TM

A configuration is an element of the following set:  
$S ∪ \{h\} × Σ^{\ast} × Σ × (Σ^{\ast}(Σ − \{ {\\\#} \}) ∪ {Λ})$  
NOTE: it means a quadruple:   
Current state  
left tape content  
current tape symbol under the head  
right tape content (without trailing blanks), can be empty

For instance(assume the head is on the underlined symbol):  
$(q,aba,a,bab)$ or $(q,aba\underline{a}bab)$  
$(h,{\\\#}{\\\#},{\\\#},{\\\#}a)$ or $(h,{\\\#}{\\\#}\underline{\\\#}{\\\#}a)$  
$(q,Λ,a,aba)$ or $(q,Λ\underline{a}aba)$ or $(q,\underline{a}aba)$  
$(q,{\\\#}a{\\\#},{\\\#},Λ)$ or $(q,{\\\#}a{\\\#}\underline{\\\#}Λ)$ or $(q,{\\\#}a{\\\#}\underline{\\\#})$  

Following situation doesn’t conform with configuration definition:  
$(q,baa,a,bc{\\\#})$ or $(q,baa\underline{a}bc{\\\#})$  
NOTE: Right string must not end with #

#### Yields in one step for TM
$(q_1,ω_1,a_1,u_1) ⊢_M (q_2,ω_2,a_2,u_2)$  
Here $δ(q_1,a_1) = (q_2,b)$ and $b ∈ Σ ∪ {L,R}$

(1) $b ∈ Σ, ω_2 = ω_1, u_2 = u_1, a_2 = b$ ($a_2$ is written over $a_1$)  
(2) $b = L, ω_1 = ω_2a_2;(a_1 = {\\\#} ∧ u_1 = Λ ⇒ u_2 = Λ) ∨ (a_1 ≠ {\\\#} ∨ u_1 ≠ Λ ⇒ u_2 = a_1u_1)$  
Left movement:   
If the head is on a blank and no more symbols to the right blank is erased.   
If the head is on a symbol or some symbols exist on the right the situation is preserved.  
(3) $b = R, ω_2 = ω_1a_1;(u_1 = a_2u_2) ∨ (u_1 = Λ ⇒ u_2 = Λ ∧ a_2 = {\\\#})$  
Right movement: If there are no more symbols on the right blank is written.

NOTE: 
For left movement, we need to remove trailing '#'.  
Because if trailing '#' were allowed in u, the same tape could be represented in infinitely many ways:  
(q, ω, a, Λ)  
(q, ω, a, #)  
(q, ω, a, ##)  
...  
Thus u must be normalized (no trailing '#'), but ω does not need normalization.

For right movement, if the right side is empty, we need to write a '#'.

## Example 3
$ω,u ∈ Σ^{\ast};a,b ∈ Σ$ (u cannot end with #)

$δ(q_1,a) = (q_2,b) ⇒ (q_1,ω\underline{a}u) ⊢_M (q_2,ω\underline{b}u)$ &ensp; (b is written over a)

$δ(q_1,a) = (q_2,L) ⇒$  
 (i) $(q_1,ωb\underline{a}u) ⊢_M (q_2,ω\underline{b}au)$ &ensp; (shift one character to the left)  
(ii) $(q_1,ωb\underline{\\\#}) ⊢_M (q_2,ω\underline{b})$ &ensp;&ensp;&ensp;&ensp; (shift one character to the left, and remove a trailing '#')  

$δ(q_1,a) = (q_2,R) ⇒$  
 (i) $(q_1,ω\underline{a}bu) ⊢_M (q_2,ωa\underline{b}u)$ &nbsp; (shift one character to the right)  
(ii) $(q_1,ω\underline{a}) ⊢_M (q_2,ωa\underline{\\\#})$ &ensp;&ensp;&ensp; (shift one character to the right, and write a '#')  

## n steps computation

#### A computation of length n

A computation of length n or in other words n steps computation can be defined as:  
$C_0 ⊢_M C_1 ⊢_M C_2 ⊢_M...C_{n−1} ⊢_M C_n$

Example 1: A machine that erases all the symbols from left to right.

| q     | σ | $δ(q,σ)$       |
|-------|---|----------------|
| $q_0$ | a | $(q_1,{\\\#})$ |
| $q_0$ | # | $(h,{\\\#})$   |
| $q_1$ | a | $(q_0,a)^1$    |
| $q_1$ | # | $(q_0,R)$      |

$(q_0,\underline{a}aaa) ⊢_M (q_1,\underline{\\\#}aaa) ⊢_M (q_0,{\\\#}\underline{a}aa) ⊢_M (q_1,{\\\#}\underline{\\\#}aa) ⊢_M (q_0,{\\\#\\\#}\underline{a}a) ⊢_M$  
$(q_1,{\\\#\\\#}\underline{\\\#}a) ⊢_M (q_0,{\\\#\\\#\\\#}\underline{a}) ⊢_M (q_1,{\\\#\\\#\\\#}\underline{\\\#}) ⊢_M (q_0,{\\\#\\\#\\\#\\\#}\underline{\\\#}) ⊢_M (h,{\\\#\\\#\\\#\\\#}\underline{\\\#})$

## Turing Computable Function

#### Turing Computable Function

Turing computable functions can perform transformations over character strings.

$M = (S,Σ,δ,s_0)$  
Let’s distinguish $Σ_I$ as input alphabet and $Σ_O$ as output alphabet;  
$f(ω) = u ∧ ω ∈ {Σ_I}^{\ast} ∧ u ∈ {Σ_O}^{\ast} ⊆ Σ^{\ast}$ and  
$(s_0,{\\\#}ω\underline{\\\#})\ {⊢_M}^{\ast}\ (h,{\\\#}u\underline{\\\#}),{\\\#} ∉ Σ_I ∧ {\\\#} ∈ Σ_O$

## Example 4

A machine that inverses strings (writes b in place of a ; a in place of b)  
NOTE: The initial position is at the rightmost # of the string, and after completion, the head is required to remain positioned at this same rightmost #.

$S = \{q_0,q_1,q_2\}$  
$Σ = \{a,b,{\\\#}\}$  
$s_0 = q_0$  

| q     | σ | $δ(q,σ)$       |
|-------|---|----------------|
| $q_0$ | a | $(q_1,L)$      |
| $q_0$ | b | $(q_1,L)$      |
| $q_0$ | # | $(q_1,L)$      |
| $q_1$ | a | $(q_0,b)$      |
| $q_1$ | b | $(q_0,a)$      |
| $q_1$ | # | $(q_2,R)$      |
| $q_2$ | a | $(q_2,R)$      |
| $q_2$ | b | $(q_2,R)$      |
| $q_2$ | # | $(h,{\\\#})$   |

$(q_0,{\\\#}aab\underline{\\\#}) ⊢_M (q_1,{\\\#}aa\underline{b}) ⊢_M$  
$(q_0,{\\\#}aa\underline{a}) ⊢_M (q_1,{\\\#}a\underline{a}a) ⊢_M$  
$(q_0,{\\\#}a\underline{b}a) ⊢_M (q_1,{\\\#}\underline{a}ba) ⊢_M$  
$(q_0,{\\\#}\underline{b}ba) ⊢_M (q_1,\underline{\\\#}bba) ⊢_M$  
$(q_2,{\\\#}\underline{b}ba) ⊢_M (q_2,{\\\#}b\underline{b}a) ⊢_M$  
$(q_2,{\\\#}bb\underline{a}) ⊢_M (q_2,{\\\#}bba\underline{\\\#}) ⊢_M$  
$(h,{\\\#}bba\underline{\\\#})$  

## Example 5

Let’s represent a number n with n $I$ symbols like $III ...I$. Let’s build a machine that computes  
$f(n) = n + 1$

$S = \{q_0\}$  
$Σ = \{I,{\\\#}\}$  
$s_0 = q_0$  

**(a)** $(q_0,{\\\#}II\underline{\\\#}) ⊢_M (q_0,{\\\#}II\underline{I}) ⊢_M (h,{\\\#}III\underline{\\\#})$  
**(b)** $(q_0,{\\\#}I^n\underline{\\\#}) ⊢_M (h,{\\\#}I^{n+1}\underline{\\\#})$  
**(c)** $(q_0,{\\\#}\underline{\\\#}) ⊢_M (q_0,{\\\#}\underline{I}) ⊢_M (h,{\\\#}I\underline{\\\#})$  

## Turing Decidable Machine

#### Turing Decidable Machine

Let $Σ_0$ be our alphabet and ${\\\#} ∉ Σ_0$ and $L$ be a language $L ⊆ {Σ_0}^{\ast}$  
If we can compute the function $x_L$ like:  

$$
∀ω ∈ {Σ_0}^{\ast},F_L(ω) = \begin{cases}
Ⓨ ⇒ ω ∈ L \\
Ⓝ ⇒ ω ∉ L
\end{cases}
$$






