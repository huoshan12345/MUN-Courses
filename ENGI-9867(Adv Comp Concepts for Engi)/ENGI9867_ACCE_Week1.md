## Computing Machines

#### Computer

A computer is a general purpose machine which can be programmed to carry out a finite set of arithmetic or logical operations (computation).

#### Machine

A machine is a tool consisting of one or more generally moving parts that is constructed to achieve a particular goal. However, the advent of electronics technology has led to the development of devices without moving parts that are considered machines.

#### Abstract Machine

An abstract machine is a theoretical model of a computer hardware or software system.

## The Future of Engineering is Provable

FROM: Build -> Test -> Patch -> Repeat  
TO: Specify -> Model -> Prove -> Synthesize

## The Two Forces Shaping Modern Systems

- Unbounded Complexity: 
Systems face exponential growth in complexity.
Real-world challenges like supply chain logistics are often NP-hard, 
meaning perfect solutions are computationally infeasible at scale. 
This creates a combinatorial explosion of possibilities that must be managed.

- The Need for Absolute Correctness: 
In safety-critical domains like avionics and autonomous systems, failure is not an option. The demand for high-assurance software is non-negotiable, requiring a rigorous, provable approach to engineering that guarantees reliability.

## To Control a System, You Must First Describe It Precisely.

- Finite Automaton (FA)  
A theoretical tool from Automata Theory used for recognizing formal languages.  
Answers: Is this string in the language?

- Finite State Machine (FSM)  
An engineering model used to describe system behavior and control.  
Answers: What should the system do next?

## Finite State Machine (FSM)

An FSM has a mathematical model defined by a quintuple (S, I, O, δ, ω), where:
- S: Set of states.
- I: Input alphabet (a finite, non-empty set of symbols).
- O: Output alphabet (a finite, non-empty set of symbols).
- δ: The transition function defined on `I × S -> S`.
- ω: The output function defined on either `S -> O` or `I × S -> O`.

## FSM properties

A finite state machine should hold the following properties:
- It has finite input and output alphabets.
- It is deterministic.
- It has transducer capability.


#### Deterministic Machine

For a deterministic machine, the outcome of a transition from one state to another given a certain input can be predicted for every occurrence. In a deterministic finite state machine, for each pair of state and input symbol there is one and only one transition to a next state.

#### Transducer

A transducer machine has two alphabets: an input alphabet and an output alphabet.  
Transducers are said to be able to transform inputs to output.  
When realizing transducers with digital circuits, the concept of discrete-time is used.

#### Discrete Time

Discrete time is the discontinuity of a function’s time domain that results from sampling a variable at a finite interval. One of the fundamental concepts behind discrete time is an implied (actual or hypothetical) system clock.

## Modeling FSMs

Following elements can be used in modeling FSMs:
- Mealy Machine
- Moore Machine

## Example#1: Coffee Vending Machine
A coffee vending machine that accepts coins of 5, 10 and 25 cents, gives co↵ee for 15 cents and returns the change. Let’s build Mealy and Moore models of this machine.

**Mealy model**, Sx/i,j: x denotes money input so far, i change return and j holds C for coffee output and - for no output.  

For Moore model the number of states need to be at least the number of different State/output pairs in the Mealy model. States should not be assigned to the coins input. When no coins are input current state is preserved.

## Example#2: Synthesizing Safety for Autonomous Systems

#### Problem Statement:  
How can we generate a controller that is guaranteed to steer a system to a goal while avoiding obstacles, even when accounting for external disturbances?  

This process is called **controller synthesis**.  

#### Transition System Definition
- States: robot states x ∈ $R^n$
- Inputs: control inputs u ∈ U
- Transitions: defined by system dynamics x[t+1] = A[t]x[t] + B[t]u[t] + d[t]
- Initial states: x[0] ∈ Ө

This defines a (possibly infinite-state) transition system automaton

| Control Problem | Automata Concept |
|---|---|
| Initial set Ө | Initial states |
| Obstacles O[t] | Forbidden (rejecting) states |
| Goal set G | Accepting states |
| Trajectory | Run (execution) |
| Reach-avoid requirement | Language acceptance condition |


## Modeling Computation and Computer Programs

- Any kind of problem that can be handled by computers can be encoded into 0’s and 1’s.
- Any solution that can be executed by a computer can be modeled as a machine.
- Using Automata Theory, we can reason about the problems and solutions that can be handled by computers.
- We can reason about the relative e↵ectiveness of algorithms, intractability, and undecidability.

## Automata Theory in Today’s Technology & Engineering

#### Compilers, Interpreters, and Language Tools

Automata theory is used verbatim in language processing.  
- Lexical analysis is based on DFAs and NFAs.
- Parsing relies on Context-Free Grammars and Pushdown Automata.
- These form the front-end of compilers and interpreters for C, C++, Java, Python,as well as MATLAB, Verilog, VHDL,and LLVM-based toolchains.

#### Regular Expressions

Regular expression engines are fundamentally NFA/DFA-based,withperformance
optimizations.
- IDEs (search, refactoring)
- Network packet inspection
- Log analysis and security tools
- Large-scale text processing pipelines

#### Finite State Machines (FSMs) in Hardware

Digital systems fundamentally rely on FSMs; modern hardware cannot be designed without
them.  
- Used in CPU control units, microcontrollers, and communication protocols
- Core abstraction in embedded systems and FPGA/ASIC design
- Typically modeled as Moore and Mealy machines

#### Control Systems and Robotics

Modern control and robotics use formal automata models, not metaphors.
- Automata-based controller synthesis
- Reach–avoid specifications, timed automata, hybrid automata
- Applications in autonomous vehicles, drones, and industrial robots

#### Model Checking

Automata theory is central to formal verification.
- Buchi automata, ω-automata, and timed automata
- Verification of hardware correctness, protocol safety, deadlock freedom, and liveness
- Widely used tools: SPIN, NuSMV, UPPAAL, PRISM

#### Active and Ongoing Research Areas

Automata theory remains an active field driven by safety-critical needs.
- Timed, probabilistic, hybrid, and game automata
- Automata learning and runtime verification
- Applications in autonomous and safety-critical systems

## Formal Languages and Automata

#### Formal Languages

A formal language is a mathematically defined set of strings or traces.
- Defined using:
  - Grammars (regular, context-free, etc.)
  - Logic (FO, MSO, temporal logic)
- Used to describe what behaviors are allowed

Examples: Program syntax, Communication traces, Execution histories

#### Automata

Automata are operational models that recognize or generate formal languages.
- Describe how behavior evolves step by step

#### Examples
- Finite automata -> regular languages
- Pushdown automata -> context-free languages
- Buchi automata -> infinite behaviors

#### Key Idea

Formal languages describe behavior **declaratively**; automata describe it **operationally**.

## Formal Methods

Formal methods use mathematics to specify, model,andverify systems.  

They generalize ideas from:
- Formal languages: what behaviors exist
- Automata: how behaviors arise

Formal methods go beyond strings to include:
- Data
- State invariants
- Correctness proofs

#### Key Idea

Formal methods provide a unified mathematical framework for reasoning about **behavior**, **state**, and **correctness** of systems.

#### Automata-based Formal Methods

- State machines / Statecharts
  - Extended finite automata
  - Languages = event traces
- Model checking
  - System -> automaton
  - Property -> logic formula
  - Verification -> language containment / emptiness

#### Logic-based Formal Methods
- Hoare Logic
  - Programs as state transitions
  - Correctness = logical property of executions
- Z / B
  - States defined as sets
  - Operations define state transitions
- HOL / Coq
  - Automata and languages as formal objects
  - Machine-checked proofs

## Finite State Machine(FSM)

An FSM has a mathematical model defined by a quintuple (S, I, O, δ, ω), where:
- S: Set of states.
- I: Input alphabet (a finite, non-empty set of symbols).
- O: Output alphabet (a finite, non-empty set of symbols).
- δ: The transition function defined on `I × S -> S`.
- ω: The output function defined on either `S -> O` or `I × S -> O`.

## An example Machine

Suppose we want to design a machine that reads numerical codes input from a keypad and accepts only one certain key combination. For this particular case(S, I, O, δ, ω) can be defined as:
- I ∈ {0,1,2,...,9}. We may want to restrict the number of digits to 4, for example 1234 ∈ $I^4$
- S: At each keystroke we need to control if the correct digit is input. In our case |S| =5 or $s_{i}$ ∈ S : 0 ≤ i ≤ 4
- O = {open,closed} is the output alphabet.
- Our machine is going to accept the code after 4 correct inputs. The final state F = $s_{4}$. Let’s ignore any wrong combinations at this moment for the sake of simplicity.
- Since we only have one correct combination can be defined as follows δ:  
($s_{0}$, 1) -> $s_{1}$  
($s_{1}$, 9) -> $s_{2}$  
($s_{2}$, 0) -> $s_{3}$  
($s_{3}$, 3) -> $s_{4}$  
- Our output function ω maps $s_{i}$ -> closed where 0 ≤ i ≤ 3 and $s_{4}$ -> open

## Formal Languages

#### Language

Language may refer either to the specifically human capacity for acquiring and using complex systems of communication, or to a specific instance of such a system of complex communication.

#### Formal Language

In mathematics, computer science, and linguistics, a formal language is a set of strings of symbols. The alphabet of a formal language is the set of symbols, letters, or tokens from which the strings of the language may be formed which are called words.

## Inductively Defined Sets

One way to build a formal language is to inductively define the set of words using a set of symbols.

#### Inductive Definition

A definition of a term within which the term itself appears, and that is well-founded, avoiding an infinite regress. Also called recursive definition.

## Inductively Defined Sets

In order to define a set E inductively, we need to have:

- Basis: An initial set S of elements where S $\subseteq$ E. Members of S are called basis elements
which are used to derive members of E. An alphabet contains basis elements for natural
languages.
- Rules: Functions that are used to transform elements of E into new elements.  
Ω = { $f_{1}$, $f_{2}$,..., $f_{n}$ } ∧ ∀ $f_{i}$ ∈ Ω  
$f_{i}$: E × E ×...× E -> E  
∀ $x_{1}$, $x_{2}$,... $x_{p}$ ∈ E, $f_{i}$($x_{1}$, $x_{2}$,..., $x_{p}$) = X ∈ E
- Closure: Performing the rules on members of E always produces a member of E. In
another way Ω(E) $\subseteq$ E

## Inductively Defined Sets

In order to define a set E inductively, we need to have:
- Induction:  
S0 = S  
S1 = Ω(S0) ∪ S0 Rules applied  
S2 = Ω(S1) ∪ S1  
...  
Si+1 = Si ∪ Ω(Si) = Si $\subseteq$ E (closure)  
i can be finite or infinite.
- Element height: Defined as the cardinality of the set in which an element is derived for the first time. H(x) = min{i | ∈ 2 Si}

## Inductively Defined Sets

Let’s build the set of even numbers inductively:
1. 0 ∈ E basis element
2. n ∈ E ⇒ (n+2) ∈ E
3. No other number can be identified as even number, apart from the rule number (2)

## Definitions

- Alphabet: A finite, non-empty set of symbols or characters. Denoted as Σ
- Word: A finite array or string from Σ
- Word Length: Number of symbols in a word.
- Empty string: A word of length 0. Denoted as or λ or Λ or ε.

## Word concatenation

Concatenation is performed by joining two character strings end-to-end.

(x = $a_{1}$ $a_{2}$... $a_{n}$) ∧ (y = $b_{1}$ $b_{2}$... $b_{m}$) ⇒ xy = $a_{1}$ $a_{2}$... $a_{n}$ $b_{1}$ $b_{2}$... $b_{m}$(x&y)  

Identity element of concatenation is λ    
x = λ ⇒ xy=y  
y = λ ⇒ xy=x

We can build a monoid set of words($Σ^{*}$) from the alphabet using concatenation operation having an empty string as an identity element and holding associativity property.

## Reverse of a string

$(baba)^R$ = abab  
$(ana)^R$ = ana 

We can define the operation using induction:
1. |w| = 0 ⇒ $w^R$ = w = λ
2.  Assume we have two strings w and u.  
|w| = n + 1  
|u| = n  
n ∈ N
(w = ua) ∧ (a ∈ Σ) ⇒ $w^R$ = a $u^R$  

#### Theorem
$(wx)^R$ = $x^R$ · $w^R$ ∧ (|x| = n, |w| = m) ∧ (m, n ∈ N)

#### Proof.
|x| = 0 ⇒ x = λ  
$(wx)^R$ = $(wλ)^R$ = $w^R$ = λ$w^R$ = $λ^R$ $w^R$ = $x^R$ $w^R$  
Inductive step: |x| ≤ n ⇒ $(wx)^R$ = $x^R$ $w^R$  
For |x| = n + 1
(x = ua) ∧ (|u| = n) ∧ (a ∈ Σ) ∧ ($x^r$ = a $u^r$)  
$(wx)^R$ = $(w(ua))^R$ = $((wu)a)^R$ = a($u^R$ $w^R$) = a $u^R$ $w^R$ = $x^R$ $w^R$

For example $(snow~ball)^R$ = $(ball)^R$ $(snow)^R$

$Σ^{+}$ denotes the set of non-empty strings over the Σ alphabet
1. a ∈ Σ ⇒ a ∈ $Σ^{+}$
2. (x ∈ $Σ^{+}$ ∧ a ∈ Σ) ⇒ ax ∈ $Σ^{+}$
3. $Σ^{+}$ doesn’t contain any elements other than the ones that can be constructed by pplying `1` and `2` finitely.

For example:  
Σ = {a,b} ⇒ $Σ^{+}$ = {a,b,aa,ba,ab,bb,aaa,aab,...}.

$Σ^{*}$ denotes the set of all strings over the Σ alphabet
1. λ ∈ $Σ^{*}$
2. x ∈ $Σ^{*}$ ∧ a ∈ Σ ⇒ ax ∈ $Σ^{*}$
3. $Σ^{*}$ doesn’t contain any elements other than the ones that can be constructed by pplying `1` and `2` finitely.

For example:  
Σ = {a,b} ⇒ $Σ^{*}$ = {λ,a,b,aa,ba,ab,bb,aaa,aab,...}.  
Σ = {0,1} ⇒ $Σ^{*}$ = {λ,0,1,00,01,10,11,000,001,...}.

Assuming (x ∈ $Σ^{*}$) ∧ (∀n ∈ N), a string’s $n^{th}$ power($x^n$) can be formally defined as:  
1. $x^0$ = λ
2. $x^{n+1}$ = $x^n$ · x = ($x^n$&x)

For example:  
Σ = {a,b}, x = ab
$x^0$ = λ, $x^1$ = ab, $x^2$ = abab, $x^3$ = ababab  
or { $a^n$ $b^n$ | n ≥ 0} defines the set: {λ,ab,aabb,aaabbb,...}

Let Σ be a finite alphabet.
A language over Σ is a subset of $Σ^{*}$.

The rules of choosing a subset from $Σ^{*}$ can be performed by using a grammar.

For example:  
{ $a^m$ $b^n$ | m,n ∈ N} is a language defined over {a,b}.

This language cannot contain any other symbols than a and b.

In this language b always succeeds a. For instance ba doesn’t belong to this language.

#### Multiplication of Languages

Let A and B be languages defined over Σ. Cartesian product A × B produces a new language.  
AB = {xy | x ∈ A ∧ y ∈ B}  
AB = {z | z = xy ∧ x ∈ A ∧ y ∈ B}

For example:  
Let Σ = {a,b} be the alphabet  
Let A = {λ,a,ab} and B = {a,bb} be the languages  
AB ={a,bb,aa,abb,aba,abbb}  
BA ={a,aa,aab,bb,bba,bbab}  
AB ≠ BA