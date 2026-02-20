**(1)** Considerthelanguage L defined below.

$L = \{a^nb^m\ |\ n + m ≡ 1\ (mod\ 2)\ and\ n,m ≥ 0\}$

Draw the deterministic finite automaton (DFA) that accepts L as a state transition diagram.

---

**(2)** You have discovered a new type of restriction enzyme called *Formalase* that cuts DNA at specific recognition sequences. When your enzyme encounters a DNA sequence that starts with a “T” and ends with a “G”, with an odd number of “A”s and an even number of “C”s (including zero), it cuts the DNA at specific positions, resulting in two fragments of DNA with “sticky ends” that can be used in molecular biology techniques such as cloning, PCR, and DNA sequencing.

However, further laboratory analysis has revealed an important structural constraint: the “C” nucleotides in the recognition site must appear in consecutive pairs. That is, every group of consecutive C’s in the sequence must contain an even number of C’s (e.g., CC, CCCC, etc.). A group containing an odd number of consecutive C’s (such as a single isolated “C” or “CCC”) will not be recognized by the enzyme, even though the total number of C’s in the sequence may still be even.

To model the behaviour of Formalase, create a Deterministic Finite Automaton (DFA) **by drawing a state transition diagram and table**. Keep in mind that a DNA sequence consists of A, T, G, and C. Possible acceptable strings include TAG, TACCG, TCCACCG, TCCACCCCG, etc. However, strings such as TCACACCG or TCAACCG are not accepted.

---

**(3)** Consider the following scenario in the context of formal verification:

A legacy authentication system uses a pattern-matching mechanism that accepts input strings over the alphabet $Σ = \{x,y\}$. The system’s specification was originally documented as a nondeterministic finite automaton (NFA), which was sufficient for theoretical analysis of the accepted language.

However, the system is now being integrated into a safety-critical environment where runtime verification must occur in real-time with O(n) complexity and constant space per input symbol. The verification module can only perform a single left-to-right scan of the input without backtracking or parallel state exploration. This operational constraint necessitates a deterministic implementation.

The original NFA specification is provided below:

$(q_0, x) → q_1$  
$(q_0, x) → q_2$  
$(q_0, y) → q_0$  
$(q_1, x) → q_3$  
$(q_1, y) → q_2$  
$(q_2, λ) → q_4$  
$(q_3, x) → q_2$  
$(q_4, x) → q_4$  
$(q_4, y) → q_5$  
$(q_4, λ) → q_0$  
$(q_5, λ) → q_3$  
start: $q_0$  
final: $q_5$  

(a) Apply the subset construction algorithm to derive an equivalent DFA. Document each step of
the construction, including the handling of any ε-closures. Present the complete transition function δ for the resulting DFA, then draw the state transition diagram of the DFA.

(b) Analyze the state complexity of your resulting DFA. Is the exponential blowup observed in this
case? Justify your answer.

---

**(4)** Your computer got attacked by Petya ransomware, which is a type of ransomware that encrypts files in your computer and overwrites the master boot record (MBR) of your computer, making it unable to boot. A security researcher discovered that the malware accepts a specific pattern of inputs to unlock files. The pattern is described by the following DFA. Derive the regular expression **systematically** to determine valid unlock sequences and recover your files on your computer.

$(q_0, a) → q_1$   
$(q_0, b) → q_3$   
$(q_1, a) → q_2$   
$(q_1, b) → q_1$   
$(q_2, a) → q_0$   
$(q_2, b) → q_2$   
$(q_3, a) → q_3$   
$(q_3, b) → q_3$  
start: q0  
final: q3  

---

**(5)** Consider the following rules regarding the words in a language L  
L contains words of the form a+b+c+d+ and each word in L either

- has many a’s as b’s and as many c’s as d’s, or
- has many a’s as d’s and as many b’s as c’s

Answer the following questions regarding L

(a) Provide a context free grammar G for L **in BNF notation**.

(b) Show that G is ambiguous by providing two different derivations for the word aabbccdd

(c) What form must a string have to satisfy both conditions of L at the same time? Express this as a pattern and explain why its existence makes L inherently ambiguous, i.e., provide a simple basic expression where the productions of the expression is the main reason why this language is inherently ambiguous.