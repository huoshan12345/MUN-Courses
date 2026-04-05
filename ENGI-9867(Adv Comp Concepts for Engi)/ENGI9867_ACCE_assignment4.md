**(1)** Design a Turing machine that finds the modulo 3 equivalent of a given number represented using I’s where the I count indicates the number. Initially the tape head will be on the blank symbol (#) before the number. At the end of execution, the machine will append I’s to the number to represent the result. The following example shows the initial and final configurations for 5 ≡ 2 (mod 3).

$\underline{\\\#}IIIII{\\\#} \ {⊢_M}^{\ast}\ {\\\#}IIIII\ II\underline{\\\#}$

Provide the state transition diagram for this Turing machine, along with the configuration corresponding to a sample input.

---

**(2)** Design a Deterministic Turing Machine that deletes the 0s from a given binary string. Binary string will start after the first blank (#) and initially, the tape head is over the first blank after the input (underlined symbol shows tape head position). Write your TM as a **state diagram**. Consider the following examples carefully. You may use additional symbols if necessary.

$\#0011001010111011\underline{\\\#}\ {⊢_M}^{\ast}\ {\\\#}111111111\underline{\\\#}$

$\#0010010\underline{\\\#}\ {⊢_M}^{\ast}\ {\\\#}11\underline{\\\#}$

$\#0000000\underline{\\\#}\ {⊢_M}^{\ast}\ {\\\#}\underline{\\\#}$

---

**(3)** Consider the following task definition:

A random string is provided on a tape that contains a’s and b’s in a random order, such as $\underline{\\\#}abbbaaab...\#$. A machine should reorder the characters in the given string where a’s always come before b’s. Thus, the final state of the tape will be as $\underline{\\\#}aaaa...bbbb...\#$ where number of a’s and b’s remain the same.

Although there exist different algorithms/solutions that can be implemented for the task, please **use the flow in the provided pseudocode** below to accomplish the described task.

Design a Turing machine, provide its control machine state-transition diagram and clearly explain the states, transition and other important parts of the design you have provided.

```
func main:
  if a:
    skip and move to next char;
  endif;
  if b:
    call lookForA_Swap
  endif;

func lookForA_Swap:
  mark the corresponding b;
  look for the nearest a on right;
  if a found:
    overwrite a;
    go back to marked b and overwrite;
    call main
  endif;
  if a not found:
    unmark b
    terminate
  endif;
```

---

**(4)** Design and sketch the state transition diagram of a Turing Machine that can perform 2’s complement operation on a given binary string as an input (if you are not familiar with the 2’s complement operation, please review it beforehand.). A possible way to take 2’s complement of a binary number is to take 1’s complement first (transform each 1 to 0 and each 0 to 1) and then add 1 to the resulting number. You can see how the machine works from the following examples. As you can see from the examples, initially the tape head is on the first blank after the input. You can assume that input will never be an empty string. The output will be overwritten. (Underlined symbol represents the position of the tape head.)

$\#001110110\underline{\\\#}\ {⊢_M}^{\ast}\ \#110001010\underline{\\\#}$

$\#1111\underline{\\\#}\ {⊢_M}^{\ast}\ \#0001\underline{\\\#}$

$\#000\underline{\\\#}\ {⊢_M}^{\ast}\ \#000\underline{\\\#}$

