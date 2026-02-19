# Backus-Naur Form and Deterministic Finite Automata

## Backus-Naur Form Definition

#### A Type-0 Grammar

\<n0\> ::= a\<n0\>b  
\<n0\>b ::= b\<w\>  
ab\<w\> ::= c  

#### A Type-1 Grammar

\<A\> ::= a\<A\>\<B\>c | abc
c\<B\> ::= \<B\>c
b\<B\> ::= bb

#### A Type-2 Grammar

\<sentence\> ::= \<noun\>\<verbal sentence \>  
\<noun\> ::= Harry | Sally  
\<verbal sentence\> ::= \<verb\>\<adverb\>  
\<verb\> ::= runs | swims  
\<adverb\> ::= fast | often | long  

#### A Type-3 Grammar

\<n0\> ::= a\<w\>  
\<w\> ::= bb\<w\> | c  

Rules of the form w → bbw are called recursive rules. If a recursive rule’s non-terminal symbol is at the rightmost side it is called a normal rule.

# Deterministic Finite Automata

## Definitions

#### Automaton

An automaton is an abstract model of a machine that perform computations on an input by moving through a series of states or configurations. At each state of the computation, a transition function determines the next configuration on the basis of a finite portion of the present configuration. As a result, once the computation reaches an accepting configuration, it accepts that input. The most general and powerful automata is the Turing machine.

#### Deterministic Finite Automata

A DFA accepts/rejects finite strings of symbols and only produces a unique computation (or run) of the automaton for each input string. Deterministic refers to the uniqueness of the computation.

The major objective of automata theory is to develop methods by which computer scientists can describe and analyze the dynamic behavior of discrete systems, in which signals are sampled periodically.

## Formal Definition of a DFA

A deterministic finite state machine is a quintuple M = ($Σ,S,s_0,δ,F$), where:
- S: A finite, non-empty set of states where s ∈ S.
- Σ: Input alphabet (a finite, non-empty set of symbols)
- $s_0$: An initial state, an element of S.
- δ: The state-transition function δ: S × Σ → S
- F: The set of final states where F $\subseteq$ S.

This machine is a Moore machine where each state produces the output in set Z = {0,1}
corresponding to the machine’s accepting/rejecting conditions.

## DFA as a machine

Consider the physical machine below with an input tape. The tape is divided into cells, one next to the other. Each cell contains a symbol of a word from some finite alphabet. A machine that is modeled by a DFA, reads the contents of the cell successively and when the last symbol is read, the word is said to be accepted if the DFA is in an accepted state.

A run can be seen as a sequence of compositions of transition function with itself. Given an
input symbol σ ∈ Σ when this machine reads σ from the strip it can be written as  
δ(s,σ) = s′ ∈ S.

#### Configuration

A computation history is a (normally finite) sequence of configurations of a formal automaton. Each configuration fully describes the status of the machine at a particular point.  
s,ω ∈ S × $Σ^{\ast}$

Configuration derivation is performed by a relation $⊢_M$. If we denote the tuples in $⊢_M$ as
(s,ω) and (s′,ω′), the relation can be defined as:  
- ω = σω′ ∧ σ ∈ Σ  
- δ(s,σ) = s′

A transition defined by this relation is called derivation in one step and denoted as (s,ω) $⊢_M$ (s′,ω′). Following definitions can be defined based on this:
- Derivable configuration: (s,ω) $⊢_M^{\ast}$ (s′,ω′) where $⊢_M^{\ast}$ is the transitive closure of $⊢_M$
- Recognized word: ($s_0$,ω) $⊢_M^{\ast}$ ($s_i$,λ) where $s_i$ ∈ F.
- Execution: ($s_0,ω_0$) ⊢ ($s_1,ω_1$) ⊢ ($s_2$,ω) ⊢ ... ⊢ ($s_n$,λ) where λ is the empty string.
- Recognized Language: L(M) = { $ω_0$ ∈ $Σ^{\ast}$ | ($s_0$,ω) $⊢_M^{\ast}$ ($s_i$,λ) ∧ $s_i$ ∈ F }

#### Language Recognizer

The transitive closure of $⊢_M$ as $⊢_M^{\ast}$. (q,ω) $⊢_M^{\ast}$ (q′,ω′) denotes that (q,ω) yields (q′,ω′) after some number of steps.
(s,ω) $⊢_M^{\ast}$ (q′,λ) denotes that ω ∈ $Σ^{\ast}$ is recognized by an automaton if q ∈ F. In other words  
L(M) = { ω ∈ $Σ^{\ast}$ | (s,ω) $⊢_M^{\ast}$ ($q_i$,λ) ∧ $q_i$ ∈ F }

#### Example 1

S = { $q_0,q_1$ }, Σ = {a,b}, $s_0 = q_0$, F = { $q_0$ }

| q | σ | δ(q,σ) |
|---|---|---|
| $q_0$ | a | $q_0$ |
| $q_0$ | b | $q_1$ |
| $q_1$ | a | $q_1$ |
| $q_1$ | b | $q_0$ |

$(q_0,aabba) ⊢_M (q_0,abba)$  
$(q_0,abba) ⊢_M (q_0,bb)$  
$(q_0,bba) ⊢_M (q_1,ba)$  
$(q_1,ba) ⊢_M (q_0,a)$  
$(q_0,a) ⊢_M (q_0,λ)$  

L(M) = $(a ∨ ba^{\ast}b)^{\ast}$. We can write the grammar as:  
V = S ∪ Σ  
I = Σ = {a,b}  
$s_0 = q_0 = n_0$  
$\langle q_0 \rangle$ ::= λ | $a \langle q_0 \rangle$ | $b \langle q_1 \rangle$ | a  
$\langle q_1 \rangle$ ::= $b \langle q_0 \rangle$ | $a \langle q_1 \rangle$ | b  

#### Example 2 

L(M) = { ω | ω ∈ $\{a,b\}^{\ast}$ ∧ ω should not include three successive b’s }  
S = { $q_0,q_1,q_2,q_3$ }, Σ = {a,b}, $s_0 = q_0$, F = { $q_0,q_1,q_2$ }

| q | σ | δ(q,σ) |
|---|---|---|
| $q_0$ | a | $q_0$ |
| $q_0$ | b | $q_1$ |
| $q_1$ | a | $q_0$ |
| $q_1$ | b | $q_2$ |
| $q_2$ | a | $q_0$ |
| $q_2$ | b | $q_3$ |
| $q_3$ | a | $q_3$ |
| $q_3$ | b | $q_3$ |

We have a dead state $q_3$ where the automaton is not able to change state once it visits the dead state.  
L(M) = $[(λ ∨ b ∨ bb)a]^{\ast}$(λ ∨ b ∨ bb)

####　Example 3

S = { $q_0,q_1,q_2$ }, Σ = {x,y}, $s_0 = q_0$, F = { $q_2$ }

$\langle q_0 \rangle$ ::= $x \langle q_0 \rangle$ | $y \langle q_1 \rangle$  
$\langle q_1 \rangle$ ::= $y \langle q_2 \rangle$ | y | $x \langle q_0 \rangle$  
$\langle q_2 \rangle$ ::= y | $y \langle q_2 \rangle$ | $x \langle q_0 \rangle$  

L(M) = $((x ∨ yx)^{\ast}yy^+x)^{\ast}(x ∨ yx)^{\ast}yy^+$  
L(M) = $((λ ∨ y ∨ yy^+)x)^{\ast}yy^+$ = $(y^{\ast}x)^{\ast}yy^+$  
L(M) = $(x ∨ yx ∨ yy^+x)^{\ast}yyy^{\ast}$


# Non-deterministic Finite Automata (NFA)

In an NFA, given an input symbol it is possible to jump into several possible next states from each state.

## Formal Definition of an NFA

A non-deterministic finite state machine is a quintuple M = ($Σ,S,s_0,Δ,F$), where:
- S: A finite, non-empty set of states where s ∈ S.
- Σ: Input alphabet (a finite, non-empty set of symbols)
- $s_0$: An initial state, an element of S.
- Δ: The state-transition relation Δ: S × $Σ^{\ast}$ × S
- F: The set of final states where F $\subseteq$ S.

A configuration is defined as a tuple in set S × $Σ^{\ast}$. Considering the definition of derivation in one step:  
(q,ω) $⊢_M$ (q′,ω′) ⇒ ∃u ∈ $Σ^{\ast}$(ω = uω′ ∧ (q,u,q′) ∈ Δ)

For deterministic automata Δ $\subseteq$ S × $Σ^{\ast}$ × S relation becomes a function S × Σ → S. For (q,u,q′) triplets |u| = 1 ∧ (∀q ∈ S ∧ ∀u ∈ Σ)∃!q′ ∈ S  
NOTE: ∃! means **exists and is unique**

The language that an NFA recognizes is L(M) = { ω | (s,ω)$⊢_m^{\ast}$(q,λ) ∧ q ∈ F }

## An example NFA

Build an NFA that recognizes languages including bab or baab as substrings.

$S = \{q_0,q_1,q_2,q_3\}$  
Σ = {a,b}  
$s_0 = q_0$  
$F = \{q_3\}$  
$Δ = \{(q_0,a,q_0),(q_0,b,q_0),(q_0,ba,q_1),(q_1,b,q_3),(q_1,a,q_2), (q_2,b,q_3),(q_3,a,q_3),(q_3,b,q_3)\}$  

M = (S,Σ,Δ,$s_0$,F)  
$\langle q_0 \rangle$ ::= $a \langle q_0 \rangle$ | $b \langle q_0 \rangle$ | $ba \langle q_1 \rangle$  
$\langle q_1 \rangle$ ::= $b \langle q_3 \rangle$ | b | $a \langle q_2 \rangle$  
$\langle q_2 \rangle$ ::= $b \langle q_3 \rangle$ | b  
$\langle q_3 \rangle$ ::= a | b | $a \langle q_3 \rangle$ | $b \langle q_3 \rangle$  
$\langle q_0 \rangle$ ::= $a \langle q_0 \rangle$ | $b \langle q_0 \rangle$ | $ba \langle q_1 \rangle$  
$\langle q_1 \rangle$ ::= $b \langle q_3 \rangle$ | b | $a \langle q_2 \rangle$  
$\langle q_2 \rangle$ ::= $b \langle q_3 \rangle$ | b  
$\langle q_3 \rangle$ ::= a | b | $a \langle q_3 \rangle$ | $b \langle q_3 \rangle$  

A possible derivation may follow the path:
$(q_0,aaabbbaabab) ⊢$  
$(q_0,aabbbaabab) ⊢ (q_0,abbbaabab) ⊢$  
$(q_0,bbbaabab) ⊢ (q_0,bbaabab) ⊢$  
$(q_0,baabab) ⊢ (q_1,abab) ⊢$  
$(q_2,bab) ⊢ (q_3,ab) ⊢ (q_3,b) ⊢ (q_3,λ)$  

#### Lemma

M = (S,Σ,Δ,$s_0$,F) ∧ q,r ∈ S ∧ x,y ∈ $Σ^{\ast}$  
∃p ∈ S ∧ (q,x)$⊢_M^{\ast}$(p,λ) ∧ (p,y)$⊢_M^{\ast}$(r,λ) ⇒ (q,xy)$⊢_M^{\ast}$(r,λ)

#### Definition

Regular Grammar: All the production rules are of type-3.  
Regular Language: Languages that can be recognized by regular grammars.  
Regular Expression: ∅, {λ}, {a | a ∈ Σ}, A ∨ B, A.B, ${A^\ast}$  
Regular set: The sets which can be represented by regular expressions are called regular sets.

Regular grammars can be represented by NFAs.

- Non-terminal symbols are assigned to states
- Initital state corresponds to initial symbol
- Accepting states corresponds to the rules that end with terminal symbols
- If λ should be recognized, initial state is an accepting state.

Languages recognized by finite automata (Regular Languages) are closed under union, concatenation and Kleene star operations.

#### Kleene Theorem

Every regular language can be recognized by a finite automaton and every finite automaton defines a regular language.

M = (S,Σ,Δ,$s_0$,F) ⇔ G = (N, Σ, $n_0$, ↦), L = L(G) whereG is a grammar of type-3.  
S = N ∪ $f_i$  
F $\subseteq$ S  
$s_0 = n_0$

