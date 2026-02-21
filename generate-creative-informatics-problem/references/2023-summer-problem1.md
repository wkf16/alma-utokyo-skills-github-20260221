### Reference 3: 2023 Summer Entrance Exam - Problem 1
*(Topic: Deterministic Finite Automata, Binary Numbers, Divisibility by 3)*

**Problem 1**

We are constructing a deterministic finite automaton (DFA) that judges whether the sum of two binary integers is a multiple of three or not.

(1) A DFA is represented by a directed graph called a state diagram. Figure 1 is an example of a state diagram. The states of a DFA are represented by the nodes of the graph. When a DFA in state $q$ reads a symbol $a$, it changes its state according to the outgoing edge labeled $a$ of the node corresponding to $q$. The set of allowed input symbols is a finite set, which is called its input alphabet. In the state graph of a DFA, each node has exactly one outgoing edge for each symbol in its input alphabet.
One of the states is the start state, which is indicated by the arrow labeled *start*. Some states are designated as final states, which are indicated by double circles. When a DFA $M$ in its start state will be in one of the final states after reading all symbols of a symbol string $w$ one-by-one from left to right, we say $M$ accepts $w$.

*(Figure 1 Omitted: Shows a DFA $M_1$ with 3 states $q_0$ (start), $q_1$ (final), $q_2$. Transitions on $\{0,1\}$.)*

(1-1) Let $M_1$ be the DFA represented by Figure 1. The input alphabet of $M_1$ is $\{0, 1\}$. Answer the state that $M_1$ will be in after reading the symbol string 0101110 starting in the start state.
(1-2) Answer the shortest symbol string starting with 0101110 that the DFA $M_1$ accepts.
(1-3) Construct a DFA $M_2$ that accepts a symbol string $w$ if and only if the length of $w$ is an even number, and draw its state diagram. $M_2$ must satisfy the following conditions.
(Condition 1) The number of states of $M_2$ is two.
(Condition 2) The input alphabet of $M_2$ is $\{0, 1\}$.

(2) Consider a string of symbols in $\{0, 1\}$ to be a binary number. Let $(x_{n-1}x_{n-2} \cdots x_0)_2$ denote the $n$-digit binary number whose $i$-th digit ($0 \le i < n$) from the least significant digit is $x_i \in \{0, 1\}$. Let $\mathcal{V}(x_{n-1}x_{n-2} \cdots x_0)$ denote its value. When the string $x_{n-1}x_{n-2} \cdots x_0$ starts with a sequence of 0s, let $\mathcal{V}(x_{n-1}x_{n-2} \cdots x_0)$ denote the value of the string without the sequence of 0s. The string whose length is zero is called an empty string, denoted by $\epsilon$. Let $\mathcal{V}(\epsilon) = 0$. For example, $\mathcal{V}(0101110)$ is 46 in decimal.
For every binary number with an even number of digits $(x_{2n-1}x_{2n-2} \cdots x_0)_2$, show
$$ \mathcal{V}(x_{2n-1}x_{2n-2} \cdots x_0) \equiv \left( 2 \sum_{i=0}^{n-1} x_{2i+1} + \sum_{i=0}^{n-1} x_{2i} \right) \pmod 3 $$
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
$$ \mathcal{V}(x_{n-1}x_{n-2} \cdots x_0) + \mathcal{V}(y_{n-1}y_{n-2} \cdots y_0) \equiv 0 $$
holds, and draw its state diagram. $M_5$ must satisfy the following conditions.
(Condition 1) The number of states of $M_5$ is three.
(Condition 2) The input alphabet of $M_5$ is $\Sigma$.
