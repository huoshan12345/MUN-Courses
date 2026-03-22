**(1)** Design a pushdown automaton (PDA) that recognizes the following language.

$L(G) = \lbrace a^kb^mc^n\ |\ k,m,n > 0$ and $k = 2m + n \rbrace$

---

**(2)** Is this grammar ambiguous? If so, prove it and construct a non-ambiguous grammar that derives the
same language.

$S → aS\ |\ aSbS\ |\ c$

---

**(3)** Provide Chomsky Normal Form for the following grammar

$S → ASA\ |\ aB$  
$A → B\ |\ S$  
$B → b\ |\ Λ$  

**Solution:**  
S symbol on the right hand side (RHS). Generate $S → S'$. (Ensure start symbol is not on the RHS.) New start symbol is S'.

$S → S$  
$S → ASA\ |\ aB$  
$A → B\ |\ S$  
$B → b\ |\ Λ$  

Since the start symbol must not appear on the right-hand side (RHS) during the CNF transformation, this step is performed first. The remaining steps then follow the standard algorithm discussed in the lecture.

---

**(4)** Prove or disprove that $L = L_1 − L_2$ is CFL. Design an automaton for L (it might be any automaton
according to the answer you found regarding L, i.e., NFA/DFA, PDA or Turing).

$L_1 = a+b+c$  
$L_2 = a^nb^{2n}c, n > 0$

Hint:  
What does it mean to remove L2 from L1?  
List a few example strings that are in L1 and ask yourself which ones get removed.  
Then think about the relationship between the number of a’s and b’s in the strings that get removed.  
Can you describe what’s “special” about those strings? The remaining strings can be split into two groups based on the count of a’s and b’s.  
What are those two groups? Recall the closure properties of CFLs.  
Is there a property that lets you combine two CFLs into one? 
