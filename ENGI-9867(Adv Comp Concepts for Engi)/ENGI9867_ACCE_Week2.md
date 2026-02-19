## Formal Languages and Alphabet

#### Theorems

Let ∅ denote empty language; A,B,C,D denote different languages defined over the alphabet Σ.

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
z ∈ AB ⇔ ∃ $x_1,y_1$[(z = $x_1y_1$) ∧ ($x_1$ ∈ A) ∧ ($y_1$ ∈ B)]  
z ∈ AC ⇔ ∃ $x_2,y_2$[(z = $x_2y_2$) ∧ ($x_2$ ∈ A) ∧ ($y_2$ ∈ C)]  
($x_1$ = $x_2$) ∧ ($y_1$ = $y_2$) ❌

- Let’s give a counter example to show that AB ∩ AC $\not\subseteq$ A(B ∩ C)  
A = { $a^n$ | n ∈ N }  
B = { $a^nb^n$ | n ∈ N }  
C = { $b^n$ | n ∈ N }  
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

Let A and B denote different languages defined over the alphabet Σ.
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

Let A and B denote different languages defined over the alphabet Σ and let n ∈ N.
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

#### Proof.

8. $AA^{\ast}$ = $A^{\ast}A$ = $A^+$
9. λ ∈ A ⇔ $A^+$ = $A^{\ast}$
13. $(A^{\ast}B^{\ast})^{\ast}$ = $(A ∪ B)^{\ast}$

#### Arden’s Theorem

Let A and B denote subsets of $Σ^{\ast}$ and let λ ∉ A.  
The only solution of X = AX ∪ B is X = $A^{\ast}B$

X = AX ∪ B  
X = A(AX ∪ B) ∪ B  
X = $A^2X$ ∪ AB ∪ B  
X = $A^2$ (AX ∪ B) ∪ AB ∪ B  
X = $A^3X$ ∪ $A^2B$ ∪ AB ∪ B  
...  
X = ... ∪ $A^3B$ ∪ $A^2B$ ∪ AB ∪ B  
X = (... ∪ $A^3$ ∪ $A^2$ ∪ $A^1$ ∪ $A^0$)B  
X = $A^{\ast}B$

####　Demonstration

X = $A^{\ast}B$ is a solution of X = AX ∪ B
Considering {λ}B = B,  
$A^{\ast}B$ = $AA^{\ast}B$ ∪ B  
= $A^+B$ ∪ B  
= ($A^+$ ∪ {λ}) ∪ B  
= $A^{\ast}B$

A similar proof can be done for the only solution of X = AX ∪ B being X = $A^{\ast}B$

# Formal Grammars, Languages and Chomsky Hierarchy

## Formal Grammars

#### Formal Grammar

A formal grammar is a set of formation rules for strings in a formal language. The rules describe how to form strings from the language’s alphabet that are valid according to the language’s syntax.

In our context
- Σ denotes the alphabet
- $Σ^{\ast}$ is the set of all words that can be constructed using Σ
- Grammar is the set of formation rules to construct a subset of $Σ^{\ast}$

For example, to construct an arithmetic expressions:  
- Z + - × / ( ) is sucient
- All the well-formed arithmetic expressions are meaningful except division by zero.
- (((2 - 1) / 3) + 4 × 6) is a well-formed and meaningful
- 2 + (3 / (5 - (10 / 2))) is well-formed as well but not meaningful

#### The Syntax of Grammars

In the classic formalization of generative grammars first proposed by Noam Chomsky in the 1950s as G = (N, Σ, $n_0$, ↦)
- N is a set of nonterminal symbols
- Σ is a set of terminal symbols that is disjoint from N
- $n_0$ is the start symbol
- ↦ is the set of production rules.

#### Some syntactical remarks
- If we call V = N ∪ Σ, ↦ is a relation defined over $V^{\ast}$.
- Rules follow the structure: $V^{\ast}NV^{\ast}$ → $V^{\ast}$
- A terminal symbol cannot be replaced with another set of symbols.
- Word production continues until no more non-terminals left

Formal grammars are also sometimes denoted as phrase structure grammars in the literature.

#### Example 1
Σ = {Harry, Sally, runs, swims, fast, often, long}  
N = {sentence, verbal sentence, noun, verb, adverb}  
$n_0$ = sentence

Grammar:  
sentence ↦ noun verbal sentence  
noun ↦ Harry  
noun ↦ Sally  
verbal sentence ↦ verb adverb  
adverb ↦ fast  
adverb ↦ often  
adverb ↦ long  
verb ↦ runs  
verb ↦ swims  

We can apply these rules in one of two ways to derive a canonical parse tree. We can either successively expand the **leftmost** expression first or we can successively expand the **rightmost** expression first

#### Parsing

Parsing, or, syntactic analysis, is the process of analyzing a text, made of a sequence of tokens (for example, words), to determine its grammatical structure with respect to a given formal grammar.

#### Example 2

Σ = { a,b,c }  
N = { $n_0$,w }  
↦ = { $n_0$ → aw | w → bbw | w → c }

L(G) = {a} · $\{bb\}^{\ast}$ · {c}  
= $a(bb)^{\ast}c$  
= { $a(bb)^nc$ | n ∈ N }

#### Example 3

Σ = { a,b,c }  
N = { $n_0$,w }  
↦ = { $n_0$ → $an_0b$ | $n_0b$ → bw | awb → c }

$n_0 ⇒ an_0b$  
⇒ $a(an_0b)b$  
⇒ $a^nn_0b^n$  
⇒ $a^n(n_0b)b^{n-1}$  
⇒ $a^nbwb^{n-1}$  
⇒ $a^{n-1}abwb^{n-1}$  
⇒ $a^{n-1}cb^{n-1}$  
$n_0 ⇒ a^{n-1}cb^{n-1}$  

Or in a general form: L(G) = { $a^mcb^m$ | m ∈ N }

#### Example 4

Σ = {a,b,c}  
N = {A,B,C}  
$n_0$ = A  
↦ = {  
A → aABc  
A → abc  
cB → Bc  
bB → bb  
}

A  
aABc  
aaABcBc  
aaaABcBcBc  
aaaabcBcBcBc  
aaaabBccBcBc  
aaaabBcBccBc  
aaaabBBcccBc  
aaaabBBccBcc  
aaaabBBcBccc  
aaaabBBBcccc  
aaaabbBBcccc  
aaaabbbBcccc  
aaaabbbbcccc  
$a^4b^4c^4$

L(G) = { $a^kb^kc^k$ | k > 0 }

# Chomsky Hierarchy and Regular Expressions

## Chomsky Hierarchy

The Chomsky hierarchy is a containment hierarchy of classes of formal grammars. For a formal grammar G = (N, Σ, $n_0$, ↦)

#### Type-0 grammars

- Type 0 grammars (unrestricted grammars) include all formal grammars.
- They generate exactly all languages that can be recognized by a Turing machine.
- These languages are also known as the recursively enumerable languages.
- Example 3 conforms to a Type-0 grammar.

#### Type-1 grammars

- Type-1 grammars (context-sensitive grammars) have transformation rules s.t. for w1 → w2 rule |w1| ≤ |w2| should hold.
- Context sensitivity follows the rules having the form lwr' → lw'r
- The languages described by these grammars are exactly all languages that can be recognized by a linear bounded automaton.
- Example 4 conforms to a Type-1 grammar.

#### Type-2 grammars

- Type-2 grammars (context-free grammars) generate the context-free languages.
- These are defined by rules of the form A → γ with a nonterminal (A) and a string of terminals and nonterminals (γ).
- These languages are exactly all languages that can be recognized by a non-deterministic pushdown automaton.
- Context-free languages are the theoretical basis for the syntax of most programming languages.
- Example 1 conforms to a Type-2 grammar.

#### Type-3 grammars

- Type-3 grammars (regular grammars) generate the regular languages.
- Such a grammar restricts its rules to a single nonterminal on the left-hand side and a right-hand side consisting of a number of terminals, possibly followed by a single nonterminal.
- These languages are exactly all languages that can be decided by a finite state automaton.
- Additionally, this family of formal languages can be obtained by regular expressions.
- Regular languages are commonly used to define search patterns.
- Example 2 conforms to a Type-3 grammar.

Only Type-2 and Type-3 grammars have syntax trees.  
$n_0$ → λ rule can be added to any type to support empty sentences  
Type-3 $\subseteq$ Type-2 $\subseteq$ Type-1 $\subseteq$ Type-0

| Type | Language Type<br>(Grammars)  | Form of Productions<br>in Grammar  | Accepting<br>Device  |
|-------|-----|-----|-----|
| 0     | Recursively<br>enumerable<br>(unrestricted) | α → β<br>α,β ∈ $(N ∪ Σ)^+$ | Turing machine |
| 1     | Context-sensitive | α → β<br>α,β ∈ $(N ∪ Σ)^+$, |α|≤|β| | Linear-bounded<br>automaton |
| 2     | Context-free | A → α<br>A ∈ N, α ∈ $(N ∪ Σ)^+$ | Pushdown<br>automaton |
| 3     | Regular | A → σB, A → σ<br>A,B ∈ N, σ ∈ $Σ^+$ | Finite<br>automaton |

## Notes on Chomsky Hierarchy

- For regular grammars, corresponding rules may either follow A → σB formed rules or
A → Bσ formed rules. Not both!
- When determining the Chomsky type of a grammar, we ignore **initial** λ productions.
- Whenever there are λ productions (other than an initial rule) in a grammar we treat the grammar as Type-0.
- λ productions (other than an initial rule) can always be eliminated
- Grammar’s type and corresponding language’s type may be different. There may be multiple grammars of different types for the same language.  
NOTE: L = $a^+b^+$ is Type-3 language, but it also can be produced by a Type-2 grammar.
- A language’s type is the type of the most restrictive grammar that can produce the
language.

## Contemporary Perspectives on LLMs and Linguistic Theory

#### Regular Expression

Regular expressions (abbrv.: regex, regexp) provide a concise and flexible means to ”match” (specify and recognize) strings of text, such as particular characters, words, or patterns of characters.  
A regular expression can be defined over an alphabet Σ by induction:
1. Each and every element of λ and Σ is a regular expression
  - L(λ) = {λ}
  - L(a) = {a} ∀a ∈ Σ
  - L(∅) = ∅
2. Concatanation operation(·)  
L(αβ) = L(α)L(β)
3. Alternation operation(∨)  
L(α ∨ β) = L(α) ∪ L(β)
4. Kleene star operation(*)  
L($α^{\ast}$) = $(L(α))^{\ast}$

#### Theorem

Let L be a language described over S s.t.  L $\subseteq$ $S^{\ast}$. L is called a regular language if it conforms to a regular grammar G. In other words L = L(G).  
Regular expressions describe regular languages in formal language theory. There exists an isomorphism between the described language and the regular expression. They have the same expressive power as regular grammars.

Syntax diagrams can be used define regular expressions. The following three diagrams describe basic properties of regular expressions.

- Concetanation ($α_1α_2$)
- Alternation ($α_1 ∨ α_2$)
- Kleene star ($(α_1)^{\ast}$)

The basis regular expression syntax only covers these operators. Operators like numbered repetitions (e.g. $a^nb^n$) can be used to extend the type of language being represented.
- a ∨ b ∨ $c^{\ast}$
- (a ∨ b) $cd^{\ast}$
- $(a ∨ bc)^{\ast}$

## Precedence of Regular Expressions

Precedence of operators are defined from highest to lowest as
- Kleene star (*) and positive closure (+)
- Concatenation (·), may be omitted
- Alternation (∨), sometimes shown with (+) or (|)

## Algebraic Laws of Regular Expressions

- Commutativeness
  - L1 ∨ L2 = L2 ∨ L1
- Association
  - (L1 ∨ L2) ∨ L3 = L1 ∨ (L2 ∨ L3)
  - (L1L2)L3 = L1(L2L3)
- Identity
  - L ∨ ∅ = L
  - λL = Lλ = L
- Absorbing
  - L∅ = ∅
- Distribution
  - L1(L2 ∨ L3)=L1L2 ∨ L1L3
  - (L1 ∨ L2)L3 = L1L3 ∨ L2L3
- Idempotency
  - L1 ∨ L1 = L1
- Kleene Closure
  - $(L^{\ast})^{\ast}$ = $L^{\ast}$
  - $(∅)^{\ast}$ = λ
  - $λ^{\ast}$ = λ
  - $L^+$ = $LL^{\ast}$
  - L? = λ ∨ L we will prefer the latter notation