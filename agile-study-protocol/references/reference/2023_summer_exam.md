# 2023 Summer Entrance Examination
## Department of Creative Informatics, The University of Tokyo

### INSTRUCTIONS
1. Do not open this booklet until the start of the examination is announced.
2. Write your examinee ID number below on this cover page.
3. Answer in Japanese or English.
4. You may write on the back of the answer sheet.
5. Write your examinee ID number and the problem number inside the top blanks of each sheet.
6. Do not bring the answer sheet or this booklet out of this room.

---

### Problem 1

We are constructing a deterministic finite automaton (DFA) that judges whether the sum of two binary integers is a multiple of three or not.

(1) A DFA is represented by a directed graph called a state diagram. Figure 1 is an example of a state diagram. The states of a DFA are represented by the nodes of the graph. When a DFA in state $q$ reads a symbol $a$, it changes its state according to the outgoing edge labeled $a$ of the node corresponding to $q$. The set of allowed input symbols is a finite set, which is called its input alphabet. In the state graph of a DFA, each node has exactly one outgoing edge for each symbol in its input alphabet.
One of the states is the start state, which is indicated by the arrow labeled *start*. Some states are designated as final states, which are indicated by double circles. When a DFA $M$ in its start state will be in one of the final states after reading all symbols of a symbol string $w$ one-by-one from left to right, we say $M$ accepts $w$.

(1-1) Let $M_1$ be the DFA represented by Figure 1. The input alphabet of $M_1$ is $\{0, 1\}$. Answer the state that $M_1$ will be in after reading the symbol string 0101110 starting in the start state.

(1-2) Answer the shortest symbol string starting with 0101110 that the DFA $M_1$ accepts.

(1-3) Construct a DFA $M_2$ that accepts a symbol string $w$ if and only if the length of $w$ is an even number, and draw its state diagram. $M_2$ must satisfy the following conditions.
(Condition 1) The number of states of $M_2$ is two.
(Condition 2) The input alphabet of $M_2$ is $\{0, 1\}$.

(2) Consider a string of symbols in $\{0, 1\}$ to be a binary number. Let $(x_{n-1} x_{n-2} \cdots x_0)_2$ denote the n-digit binary number whose $i$-th digit ($0 \le i < n$) from the least significant digit is $x_i \in \{0, 1\}$. Let $\mathcal{V}(x_{n-1} x_{n-2} \cdots x_0)$ denote its value. When the string $x_{n-1} x_{n-2} \cdots x_0$ starts with a sequence of 0s, let $\mathcal{V}(x_{n-1} x_{n-2} \cdots x_0)$ denote the value of the string without the sequence of 0s. The string whose length is zero is called an empty string, denoted by $\epsilon$. Let $\mathcal{V}(\epsilon) = 0$. For example, $\mathcal{V}(0101110)$ is 46 in decimal.
For every binary number with an even number of digits $(x_{2n-1} x_{2n-2} \cdots x_0)_2$, show
$$ \mathcal{V}(x_{2n-1} x_{2n-2} \cdots x_0) \equiv \left( 2 \sum_{i=0}^{n-1} x_{2i+1} + \sum_{i=0}^{n-1} x_{2i} \right) \pmod 3 $$
Here, "$a \equiv b \pmod 3$" denotes the remainders of $a$ and $b$ are the same when they are divided by three. In what follows, we will omit "$\pmod 3$" and simply denote "$a \equiv b$."

(3) Consider $w$, a string of symbols in $\{0, 1\}$, to be a binary number $(w)_2$. Construct a DFA $M_3$ that accepts $w^R$, the string $w$ in reverse order, if and only if its length is an even number and
$$ \mathcal{V}(w) \equiv 0 $$
holds, and draw its state diagram. $M_3$ must satisfy the following conditions.
(Condition 1) The number of states of $M_3$ is six.
(Condition 2) The input alphabet of $M_3$ is $\{0, 1\}$.

(4) Consider $w$, a string of symbols in $\{0, 1\}$, to be a binary number $(w)_2$. Construct a DFA $M_4$ that accepts $w^R$ if and only if
$$ \mathcal{V}(w) \equiv 0 $$
holds regardless of the length of $w$, and draw its state diagram. $M_4$ must satisfy the following conditions.
(Condition 1) The number of states of $M_4$ is three.
(Condition 2) The input alphabet of $M_4$ is $\{0, 1\}$.

(5) Let
$$ \Sigma = \{ \binom{a}{b} \mid a, b \in \{0, 1\} \}. $$
For $w = \binom{x_{n-1}}{y_{n-1}} \binom{x_{n-2}}{y_{n-2}} \cdots \binom{x_0}{y_0}$, a string of symbols in $\Sigma$ with length $n$, construct a DFA $M_5$ that accepts $w^R$ if and only if
$$ \mathcal{V}(x_{n-1} x_{n-2} \cdots x_0) + \mathcal{V}(y_{n-1} y_{n-2} \cdots y_0) \equiv 0 $$
holds, and draw its state diagram. $M_5$ must satisfy the following conditions.
(Condition 1) The number of states of $M_5$ is three.
(Condition 2) The input alphabet of $M_5$ is $\Sigma$.

---

### Problem 2

An IPv4 address, which indicates a location on the Internet, is a 32 bits (4 Bytes) number. Each 8 bits (1 Byte) is represented as a decimal number separated by a dot "." as in Figure 1. IP addresses are assigned to network interfaces (boundaries between nodes and physical links). An IP address consists of a network ID that identifies the network and an interface ID that identifies the interface. In the network notation, a network is expressed by a decimal notation of the IP address with "/" and a length of a network ID (number of bits), as shown in Figure 1.

(Figure 1: IP address structure)

A network can be divided into subnets. Each subnet has a unique network ID. The network administrator assigns IP addresses from the range (block) of IP addresses with the subnet's network ID to the interfaces connecting to that subnet.

For example, 203.178.168.0/24 can be divided into 203.178.168.0/25, with IP addresses ranging from 203.178.168.0 to 203.178.168.127, and 203.178.168.128/25, with IP addresses ranging from 203.178.168.128 to 203.178.168.255. In addition, a subnet of 203.178.168.0/27 can be created. Suppose 203.178.168.0/27 is in use in another subnet. In that case, the network administrator must avoid IP address duplication. The administrator assigns IP addresses to the interfaces connecting to the subnet of 203.178.168.0/25 from the range excluding 203.178.168.0/27 because 203.178.168.0/25 includes 203.178.168.0/27.
Answer the following questions.

(1) How many uniquely identifiable IPv4 addresses exist in the Internet?

(2) Express in decimal representation the IPv4 address with the hexadecimal representation C0A864C8.

(3) What is the maximum number of IP addresses that can be assigned in a network with a network ID length of 20 bits? However, the interface IDs are reserved when they are all 0 or 1. They are not assigned to interfaces.

(4) Assign network addresses to each of the six subnets (N1 to N6) in Figure 2 from 192.168.254.0/23. The subnet assignment has the following constraints: IP addresses are assigned in ascending order from N1 to N6. IP addresses must be assigned on 250 interfaces in N1, IP addresses must be assigned on 120 interfaces in N2, and IP addresses must be assigned on 110 interfaces in N3. Note that the interfaces connected to N1 to N3 include those of the respective routers. A node with multiple interfaces connecting to different subnets is called a router here. In addition, we should assign IP addresses to the routers (R1 to R3)' interfaces in N4, N5 and N6. We have the same reserved IDs as in question (3). Answer the network address, such as 192.168.a.b - 192.168.d.e, to be assigned to each subnet.

A UDP packet is sent for a Voice-over IP application in a network shown in Figure 3. The packet consists of a 100-byte header and a P-byte payload (data part). The bottleneck in this network is between Router 1 and Router 2, with the bandwidth of 6M bits/sec.

(5) Consider sending digitally encoded voice data directly from the source node to the destination node. Suppose the data is encoded at a constant rate of 128 kbps and each packet is entirely filled before the source sends the packet into the network. The source node must wait until the payload is filled with data, and this delay is called packetization delay. When $P = 1000$ bytes, determine the packetization delay.

(6) If we want to keep packetization delay below 20 milliseconds for comfortable conversations, how should we change the packet size?

(7) Next, we want to send large files as quickly as possible. Payload throughput is called effective throughput. Express the maximum effective throughput using $P$ in an equation. Also, give the maximum effective throughput when $P = 100$ and $P = 1000$ bytes.

(8) On the Internet, routers may discard packets when necessary. When a router discards a packet with probability $s$, give the average number of hops for all packets sent by the source node in Figure 3 (including those that did not reach the destination). Delivering a packet to the next destination is called hopping. In Figure 3, when a packet reaches the destination node from the source node, it hops three times.

(9) The bit error rate of the transmission channel is $\alpha (0 \le \alpha < 1)$. The source node sends each bit three times to improve the error rate. For example, when it transmits 0, it sends 000, and when it transmits 1, it sends 111. When the receiver restores the original data by majority vote, express bit error rate after the restoration as an equation.

(10) In TCP/IP communication, since multiple processes are assumed to be running at the destination node, the destination port number is used to identify the destination process for the received packet. Why did the designers of TCP/IP choose an abstract identifier, the port number, which is independent of its process identifier? Answer two benefits of the port number.

---

### Problem 3

Select four items out of the following eight items concerning information systems, and explain each item in approximately from four to eight lines of text. If necessary, use examples, figures or equations.

(1) Hash table
(2) Process and Thread
(3) CSMA/CD
(4) Routh-Hurwitz stability criterion
(5) Random forest
(6) Functional programming
(7) Flip-flop
(8) SLAM (Simultaneous localization and mapping)
