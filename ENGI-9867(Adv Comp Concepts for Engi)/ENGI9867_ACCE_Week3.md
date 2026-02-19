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