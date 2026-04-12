# Recognizability and Decidability

## What Can We Do With a TM?

- Last time, we saw TMs that
  - check if a string is an even length,
  - check if a string is a palindrome,
  - flip the a’s and b’s; b’s and a’s (i.e., writes b in place of a ; a in place of b)
- Here’s a list of some other things TMs can do:
  - Check if a number is a Fibonacci number.
  - Convert the number n into a string of n a’s.
  - Check if a string is a tautonym (the same string repeated twice).
  - So much more!
- This hints at the idea that TMs might be more powerful than they look.

## Recap:

Classical automata (a.k.a. language recognizers(DFA,NFA,PDA)) sometimes is incapable of recognizing very simple language(e.g. $a^nb^nc^n : n ≥ 0$).  
There exists more general language recognizers which perform transformation between chains of tokens. Turing machine is an example to this kind of language recognizers.

#### Church-Turing Thesis

In computability theory, the Church-Turing thesis is a combined hypothesis about the nature of functions whose values are effectively calculable; or, in more modern terms, functions whose values are algorithmically computable. In simple terms, the Church-Turing thesis states that a function is algorithmically computable if and only if it is computable by a Turing machine.  
Informally the Church-Turing thesis states that if some method (algorithm) exists to carry out a calculation, then the same calculation can also be carried out by a Turing machine (as well as by a recursively definable function, and by a λ-function).

## Real and “Ideal” Computers

- A real computer has finite memory: finite disk space, finite RAM, etc.
- But as computers get more powerful, the amount of memory available keeps increasing.
  - Compare our first PCs to your laptops!
- An <span style="color: #87CEFA;font-style: italic;">idealized computer</span> is a computer with unlimited RAM and disk space.
- It functions just like a regular computer, but never runs out of memory.

## Church-Turing Thesis in Simple Words

<span style="color: #87CEFA;font-style: italic;">Hypothesis:</span> Turing machines are equal in power to idealized computers.

More specifically: any computation that can be done on a TM can be done on an idealized
computer and vice-versa.

- Programming languages provide a set of simple constructs.
  - Think things like variables, arrays, loops, functions, classes, etc.
- You, the programmer, then combine these basic constructs together to assemble larger
programs.
- <span style="color: #87CEFA;font-style: italic;">Key Idea:</span> A TM is powerful enough to simulate each of these individual pieces. It’s
therefore powerful enough to simulate anything a real computer can do.
- The resulting TM might be colossal, slow, or both, but it would still faithfully simulate the computer

## Example- The Computer View

A is a list of binary strings (made of 0s and 1s), separated by symbols, where no two strings
are the same.

```
for each string x1 do
  for each string x2 to the right of x1 do
    Compare x1 and x2
      if x1 = x2 then
        REJECT
      end if
    end for
  end for
ACCEPT
```

```python
for i in range(len(A)):    
  for j in range(i + 1, len(A)):  
    if A[i] == A[j]:
      return "REJECT"
return "ACCEPT"
```

M decides $A = \{ {\\\#}x1{\\\#}x2{\\\#}...{\\\#}x\ |\ \text{ each } x_i ∈ \{0,1\}^{\ast} \text{ and } x_i ≠ x_j \text{ for each } i ≠ j \}$

For string w
1. Place a mark on top of the leftmost tape symbol. If that symbol was a blank, accept. If that symbol was a #, continue with the next step. Otherwise, reject.
2. Scan right to the next # and place a second mark on top of it. If no # is encountered before a blank symbol, only x1 was present, so accept
3. By zig-zagging, compare the two strings to the right of the marked #s. If they are equal, reject.
4. Move the rightmost of the two marks to the next # symbol to the right. If no # symbol is encountered before a blank symbol, move the leftmost mark to the next # to its right and the rightmost mark to the # after that. This time, if no # is available for the rightmost mark, all the strings have been compared, so accept.
5. Go to step 3.

## Other Data Types

- “cat pictures?”
  - Sure! A picture is just a 2D array of colors, and a color can be represented as a series of numbers.
- “cat videos?”
  - If you think about it, a video is just a series of pictures!
- “music?”
  - Sure! Music is encoded as a compressed waveform. That’s just a list of numbers.
- “Deep Learning or Generative AI?”
  - Sure! That’s just applying a bunch of matrices and nonlinear functions to some input.

<br>
<center style="font-size: 1.5em;>The <span style="color: #87CEFA; font-style: italic;">Church-Turing Thesis<span> claims that</center>
<br>
<div style="font-size: 1.5em; color: #F08080; font-style: italic;">
<center>every feasible method of computation</center>
<center>is either equivalent to or weaker than</center>
<center>a Turing machine.</center>
</div>
<br>
<br>
<div style="font-size: 1.5em;">
<center>“This is not a theorem– it is a falsifiable scientific hypothesis.</center>
<center>And it has been thoroughly tested!”</center>
<center>—Ryan Williams</center>
</div>
<br>

---

<br>
<center style="font-size: 2em; color: #87CEFA;">Recognizability and Decidability</center>
<div style="font-size: 1.5em;">
<br>
<center>
What problems can we solve with a computer?
</center>
<center style="color: #87CEFA; font-style: italic;">
What does it mean to “solve” a problem?
</center>
</div>
<br>

## The Hailstone Sequence

- Consider the following procedure, starting with some $n ∈ N$, where $n > 0$:
  - If n = 1, you are done.
  - If n is even, set $n = n/2$.
  - Otherwise, set $n = 3n + 1$.
  - Repeat.
- Question: Given a natural number n > 0, does this process terminate?

<br>
<center style="font-size: 2em;">
Does this <strong>ALWAYS</strong> eventually reach 1, for <strong>EVERY</strong> number?
</center>
<center style="font-size: 2em; color: #87CEFA;">
Nobody knows!
</center>
<br>
<center style="font-size: 1.5em;">
The conjecture (unproven claim) that the Hailstone Sequence always terminates is called the Collatz Conjecture and has been unsolved since 
<br>1937!
</center>
<br>


## The Hailstone Turing Machine

Let’s represent the problem with TM.  
Remember: *any algorithm can be simulated by a Turing machine*.
- Let $Σ = \{a\}$ and consider the language  
$L = \{a^n\ |\ n > 0 \text{ and the hailstone sequence terminates for } n\}$.
- We can build a TM for L as follows:
  - If the input is $λ$, reject.
  - While the string is not $a$:
    - If the input has even length, halve the length of the string.
    - If the input has odd length, triple the length of the string and append a $a$.
  - Accept.

Tracing an Example $(n = 3)$  
**Hailstone Sequence:** 

$3 → 10 → 5 → 16 → 8 → 4 → 2 → 1$

Hailstone TM on tape:  
Start: aaa (length = 3, odd)  
Step 1: aaaaaaaaaa (length = 3·3+1=10, even)  
Step 2: aaaaa (length = 10/2=5, odd)  
Step 3: aaaaaaaaaaaaaaaa (length = 5·3+1=16, even)  
Step 4: aaaaaaaa (length = 16/2=8, even)  
Step 5: aaaa (length = 8/2=4, even)  
Step 6: aa (length = 4/2=2, even)  
Step 7: a (length = 2/2=1)  
⇒ String is “a” ⇒ EXIT loop ⇒ ACCEPT

## Important Terminology

Before diving into details on recognizability and decidability, let’s clarify some very important terminology:
- Let M be a Turing machine and w be a string.
- M accepts w if it returns true on w.
- M rejects w if it returns false on w.
- M loops on w (or loops infinitely) if when run on w it neither returns true nor returns false.
- M does not accept w if it either rejects w or loops on w.
- M does not reject w if it either accepts w or loops on w.
- M halts on w if it accepts w or rejects w.

## Recognizability and Decidability

When we start a Turing machine on an input it may *accepts*, *reject*, or *loop*. Looping may entail any simple or complex behavior that never leads to a halting state.

#### Definition

A language is Turing-recognizable if some Turing machine is able accepts the words in a language.

#### Definition

A language is Turing-decidable or simply decidable if some Turing machine is able to decide it. 
Turing machines that halt on all inputs and never loop are called deciders because they always make a decision to accepts or reject.

#### Definition

A TM M is a recognizer for a language L over alphabet Σ when:

$$
∀ω ∈ Σ^{\ast}, M(ω) = \begin{cases}
Ⓨ \hspace{10em}\text{ if } ω ∈ L \\
\text{loops forever or rejects} \hspace{1.3em}\text{ if } ω ∉ L
\end{cases}
$$

That is: M accepts every string in L, and does not accept any string outside L (it may *reject* or *loop* on those strings).

Definition

A language L is **Turing-recognizable** (also called **recursively enumerable** language, written **RE**) 
if there exists a Turing machine that is a recognizer for L.

## Recognizers and Recognizability- An Example

Recap: The Hailstone Turing Machine

- Let $Σ = \{a\}$ and consider the language  
$L = \{a^n\ |\ n > 0 \text{ and the hailstone sequence terminates for } n\}$.
- We can build a TM for L as follows:
  - If the input is $λ$, reject.
  - While the string is not $a$:
    - If the input has even length, halve the length of the string.
    - If the input has odd length, triple the length of the string and append a $a$.
  - Accept.


<div style="font-size: 1.5em;">
<br>
<center>
What problems can we <strong>solve</strong> with a computer?
</center>
<center style="color: #87CEFA; font-style: italic;">
What does it mean to “solve” a problem?
</center>
</div>
<br>
<center style="font-size: 1.15em;">
You can think of RE as “all problems with yes/no answers where yes answers can be confirmed by a
computer.” → Does it sound like a solving problem? Well, maybe ... partially. ”
</center>
<br>
<center style="font-size: 1.5em; color: #87CEFA; font-weight: bold">
Is there a more“complete” way of solving a problem??
</center>
<br>

## Deciders and Decidability

#### Definition

A language is Turing-decidable or simply decidable if some Turing machine is able to decide it.
Turing machines that halt on all inputs and never loop are called deciders because they always
make a decision to **accepts** or **reject**.

#### Definition

A TM M is a decider for a language L over alphabet Σ when:

$$
∀ω ∈ Σ^{\ast}, \hspace{1em} M(ω) = \begin{cases}
Ⓨ ⇒ ω ∈ L \\
Ⓝ ⇒ ω ∉ L
\end{cases}
$$

- The machine gives a definitive YES or NO for every input.
- It **never loops forever** — it always terminates.
- This is what we think of as a **fully solvable** decision problem, i.e., a more “complete” way of solving a problem.

## Definition

A language L is Turing-decidable (also called recursive language, written R) if there exists a
Turing machine that is a recognizer for L.

## Deciders and Decidability- An Example

$L = \{ω ∈ {Σ_0}^{\ast}|\ |ω|even\ number\}$  
$Σ_0 = \{a\}$  
$S = \{q_0,...,q_6\}$  
$Σ = \{a,Ⓨ,Ⓝ,{\\\#}\}$  
$s_0 = q_0$

| q     | σ  | $δ(q,σ)$       |
|-------|----|----------------|
| $q_0$ | #  | $(q_1,L)$      |
| $q_1$ | a  | $(q_2,{\\\#})$ |
| $q_1$ | #  | $(q_4,R)$      |
| $q_2$ | #  | $(q_3,L)$      |
| $q_3$ | a  | $(q_0,{\\\#})$ |
| $q_3$ | #  | $(q_6,R)$      |
| $q_4$ | #  | $(q_5,Ⓨ)$     |
| $q_5$ | Ⓨ | $(h,R)$        |
| $q_5$ | Ⓝ | $(h,R)$        |
| $q_6$ | #  | $(q_5,Ⓝ)$     |

## More on Decidability

**Examples:**

Is this graph connected? <span style="color: #87CEFA;font-style: italic;">decidable by BFS/DFS</span>  
Is this matrix singular? <span style="color: #87CEFA;font-style: italic;">decidable by computing determinant or row reduction.</span>  
Is this proposition satisfiable? <span style="color: #87CEFA;font-style: italic;">decidable, because there are finitely many truth assignments. 
it may be hard, but still decidable.</span>

Given a problem, the answer is “Yes” or “No”?

A language is the set of inputs with the desired property.  
So we can equivalently ask “Is this instance in the language?”  
We use “problem” informally, to denote “language”.  

**Examples:**

Is this graph connected? <span style="color: #87CEFA;font-style: italic;">decidable by BFS/DFS</span>  

$L_{conn} = \{ \langle G \rangle\ |\ G$ is a connected graph $\}$

Is this matrix singular? <span style="color: #87CEFA;font-style: italic;">decidable by computing determinant or row reduction.</span>  

$L_{sing} = \{ M |\ M$ is a square matrix over $Z$ and $det(M) = 0 \}$

Is this proposition satisfiable? 
<span style="color: #87CEFA;font-style: italic;">
decidable, because there are finitely many truth assignments. it may be hard, but still decidable.
</span>

$L_{SAT} = \{ \langle ϕ \rangle\ |\ ϕ$ is satisfiable $\}$

## Revisit

#### Definition (The Acceptance Problem)

Testing whether a particular deterministic finite automaton accepts a given string can be
expressed as a language, $A_{DFA}$. This language contains the encodings of all DFAs together
with strings that the DFAs accept.

$A_{DFA} = \{ \langle B,ω \rangle\ |\ B$ is a DFA that accepts input string $ω\}$

<span style="color: #87CEFA;font-style: italic;">
Collect every possible DFA, pair it with every possible string, and keep exactly the pairs where the DFA says accept.
</span>

Suppose B is a DFA over {0,1} that accepts strings ending in 1. Then:
- $\langle B,101 \rangle ∈ A_{DFA}$ because B accepts 101.
- $\langle B,100 \rangle ∈ A_{DFA}$ because B rejects 100.

#### Theorem

$A_{DFA}$ is a decidable language

#### Proof.

M = On input $\langle B,ω \rangle$, where B is a DFA and ω is a string:
1. Simulate B on input ω
2. If the simulation ends in an accept state, accept. If it ends in a non-accepting state, reject.

## Revisit:

$A_{NFA} = \{ \langle B,ω \rangle\ |\ B$ is a NFA that accepts input string $ω\}$

#### Theorem

$A_{NFA}$ is a decidable language

#### Proof.

M = On input $\langle B,ω \rangle$, where B is a NFA and ω is a string:
1. Convert NFA B to an equivalent DFA C
2. Run TM M from previous slide on input $\langle C,ω \rangle$
3. If M accepts, accept; otherwise, reject.

## Revisit:

$A_{CFG} = \{ \langle G,ω \rangle\ |\ G$ is a CFG that generates string $ω\}$

#### Theorem

$A_{CFG}$ is a decidable language

#### Proof.

F = On input $\langle G,ω \rangle$, where G is a CFG and ω is a string:
1. Convert G to an equivalent grammar in Chomsky normal form.
2. List all derivations with 2n−1 steps, where n is the length of w; except if n = 0, then instead list all derivations with one step.
3. If any of these derivations generate w, accept; if not, reject.

## Is $A_{TM}$ a decidable language?

$A_{TM} = \{ \langle M,ω \rangle\ |\ M$ is a TM and M accepts $ω\}$

#### Theorem

$A_{TM}$ is a decidable language

#### Proof.

1. We assume $A_{TM}$ is decidable and obtain a contradiction. Let’s assume that H is a decider

$$
\text{for } A_{TM} \text{ where } H(\langle M,ω \rangle) = \begin{cases}
\text{accept} \hspace{1em}\text{if M accepts ω} \\
\text{reject} \hspace{1.4em}\text{if M does not accept ω}
\end{cases}
$$

2. Define a TM D where
$$
D(\langle M \rangle) = \begin{cases}
\text{accept} \hspace{1em}\text{if H rejects } \langle M,ω \rangle \\
\text{reject} \hspace{1.4em}\text{if H accepts } \langle M,ω \rangle
\end{cases}
$$

3. Feed D unto itself to obtain a contradiction
$$
D(\langle D \rangle) = \begin{cases}
\text{accept} \hspace{1em}\text{if D rejects } \langle D \rangle \\
\text{reject} \hspace{1.4em}\text{if D accepts } \langle D \rangle
\end{cases}
$$

## Recap

 Regular Languages ⊆ CFLs ⊆ Problems Solvable by TM ⊆ All Languages

## Chomsky Hierarchy revisited

| Type | Language Type<br>(Grammars)                 | Form of Productions<br>in Grammar              | Accepting<br>Device         |
|------|---------------------------------------------|------------------------------------------------|-----------------------------|
| 0    | Recursively<br>enumerable<br>(unrestricted) | $α → β$<br>$α,β ∈ (N ∪ Σ)^+$                   | Turing machine              |
| 1    | Context-sensitive                           | $α → β$<br>$α,β ∈ (N ∪ Σ)^{\ast}, \|α\|≤\|β\|$ | Linear-bounded<br>automaton |
| 2    | Context-free                                | $A → α$<br>$A ∈ N, α ∈ (N ∪ Σ)^{\ast}$         | Pushdown<br>automaton       |
| 3    | Regular                                     | $A → σB, A → σ$<br>$A,B ∈ N, σ ∈ Σ^{\ast}$     | Finite<br>automaton         |

## Context-Sensitive Grammars

#### Definition

A context-sensitive grammar (CSG) is an unrestricted grammar in which no production is length-decreasing.  
In other words, every production is of the form $α → β$, where $|β| ≥ |α|$

#### Definition

A linear-bounded automaton (LBA) is a 5-tuple that is identical to a nondeterministic Turing machine, with the following exception. 
There are two extra tape symbols: [ and ] wrapping the initial input string on the tape. 
During its computation, an LBA is not permitted to replace either of these brackets or to move its tape head to the left of the [ or to the right of the ].

#### Theorem

If $L ⊆ Σ^{\ast}$ is a context-sensitive language, then there is a linear-bounded automaton that
accepts L.

#### Theorem

If $L ⊆ Σ^{\ast}$ is accepted by a linear-bounded automaton M, then there is a context-sensitive
grammar G generating $L−\{Λ\}$.

#### Theorem

Every context-sensitive language L is recursive.

Regular languages (RL)  
⊆ Deterministic context free languages (DCFL)  
⊆ Context free languages (CFL)  
⊆ Context sensitive languages  
⊆ Recursive languages (R)  
⊆ Recursively enumerable languages (RE)  

## Unanswered Questions

- Why exactly is **RE** an interesting class of problems?
- What does the **R** $\stackrel{?}{=}$ **RE** question mean?
- Is **R** = **RE**?
- What lies beyond **R** and **RE**?

## Recap:

<div style="font-size: 1.5em;">
<br>
<center>
What problems can we <strong>solve</strong> with a computer?
</center>
<center style="color: #87CEFA; font-style: italic;">
What does it mean to “solve” a problem?
</center>
</div>
<br>
<center style="font-size: 1.15em;">
You can think of RE as “all problems with yes/no answers where yes answers can be confirmed by a
computer.” → Does it sound like a solving problem? Well, maybe ... partially. ”
</center>
<br>
<center style="font-size: 1.5em; color: #87CEFA; font-weight: bold">
Is there a more“complete” way of solving a problem??
</center>
<br>

## The Universal Turing Machine

#### Definition (Universal Turing Machine)

$U_{TM}$ = On input $\langle M,ω \rangle$, where M is a TM and ω is a string:
1. Simulate M on input ω.
2. If M ever enters its accept state, accept; if M ever enters its reject state, reject.

#### Definition (Universal Turing Machine)

- Theorem (Turing, 1936): There is a Turing machine $U_{TM}$ called the universal Turing
machine such that, when run on an input of the form $\langle M,w \rangle$, where M is a Turing
machine and w is a string, it simulates M running on w and does whatever M does on w
(accepts, rejects, or loops).

- The observable behavior of $U_{TM}$ is:
  - If M accepts w, then $U_{TM}$ accepts $\langle M,w \rangle$.
  - If M rejects w, then $U_{TM}$ rejects $\langle M,w \rangle$.
  - If M loops on w, then $U_{TM}$ loops on $\langle M,w \rangle$.

#### Key Idea

$U_{TM}$ does to $\langle M,w \rangle$ what M does to w.

One single TM ($U_{TM}$) can simulate ANY other TM. It is a programmable computer!

- Building out $U_{TM}$ is nontrivial, but the conceptual idea behind it isn’t too bad.
- Essentially:
  - $U_{TM}$ splits its tape into two regions: one holding the description of the TM to simulate, and one holding that TM’s tape contents.
  - $U_{TM}$ marks the position of the simulated tape head (e.g., with a special symbol).
  - $U_{TM}$ repeatedly consults the description of the simulated TM to determine the next action, then simulates that action.
  - If the simulated TM accepts or rejects, then $U_{TM}$ also accepts or rejects.

## $U_{TM}$ as a Recognizer - Revisited

- As a refresher, the language $A_{TM}$ is

$A_{TM} = \{ \langle M,ω \rangle\ |\ M$ is a TM and M accepts $ω\}$

- The universal TM $U_{TM}$ has the following behavior when given as input a TM M and a
string w:
  - If M accepts w, then $U_{TM}$ accepts $\langle M,w \rangle$.
  - If M rejects w, then $U_{TM}$ rejects $\langle M,w \rangle$.
  - If M loops on w, then $U_{TM}$ loops on $\langle M,w \rangle$.
- $U_{TM}$ is a recognizer for $A_{TM}, but because of that last case it’s not a decider for $A_{TM}.  
The proof on it will be skipped.

## What Does This Mean?

- In one fell swoop, we’ve proven:
  - $A_{TM}$ is <span style="color: #87CEFA; font-style: italic;">undecidable</span> — no general algorithm can determine whether a TM accepts a string.
  - **R** ≠ **RE** since $A_{TM} ∉ **R** but $A_{TM}$ ∈ **RE**.
- This implies: computers cannot, in general, answer all questions about program behavior.
- At a deeper level:
<center style="color: #87CEFA; font-style: italic;">
There is a gap between what is true and what we can discover is true.
</center>

- Given a TM M and input w, one is true:
<center style="color: #F08080; font-style: italic;">
M accepts w <span style="color: white;">&emsp;or&emsp;</span> M does not accept w
</center>
&emsp;&emsp;&emsp;but no algorithm can always decide which.

- Because **R** ≠ **RE**:
<center style="color: #87CEFA; font-style: italic;">
Solving a problem can be fundamentally harder than verifying a solution.
</center>

- Some problems allow:
  - verification of “yes” answers (recognizers),
  - but no general procedure to decide all cases (deciders).

## The Halting Problem

- The most famous undecidable problem is the halting problem, which asks:
<center style="color: #F08080;">
Given a TM M and a string w,
<br>
will M halt when run on w?
</center>

- Our goal is not to build a TM that halts on w, but to check whether an arbitrary TM M halts on an arbitrary input w.
- As a formal language:

$$
\color{F08080}
\text{HALT} = \{\langle M,w \rangle\ |\ M \text{ halts on } w \}
$$

- Theorem: HALT is recognizable, but undecidable.
  - There exists a recognizer for HALT.
  - There is no decider for HALT.

## So What?

- These problems might not seem all that exciting, so who cares if we can’t solve them?
- Turns out, this same line of reasoning can be used to show that some very important problems are impossible to solve.
- *Engineering Problem:* Design a diesel engine that doesn’t emit lots of NOx pollutants.
- *Regulatory Problem:* Design a testing procedure that, given a diesel engine, determines whether it emits lots of NOx pollutants.

Fact: Almost all “regulatory problems” about computer programs are undecidable. That is,
almost all problems of the form “does program X have behavior Y?” are undecidable.

This can be formalized as Rice’s Theorem.

- ”Does program X ever halt?”
- ”Does program X accept all strings?”
- ”Does program X print ’Hello’?”
- ”Does program X sort correctly?”
- ”Does program X ever reach line 42?”
- ”Does program X have an infinite loop?”
- ”Does program X accept any input at all?”

#### Theorem (Rice’s Theorem)

Any non-trivial property about what a Turing machine computes is undecidable.

**What is a “Property”?**

A property is just a YES/NO question about a language:

#### Property Definition

Property P is a function:  
P(M) = YES  &emsp;if TM M has this property  
P(M) = NO   &emsp;if TM M does not

#### Examples

P(M) = ‘‘Does L(M) contain the string ‘ab’?’’  
P(M) = ‘‘Is L(M) empty?’’  
P(M) = ‘‘Is $L(M) = Σ^{\ast}$?’’  
P(M) = ‘‘Does M accept at least one string?’’  

What exactly is the class **RE**?
- Recall that the class **RE** is the class of all recognizable languages:

$$
RE = \{ L\ | \text{ there exists a TM } M \text{ that recognizes } L \}
$$

- Since **R** ≠ **RE**, there is no general way to “solve” problems in **RE**, if by “solve” you mean:  
*make a computer program that can always tell you the correct answer.*
- So what exactly are the kinds of languages in RE?

A language L is in **RE** when, for any string w, if you’re convinced that $w ∈ L$, there’s a way to
prove that to someone else.

A language L is in RE if:
$$
w ∈ L ⇔ ∃ \text{ a finite certificate / checkable accepting computation}  
$$
(not necessarily in polynomial time, just in finite time)

## Verifiers

- A *verifier* for a language L is a TM V with the following properties:
<center style="color: #F08080; font-size: 1.15em;">
V halts on all inputs.
</center>

$$
\color{F08080}
∀w ∈ Σ^{\ast}.\quad (w ∈ L ⇔ ∃c ∈ Σ^{\ast} \text{ such that V accepts } \langle w,c \rangle)
$$

- Some notes about V:
  - If V accepts $\langle w,c \rangle$, then we are guaranteed w ∈L.
  - If V rejects $\langle w,c \rangle$, then either:
    - $w ∈ L$,but c is not a valid certificate, or
    - $w ∉ L$, so no certificate c will work.
    - The certificate c is existentially quantified. Any string $w ∈ L$ must have at least one c that causes V to accept, and possibly more.
    - Although V always halts, V isn’t a decider for L and isn’t a recognizer for L. (Do you see why?)
    - V just checks certificates — it does not decide membership in L.
    - In practice, c is often just auxiliary data that helps verify the claim.

## Deciders vs Verifiers vs Recognizers

#### Theorem

If L is a language, then there is a verifier for L if and only if L ∈ RE.

- Verifiers and recognizers give two different perspectives on the “proof” intuition for RE.
- A verifier V for L checks proofs that $w ∈ L$:
  - If $w ∈ L$, there exists a proof c such that V accepts $\langle w,c \rangle$.
  - If $w ∉ L$, then V never accepts any certificate for w.
- A recognizer R for L searches for a proof that w ∈ L:
  - If $w ∈ L$, then R eventually finds a proof and accepts.
  - If $w ∉ L$, then R never finds a proof and loops.
    - Or possibly finds evidence that w /∈L and rejects.

## Revisit:

DFA = NFA = Regex (RL)  
⊆ PDA  (CFL)  
⊆ Decider (R)  
⊆ Recognizer = Verifier (RE)  

## Finding Non-RE Languages

How?  
How do we PROVE that languages exist which no TM can even recognize?

## Countability

#### Set of even numbers

Let $\mathbb{N}$ be the set of natural numbers and let $\mathbb{E}$ be the set of even natural numbers. Georg
Cantor observed that two sets have the same size if we can define a correspondence (bijection)
between two sets.  
Considering $f(n) = 2n$ we can conclude that $\mathbb{N}$ and $\mathbb{E}$ are the same size.

#### Definition

A set A is countable if either it is finite or it has the same size as $N$

Examples: $\mathbb{N}, \mathbb{Z}, \mathbb{N} × \mathbb{N}, \mathbb{Q}, Σ^{\ast}$ (for any finite, nonempty alphabet Σ)

#### Set of rational numbers

Let $\mathbb{Q} = \{\frac{m}{n} | m,n ∈ \mathbb{N} \}$ be the set of positive rational numbers. To find a correspondence we
make an infinite matrix containing all the positive rational numbers as below.

## Diagonalization

#### Set of real numbers

Let $\mathbb{R}$ be the set of real numbers. Real numbers have decimal representations like
π =3.1415926... adn $\sqrt{2}$ = 1.4142135.... Cantor proved that R is uncountable by
introducing the diagonalization method.

#### Proof.

1. Suppose there is a bijection $f(n)$ between $\mathbb{N}$ and $\mathbb{R}$.
2. Construct a table between each natural number and rational number (can be in floating
point representation).
3. We construct a real number x by selecting each digit as follows
4. For each natural number i in the table change the $i^{th}$ digit in the real number to another
integer. Do not choose 9’s or 0’s.

We have just constructed a number x which differs from every number in the so called
bijection $f$. Contradiction.

#### Corollary

Some languages are not Turing-recognizable

#### Proof.

1. The set of all strings $Σ^{\ast}$ is countable for any alphabet $Σ$.
2. The set of all Turing machines is countable because each Turing machine M has an encoding into a string $\langle M \rangle$
3. The set of all languages $\mathbb{L}$ over alphabet $Σ$ is uncountable.
   1. The set of all infinite binary sequences($\mathbb{B}$) is uncountable (use diagonalization).
   2. Let $Σ^{\ast} = \{s_1,s_2,s_3,...\}$ Each language $A ∈ \mathbb{L}$ has a unique characteristic sequence in $\mathbb{B}$ where the $i^{th}$
bit of that sequence is 1 if $s_i ∈ A$.
   3. The function defined above is a bijection and hence $\mathbb{L}$ and $\mathbb{B}$ is correspondent. $\mathbb{L}$ is uncountable.
4. The set of all languages cannot be put into a correspondence with the set of all Turing machines. We
conclude that some languages are not recognized by any Turing machine

## What This Means?

- On a deeper philosophical level, the fact that non-RE languages exist supports the following claim:

<center style="color: #87CEFA; font-style: italic;">
There are statements that are true but not provable.
</center>

- This result can be formalized as a theorem called **Godel’s incompleteness theorem**, one of
the most important mathematical results of all time.
- On a more philosophical note, you could interpret the previous result in the following way:
<center style="color: #87CEFA;">
There are inherent limits about what mathematics can teach us.
</center>
&emsp;&emsp;&emsp;There’s no automatic way to do math. There are true statements that we can’t prove.

## Where We Stand

- We’ve just done a whirlwind tour of computability theory:
- <span style="color: #87CEFA; font-style: italic;">The Church-Turing thesis</span> tells us that TMs give us a mechanism for studying computation in the abstract.
- <span style="color: #87CEFA; font-style: italic;">Universal computers</span> — computers as we know them — are not just a stroke of luck. The existence of the universal TM ensures that such computers must exist.
- <span style="color: #87CEFA; font-style: italic;">Self-reference (i.e., the barber problem)</span> is an inherent consequence of computational power.
- <span style="color: #87CEFA; font-style: italic;">Undecidable problems</span> exist partially as a consequence of the above and indicate that there are statements whose truth can’t be determined by computational processes.
- <span style="color: #87CEFA; font-style: italic;">Unrecognizable problems</span> are out there and can be discovered via diagonalization. They imply there are limits to mathematical proof.

## Where We Stand- Computational Models

- Finite automata
- Pushdown automata
- Turing machines
- Church’s λ-calculus
- Any modern computer programming language
- Quantum computing

Exact choice of model is not crucial.  
The last four have similar computational power.

**The Church-Turing thesis:**
- The intuitive notion of an algorithm is captured by a Turing machine.
- Any conceivable computational process can be performed in a Turing machine.

## Next Lecture

*From computability to complexity*

- The class **R** represents problems that can be solved by a computer.
- The class **RE** represents problems where “yes” answers can be verified by a computer.
- The class **P** represents problems that can be solved *efficiently* by a computer.
- The class **NP** represents problems where “yes” answers can be verified *efficiently* by a computer.
- <span style="color: #87CEFA; font-style: italic;">Introduction to Complexity Theory</span>
  - Not all decidable problems are created equal!
- <span style="color: #87CEFA; font-style: italic;">The Classes P and NP</span>
  - Two fundamental and important complexity classes.
- <span style="color: #87CEFA; font-style: italic;">The P 
$\stackrel{?}{=}$ NP Question</span>
  - A literal million-dollar question!




