# PDAs (cont.) and CFL Properties

## Recap

Can the following languages be recognized by PDAs?

(1) $L_1 = \lbrace a^k\text{\#}w\ |\ k > 0, w ∈ {\lbrace a,b \rbrace}^{\ast}, and\ |w|=k \rbrace$  
(2) $L_2 = \lbrace a^ib^jc^k\ |\ i = j\ or\ j = k \rbrace$  
(3) $L_3 = \lbrace w\text{\#}w\ |\ w ∈ {\lbrace a,b \rbrace}^{\ast} \rbrace$  

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














