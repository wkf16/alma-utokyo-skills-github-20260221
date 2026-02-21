# 2022 Summer Entrance Examination
## Department of Creative Informatics, The University of Tokyo

### INSTRUCTIONS
1. Do not open this booklet until the start of the examination is announced.
2. Write your examinee ID number below on this cover page.
3. You may write on the back of the answer sheet.
4. Write your examinee ID number and the problem number inside the top blanks of each sheet.
5. Do not bring the answer sheet or this booklet out of this room.

---

### Problem 1

Let $n$ and $r$ be positive integers. For $i = 1, 2, ..., n$, let $f_i$ be a univariate real-valued function defined in the integer domain and let $f_i(x_i)$ be $-\infty$ for negative integer $x_i$. Any non-negative integer solution $(x_1, ..., x_n)$ that satisfies $\sum_{i=1}^n x_i = r$ is called a feasible solution. In addition, a feasible solution that maximizes the objective function $\sum_{i=1}^n f_i(x_i)$ is called an optimal solution and the objective function value at the solution is called the optimal value. This problem is expressed as follows.

$$
(P) \quad \begin{array}{ll}
\text{Maximize} & \sum_{i=1}^n f_i(x_i) \\
\text{subject to} & \sum_{i=1}^n x_i = r \\
& x_i \text{ is a non-negative integer, } i = 1, ..., n
\end{array}
$$

(1) For $i = 1, 2, ..., n$ and non-negative integer $\alpha$, define the function $d_i(\alpha) := f_i(\alpha) - f_i(\alpha - 1)$ and assume that $d_i(\alpha)$ is non-increasing in terms of $\alpha$. Apply the following greedy algorithm $\mathcal{A}_G$ to $(P)$.

> **Step 0:** For $i = 1, 2, ..., n$, set $x_i \leftarrow 0$.
>
> **Step 1:** Repeat the following procedure for $r$ times: Let $\gamma$ be any index $i$ that maximizes $d_i(x_i + 1)$ among $i = 1, 2, ..., n$, and set $x_\gamma \leftarrow x_\gamma + 1$.

Answer the following questions.

(1-1) Let $r = 5, n = 3$, and let $f_1, f_2, f_3$ take the following values. Notice that $d_1, d_2, d_3$ are non-increasing. Answer the solution obtained by the greedy algorithm $\mathcal{A}_G$.

| $\alpha$ | 0 | 1 | 2 | 3 | ... |
| :--- | :--- | :--- | :--- | :--- | :--- |
| $f_1(\alpha)$ | 0 | 0 | -8 | -24 | ... |
| $f_2(\alpha)$ | -2 | 1 | -14 | -40 | ... |
| $f_3(\alpha)$ | 0 | -3 | -12 | -22 | ... |

(1-2) Let $(x_1^*, x_2^*, ..., x_n^*)$ be a feasible solution. Show that it is an optimal solution of $(P)$ if and only if the following condition holds.
$$ \max_{i=1,2,...,n} d_i(x_i^* + 1) \le \min_{i=1,2,...,n} d_i(x_i^*) $$

(1-3) Show that the greedy algorithm $\mathcal{A}_G$ outputs an optimal solution of $(P)$.

(2) Unless the non-increasing assumption of (1) holds, the greedy algorithm $\mathcal{A}_G$ does not always output an optimal solution of $(P)$. To apply dynamic programming, we consider the following problem $(P_N^R)$ in which $n$ and $r$ in $(P)$ are replaced with $N \in \{1, 2, ..., n\}$ and $R \in \{0, 1, ..., r\}$, respectively.

$$
(P_N^R) \quad \begin{array}{ll}
\text{Maximize} & \sum_{i=1}^N f_i(x_i) \\
\text{subject to} & \sum_{i=1}^N x_i = R \\
& x_i \text{ is a non-negative integer, } i = 1, ..., N
\end{array}
$$

The optimal value of the problem is denoted by $g_N(R)$. Answer the following questions.

(2-1) Express $g_N(R)$ only with $g_{N-1}(c)$ and $f_N(c)$ for any non-negative integer $c$ in the case of $N \ge 2$.

(2-2) Write a pseudo-code of a dynamic programming algorithm within 15 lines to output the optimal value $g_n(r)$ of $(P)$. Hereafter, this algorithm is called $\mathcal{A}_D$.

(2-3) Show that the optimal value of $(P)$ is obtained by the dynamic programming algorithm $\mathcal{A}_D$.

(2-4) Answer the computational complexity of the dynamic programming algorithm $\mathcal{A}_D$ and the computational complexity of the greedy algorithm $\mathcal{A}_G$. Ignore the computational cost of calculating $f_1, ..., f_n$.

---

### Problem 2

Consider packet transfer between the computers shown in the figure.

(Figure showing Client nodes, Router 1, Router 2, Server node with delays and bandwidths)
Delay $D_1 = 0.1 \text{msec}$, Bandwidth $B_1 = 1 \text{Gbits/sec}$
Delay $D_2$, Bandwidth $B_2$ (between Router 1 and Router 2)
Delay $D_3 = 0.1 \text{msec}$, Bandwidth $B_3 = 1 \text{Gbits/sec}$

First, we upload a very large file from a client node to the server node. Packets are not discarded in the communication links and routers on the packet transmission path. The server node checks whether the data in the received packet sent from the client node has a bit error. Let $\alpha$ ($0 \le \alpha < 1$) be the probability that one or more than one bit errors will occur in the data in the received packet. In addition, it is assumed that no bit error in the destination address part occurs.

In order to achieve error-free file transfer, the server node sends an ACK (Acknowledgement) packet, which indicates the detection result of a bit error in the packet sent by the client node, to the client node for each packet reception. Here, we assume that no bit error in the data part of the ACK packets occurs. If the received ACK packet indicates no bit error in the packet, the next packet is immediately sent after receiving the ACK packet to the server node. On the other hand, if the received ACK packet indicates there is bit error in the packet, the client node retransmits the packet which was not correctly received immediately after receiving the ACK packet. The size of the packet transferred from the client node to the server node is $m_1$ [bits], the size of the ACK packet is $m_2$ [bits], and we assume that the buffering delay of the packet in the routers is zero. This is referred to as Method 1. Also, in the following calculation, calculate the answers to three significant digits.

(1) Show the transmission period between the start of packet transfer from the client node and the reception of a corresponding ACK packet from the server node, regardless of whether the data in the packet from the client node to the server node has a bit error, with a mathematical formula. And, show the probability that an error-free packet transfer from the client node to the server node will succeed at the n-th time ($n \ge 1$) with a mathematical formula.

(2) Show the average data transfer speed from the client node to the server node with a mathematical formula. Furthermore, in each case of $\{D_2 = 0.1 \text{msec}, B_2 = 1 \text{Gbits/sec}\}$ and $\{D_2 = 500 \text{msec}, B_2 = 10 \text{Mbits/sec}\}$, show the maximum transfer speed when $m_1 = m_2 = 100$ [bits].

(3) In TCP (Transport Control Protocol), which is generally used on the Internet, the data transfer speed is improved by transferring packets in a pipeline fashion, without waiting for the reception of the ACK packets. The maximum amount of packets that can be transferred without waiting for the reception of an ACK packet (this is called the window size) is set to 64 Kbytes. Show the maximum transfer speed when $m_1 = m_2 = 100$ [bits] in the case of $\{D_2 = 0.1 \text{msec}, B_2 = 1 \text{Gbits/sec}\}$ and in the case of $\{D_2 = 500 \text{msec}, B_2 = 10 \text{Mbits/sec}\}$. Here, this method of transferring data with a window size of 64 Kbytes is referred to as Method 2.

(4) In both Methods 1 and 2, when there are multiple upload destination server candidates, it is desirable to know the available transfer speed and delay time for each server. Method 1 can be improved to predict the maximum available data transfer speed between the client node and the server node, based on the information of the arrival intervals of the ACK packets observed at the client node. Explain this method.

Next, we would like to simultaneously deliver the same 500 Mbyte video streaming playback files from the server node to N client nodes. It is assumed that video streaming data is simultaneously distributed from the server node to each client node using Method 2, and a data transfer speed of 8 Mbits/sec from the server node to each client node is required between the nodes for normal video playback. Here, $N \le 100$.

(5) Show $D_{2\text{max}}$, which is the maximum value of $D_2$ that enables normal video playback.

(6) Show two solutions to enable normal video playback even when $D_2$ is larger than $D_{2\text{max}}$. Note that the bandwidth $B_i$ and the propagation delay $D_i$ of the communication line, and the size of transferred packets, $m_1$ and $m_2$, cannot be changed.

---

### Problem 3

Select four items out of the following eight items concerning information systems, and explain each item in approximately from four to eight lines of text. If necessary, use examples, figures, or equations.

(1) Cellular automaton
(2) Clock frequency
(3) The method of surrogate data
(4) Pseudo-inverse matrix (generalized inverse matrix)
(5) Recurrent neural network
(6) Kullback–Leibler divergence
(7) Homography transformation
(8) Passive walking
