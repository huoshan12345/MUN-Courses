#### 1 For each statement, circle **True** or **False**.  

(a) Every Turing-decidable language is also Turing-recognizable.

(b) If a Turing machine M does not accept a string w, then M must reject w.

(c) The set of all Turing machines is uncountable.

(d) A verifier for a language L is a decider for L.

(e) The language $A_{TM}$ is Turing-recognizable but not Turing-decidable.

(f) Every context-sensitive language is recursive (decidable).

(g) The Church–Turing thesis is a mathematically proven theorem.

---

#### 2 Complete each statement.

(a) A Turing machine that halts on all inputs and never loops is called a \_\_\_\_.

(b) A language is Turing-recognizable if and only if it has a \_\_\_\_.

(c) The language $HALT = \lbrace \langle M,w \rangle\ |\ M \text{ halts on } w \rbrace \text{ is \\\_\\\_ but \\\_\\\_}$ .

(d) The set of all languages over an alphabet Σ is \_\_\_\_(countable/uncountable),
while the set of all Turing machines is \_\_\_\_(countable/uncountable). 

(e) A linear-bounded automaton is a nondeterministic Turing machine whose tape head is restricted to the
portion of the tape containing the \_\_\_\_.

---

#### 3 Circle the single best answer.

(1) Which of the following best describes the relationship between R and RE?  
(a) R = RE  
(b) R ⊂ RE  
(c) RE ⊂ R  
(d) R and RE are incomparable

(2) Which of the following languages is decidable?  
(a) $A_{TM} = \lbrace \langle M,w \rangle\ | \text{ M is a TM and M accepts } w \rbrace$  
(b) $HALT = \lbrace \langle M,w \rangle\ |\ M \text{ halts on } w \rbrace $  
(c) $A_{DFA} = \lbrace \langle B,w \rangle\ | \text{ B is a DFA and M accepts } w \rbrace$  
(d) None of the above  

(3) A recognizer for language L:  
(a) Always halts on every input  
(b) Accepts every string in L and may loop on strings not in L  
(c) Rejects every string not in L  
(d) Is the same as a decider for L  

(4) According to the Chomsky hierarchy, which class of languages is recognized by linear-bounded automata?  
(a) Regular languages  
(b) Context-free languages  
(c) Context-sensitive languages  
(d) Recursively enumerable languages  

(5) Which of the following is **NOT** undecidable by Rice’s Theorem?  
(a) “Does L(M) contain the string ‘ab’?”  
(b) “Is L(M) empty?”  
(c) “Does M have exactly 5 states?”  
(d) “Is $L(M) = Σ^{\ast}$?”  

---

#### 4 Answer each question thoroughly. Show your reasoning.

(1) Explain the difference between a recognizer and a decider. Use the Hailstone Turing Machine as an example
to illustrate why this distinction matters.

(2) The universal Turing machine UTM recognizes ATM but does not decide it. Explain why UTM fails to be a
decider for ATM. What specifically prevents it from deciding?

(3) As you may remember from our class, the Barber Paradox states: “In a village, the barber shaves everyone
who does not shave themselves, and only those people.” The paradox asks: who shaves the barber?  
(a) Explain the contradiction that arises in the Barber Paradox.  
(b) The proof that ATM is undecidable uses a similar self-referential argument. Explain how the construction
of TM D in that proof mirrors the Barber Paradox, and describe the contradiction that arises.

(4) Explain in your own words why the existence of non-RE languages implies that there are inherent limits to
what mathematics can prove.

---

5 Design a Turing machine that can decide if a string belongs to the language represented by regular expression
ab∗a. In the initial configuration of the machine, there is a single blank character at the leftmost side, and the
string of a’s and b’s are placed afterwards, followed by blank symbols. The R/W head is placed on the leftmost
blank symbol after the string. After the machine halts there is going to be a single Ⓨ/Ⓝ symbol following the
leftmost blank and trailing blanks afterwards. Some example computations can be given as:

(a) ${\\\#}abbba{\\\#} \ {⊢_M}^{\ast}\ {\\\#}Ⓨ$  
(b) ${\\\#}aa{\\\#} \ {⊢_M}^{\ast}\ {\\\#}Ⓨ$  
(c) ${\\\#}abbab{\\\#} \ {⊢_M}^{\ast}\ {\\\#}Ⓝ$  

Considering the information above provide the control machine and transition function of the Turing machine
specified. You may use additional symbols such as α in your function.













