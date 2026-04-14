(1) You are asked to design a Turing decider that can decide the words of the language $a^nb^n \text{ where } n ≥ 1$. 
Your machine starts from the initial configuration: $(q_0,\underline{\\\#}w)$ where w is the input string. 
Your machine may read/write and move with a single transition.

(a) Design a Turing machine that performs the task defined above. 
Do not consider the performance of your machine. 
It is better if your machine is simple but not as performant as part (b) of this question

(b)  **Provide a pseudo-code** of a Turing machine’s algorithm that can perform the recognition in
$O(nlogn)$ steps. Show that your algorithm performs appropriate number of steps by annotating each step
with its Big-Oh complexity in the number of steps taken.

---

(2) Assume that disjoint languages $L_1$ and $L_2$ are defined over the same alphabet Σ and both of them are Turing recognizable but not Turing decidable. 
Explain, with a few sentences why the following is not possible:
$$
L_1 ∪ L_2 = Σ^{\ast}
$$

