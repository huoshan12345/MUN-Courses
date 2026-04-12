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

M decides $A = \{{\\\#}x1{\\\#}x2{\\\#}...{\\\#}x$ | each $x_i ∈ \{0,1\}^{\ast}$ and $x_i ≠ x_j$ for each $i ≠ j \}$

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
$L = \{a^n\ |\ n > 0$ and the hailstone sequence terminates for $n\}$.
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


