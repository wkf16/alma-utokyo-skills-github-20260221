# 2020 Summer Entrance Examination
## Department of Creative Informatics, The University of Tokyo

### INSTRUCTIONS
1. Do not open this booklet until the start of the examination is announced.
2. Write your examinee ID number below on this cover page.
3. Answer all three problems.
4. Three answer sheets are given. Use a separate answer sheet for each problem. You may write on the back of the sheet.
5. Write your examinee ID number and the problem number inside the top blanks of each sheet.
6. Do not bring the answer sheets or this booklet out of this room.

---

### Problem 1

Given a convex n-gon made by connecting a point sequence $v_0, ..., v_{n-1}, v_0$ in this order, a triangulation of the convex n-gon is a way of dividing its interior into triangles without overlap.

First, we count the number of triangulations of a convex n-gon. We denote the number as $C[n]$. For example, $C[4]=2$.

(1) Answer the values of $C[5]$, $C[6]$, and $C[7]$.

(2) Represent $C[n]$ as a function of $C[2], C[3], C[4], ..., C[n-1]$. We define $C[2]=1$ and $C[3]=1$.

(3) The following pseudo-code implements an algorithm for computing $C[n]$ for arbitrary $n$. Answer the code that fills [ (1) ]. Also answer the computational complexity (order) of the algorithm.

```
C[2] = 1; C[3] = 1;
for(i=4...n)
  C[i] = 0;
for(i=4...n)
  for(j=0...i-3)
    [     (1)      ]
return C[n];
```

Next, we find the triangulation of a convex n-gon with a minimum cost. Here, the cost of a triangulation is defined as the sum of the cost of triangles in the triangulation, and the cost of a triangle is defined as the sum of the cost of the edges composing the triangle. Assume that all $D[i,j]$ ($=D[j,i]$), the costs of the edges connecting an arbitrary pair of vertices ($v_i, v_j$) of the n-gon, are given.

(4) We consider solving the problem of finding a triangulation with a minimum cost by dividing the problem into subproblems. We denote $E[i,m]$ as the cost of triangulating a polygon made by a path starting from $v_i$, visiting $m$ vertices clockwise, and then coming back to $v_i$ (see the figure below). Assume that $E[i',m']$ are all given for $i'=0, ..., n-1$ and $m'=2, ..., m-1$. Represent $E[i, m]$ as a function of $E[i', m']$ and $D[i, j]$. We define $E[i, 2]=0$ ($i=0, ..., n-1$). Also draw a figure explaining the situation.

(Figure showing polygon vertices $v_i, v_{i+1}, ..., v_{i+m-1}$)

(5) Give approximately 10-line pseudo-code implementing an algorithm to compute the minimum cost of triangulating an arbitrary n-gon using the formula obtained in (4). Also answer the computational complexity (order) of the algorithm.

---

### Problem 2

Consider making a memory that can be accessed randomly, using D-FFs (Flip Flop) and 2:1 multiplexers. Assume that the D-FF is a circuit that stores 1 bit as shown in Fig. 1. A 1-bit signal given to $d$ is written to this circuit at the rise of the clock signal $clk$ and this circuit continues to output the written signal to $q$. As shown in Fig. 2, the 2:1 multiplexer is a circuit that selects one of the two input signals $a$ and $b$ according to the selection signal $s$ and outputs it to $c$.

(1) Give a truth table for the 2:1 multiplexer shown in Fig. 2. Assume that this multiplexer selects $a$ when $s$ is 0 and selects $b$ when $s$ is 1.

(2) Draw a circuit diagram of a memory that stores 4 bits and outputs 1 bit at the position specified by a 2-bit address according to the following instructions.
- Use only two kinds of components, which are the D-FF shown in Fig. 1 and the 2:1 multiplexer in Fig. 2.
- Ignore circuits related to clock and write (do not connect anything to $clk$ and $d$).
- Specify the address of data stored in each D-FF in the circuit diagram.
- Specify the lower bit of the 2-bit address signal wires as $addr\_low$ and the upper bit of it as $addr\_high$ in the circuit diagram.
- Specify the output wire of the memory as $output$ in the circuit diagram.

(3) In the similar way as in (2), consider a memory that stores $2^n$ bits and outputs 1 bit at the position specified by an $n$-bit address using the D-FF shown in Fig. 1 and the 2:1 multiplexer shown in Fig. 2. Give how many multiplexers you need to make this memory.

(4) The D-FF shown in Fig. 3 is a D-FF with write control. In this D-FF, the signal given to $d$ is written only when the input to the write enable signal $we$ is 1 at the rise of the clock signal $clk$. If $we$ is 0, a previously written signal continues to be output to $q$ without updating the stored contents. Give a circuit diagram of this D-FF in Fig. 3 using only the D-FF in Fig. 1 and the 2:1 multiplexer in Fig. 2. Assume that this multiplexer selects $a$ when $s$ is 0 and selects $b$ when $s$ is 1.

(5) Draw a circuit diagram of a memory that stores 4 bits according to the following instructions.
- Assume that, at the rise of the clock signal, 1 bit data is written at the position specified by a 2-bit address.
- Use only three kinds of components, which are the D-FF with write control shown in Fig. 3, the AND gate shown in Fig. 4, and the NOT gate shown in Fig. 5.
- You can use up to four AND gates and up to two NOT gates.
- Ignore circuits related to clock and output (do not connect anything to $clk$ and $q$).
- Specify the address of data stored in each D-FF in the circuit diagram.
- Specify the lower bit of the 2-bit address signal wires as $addr\_low$ and the upper bit of it as $addr\_high$ in the circuit diagram.
- Specify the data input wire of the memory as $input$ in the circuit diagram.

(Figures 1-5 showing D-FF, Multiplexer, D-FF with write control, AND gate, NOT gate)

---

### Problem 3

Select four items out of the following eight items concerning information systems, and explain each item in approximately from four to eight lines of text. If necessary, use examples, figures or equations.

(1) Semaphore
(2) A* search algorithm
(3) FPGA
(4) Buffer overflow
(5) LR parsing
(6) IPv4 and IPv6
(7) Stepping motor
(8) Perceptron
