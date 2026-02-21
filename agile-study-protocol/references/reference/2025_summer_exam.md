# 2025 Summer Entrance Examination
## Department of Creative Informatics, The University of Tokyo

### INSTRUCTIONS
1. Do not open this booklet until the start of the examination is announced.
2. Write your examinee's number below on this cover page.
3. Answer all three problems in Japanese or English.
4. Three answer sheets are given. Use a separate answer sheet for each problem. You may write on the back of the answer sheet.
5. Write your examinee's number and the problem number inside the top blanks of each sheet.
6. Do not bring the answer sheet or this booklet out of this room.

---

### Problem 1

Suppose that there are $N$ web pages. A user staying at a web page at time $t$ ($t \ge 0$) will move to one of the linked pages at time $t+1$ with equal probability. If there are no linked pages, the user will stay at the same page as time $t$. Let $p_n^{(t)}$ ($1 \le n \le N$) denote the probability of the user staying at the $n$-th page at time $t$, and $p^{(t)} = (p_1^{(t)} p_2^{(t)} ... p_N^{(t)})^T$ denote the vector that summarizes them.

First, let us consider the case of $N=3$ shown in Table 1. When there are three web pages shown in Table 1, the state transition diagram that represents a user's state is depicted as a graph in Figure 1. Each node in the graph shown in Figure 1 corresponds one-to-one to a page in Table 1, and an edge represents a transition between the pages from time $t$ to time $t+1$. The value appended to an edge shows the probability of the transition occurring. Note that when there are no linked pages and a user keeps staying at the same page, it is interpreted as a transition to the same page as time $t$.

**Table 1**
| | Page 1 | Page 2 | Page 3 |
| :--- | :--- | :--- | :--- |
| **Linked Page** | Page 2 | Page 1, 3 | None |

(Figure 1 showing state transitions: 1->2 (1.0), 2->1 (0.5), 2->3 (0.5), 3->3 (1.0))

Answer the following questions.

(1) Given $p^{(0)} = (1 \ 0 \ 0)^T$, find $p^{(1)}$ and $p^{(2)}$.

(2) Represent $p_1^{(t)}$ and $p_2^{(t)}$ using $t$. $p^{(0)}$ is the same as in Question (1).

(3) Find $p^{(t)}$ when $t \to \infty$. $p^{(0)}$ is the same as in Question (1).

Next, we introduce an operation called "jump" that occurs during a move between pages from time $t$ to time $t+1$ with a constant probability $\alpha > 0$. When a jump occurs, the user moves to one of $N$ pages (including the current page) with equal probability. When a jump does not occur, the user moves to one of the linked pages with equal probability in the same manner as before (if there are no linked pages, the user will keep staying at the current page).

(4) We introduce the jump operation into the case in Table 1. Suppose that $\alpha = 1/3$. Draw a state transition diagram for this case. Also, find the transition probability matrix $A$ that satisfies the following equation
$$ p^{(t+1)} = A p^{(t)}. $$

(5) When $p^{(t+1)} = p^{(t)} (= p)$, this $p$ is called a stationary distribution. Find the stationary distribution in the case of Question (4).

Finally, we consider the transition probability matrix $R$ and stationary distribution of a general case where the jump operation is introduced. For answering the following questions, you can use the Perron-Frobenius theorem described below.

> **Perron-Frobenius theorem for positive matrices**
> A positive square matrix has a positive eigenvalue $k$ that satisfies the following. Here, a positive matrix is a matrix whose elements are all positive real numbers.
> (i) For the absolute value of an arbitrary eigenvalue $\lambda$ other than $k$, $|\lambda| < k$ holds.
> (ii) The eigenvalue $k$ is a simple root (i.e., has the multiplicity of 1), and there exists a positive eigenvector that belongs to the eigenvalue $k$. Here, a positive vector is a vector whose elements are all positive real numbers.
> (iii) There are no positive eigenvectors that belong to eigenvalues other than $k$.

(6) Show that $R^T$, the transpose of $R$, has 1 as an eigenvalue, and that this is the eigenvalue with the largest absolute value.

(7) Show that a stationary distribution exists uniquely. Here, you can assume the following fact as given; In general, a square matrix and its transpose have the same set of eigenvalues.

(8) Show that, by iteratively computing $p^{(t)}$ following the equation $p^{(t+1)} = R p^{(t)}$, regardless of the initial probability distribution $p^{(0)}$, $p^{(t)}$ converges to the stationary distribution when $t \to \infty$. You can assume that $p^{(0)}$ can be represented as a linear combination of eigenvectors, $p^{(0)} = \sum_{i=1}^N c_i x_i$. Here, $x_i$ denotes the $i$-th eigenvalue of $R$ while $c_i$ is its coefficient.

---

### Problem 2

We transmit data via packet switching between sender S and receiver R connected as shown in Figure 1. Assume that one-way propagation delay $d_{prop}$ is 250 ms and bandwidth $B$ is 200 kbps. Ignore packet losses and assume that the packets are not fragmented during transmission. The communication is full-duplex. The prefix "k" represents $10^3$.

(Figure 1: Sender S --(network)-- Receiver R)

Answer the following questions.

(1) Assume that the packet size is 1500 bytes. Calculate the time from the moment S starts sending a packet to the moment R completely receives the packet. Note that the time required to push all the bits of a packet into the communication channel is referred to as *transmission delay*, and the time asked in this question is the sum of the transmission delay and the one-way propagation delay.

(2) Assume that the packet size is 1500 bytes. Consider a communication method where each time R completes receiving a packet, R sends an acknowledgment packet to S, then S sends the next packet immediately after S receives the acknowledgement packet. The acknowledgment packet is small enough that we can ignore its transmission delay. Calculate the effective speed in this setting. Provide your answer in kbps and round it to one decimal place. Note that *effective speed* refers to the value obtained by dividing the transmitted data size by the time from the moment S starts sending the first packet to the moment S receives the acknowledgment packet for the last packet.

(3) We define *line utilization* as the ratio of effective speed to bandwidth. Let's consider improving line utilization by increasing the packet size. Answer the minimum packet size $P$ that gives line utilization of 20% or more. Additionally, express line utilization as an equation in terms of the packet size $P$. Note that the unit of $P$ is bytes.

We adopt the following communication method to improve communication efficiency with a fixed packet size. Sender S continuously sends $\omega$ packets, and then checks whether the acknowledgment packet for the first packet has arrived at S at the time $\omega$ packets have been sent. If the packet has arrived, then S sends the next packet. Otherwise, S waits for the arrival of the acknowledgment packet, then S sends the next packet immediately after the arrival. Subsequent packets will be processed in the same way.

(4) Calculate the minimum value of $\omega$ such that the communication method described above fully utilizes the bandwidth. Assume that the packet size is 1500 bytes. Also, depict the communication in this case in a sequence diagram. Note that "fully utilize the bandwidth" refers to the situation that S is always pushing packets into the communication channel until all the packets have been sent.

(5) Express the minimum value of $\omega$ as an equation in terms of one-way propagation delay $d_{prop}$ (in ms), bandwidth $B$ (in kbps), and packet size $P$ (in bytes) such that the communication method described above fully utilizes the bandwidth. Note that the smallest integer greater than or equal to a real number $x$ is denoted by $\lceil x \rceil$.

Consider a network that transmits data via packet switching as shown in Figure 2. The server stores a file of size $4 \times 10^5$ bytes, and each client acquires the file via the network. First, a client sends a packet that requests the file to the server, and then the server sends the file to the client after receiving the request. Note that the communication between the server and a client is full-duplex. Also, the server and each client are connected by a dedicated communication channel, and therefore its bandwidth is not affected by other communication channels. The packet that requests a file is small enough that we can ignore its transmission delay.

(Figure 2: Server connected to Client 1, Client 2, Client 3, ..., Client 20)

Answer the following questions. Note that time $t$ is the elapsed time measured from the moment Client 1 sends a file request packet.

(6) Assume that the server can process only one file request packet at a time. When the server receives a file request packet from a client, the server sends the file to the client. Assume that it takes 5 ms from the moment when the server starts processing a file request packet to the moment it starts sending the file, and that the server completes processing the file request packet when it completes sending the file. When a new file request packet arrives from another client while the server is processing a file request packet, the new file request packet is stored in a queue. The server starts processing the file request packet at the head of the queue immediately after it completes processing the current file request packet. Each client sends a file request packet to the server at times shown in Table 1. The configuration of the network each client is connected to is shown in Table 1. Answer the time when Client 1, 2, and 3 complete receiving the file, respectively.

**Table 1: File request time and network configuration of clients**
| | File request time | Propagation delay between a client and the server (one-way) | Bandwidth |
| :--- | :--- | :--- | :--- |
| Client 1 | $t=0$ ms | 50 ms | 500 kbps |
| Client 2 | $t=30$ ms | 110 ms | 250 kbps |
| Client 3 | $t=50$ ms | 60 ms | 800 kbps |

From now on, we improve the server and make it possible for the server to process file request packets from multiple clients concurrently by multi-threading. The server starts a thread each time it receives a file request, and each thread is dedicated to file transmission to a client after the start. Assume that it takes 15 ms from the moment when the server starts processing a file request packet to the moment it starts sending the file after starting a thread. A thread terminates immediately after it completes sending the file.

(7) Assume that a sufficient number of threads can run without interfering with each other on the server. The configuration of the network each client is connected to is shown in Table 1. Answer the time when Client 1, 2, and 3 complete receiving the file, respectively.

(8) Assume that there are 20 clients connected to the server with an identical configuration as shown in Table 2. Client 1, Client 2, ..., and Client 20 request the file in this order with 10 ms intermission.

**Table 2: Network configuration of clients**
| Propagation delay between a client and the server (one-way) | Bandwidth |
| :--- | :--- |
| 50 ms | 500 kbps |

Assume that the maximum number of file transmission threads that can run concurrently on the server is 12. When a file request packet arrives but already 12 threads are running and the server cannot start a new thread, the file request packet is stored in a queue. When one of the threads terminates, the server immediately starts processing the file request packet at the head of the queue. Answer the time when the server starts processing the file request packet from Client 20, and the time when Client 20 completes receiving the file.

---

### Problem 3

Select four items out of the following eight items concerning information systems, and explain each item in approximately from four to eight lines of text. If necessary, use examples, figures or equations.

(1) Radix sort
(2) L-value and R-value in programming languages
(3) Model checking
(4) Quasi-Newton method
(5) Bayesian networks
(6) Marching cubes method
(7) Types of optical distance sensors (at least two) and their principles
(8) Cryptographic hash function
