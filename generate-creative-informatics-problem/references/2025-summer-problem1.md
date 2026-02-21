### Reference 1: 2025 Summer Entrance Exam - Problem 1
*(Topic: Markov Chains, PageRank, Perron-Frobenius Theorem)*

**Problem 1**

Suppose that there are $N$ web pages. A user staying at a web page at time $t (t \ge 0)$ will move to one of the linked pages at time $t+1$ with equal probability. If there are no linked pages, the user will stay at the same page as time $t$. Let $p_n^{(t)} (1 \le n \le N)$ denote the probability of the user staying at the $n$-th page at time $t$, and $p^{(t)} = (p_1^{(t)}, p_2^{(t)}, ..., p_N^{(t)})^T$ denote the vector that summarizes them.

First, let us consider the case of $N=3$ shown in Table 1. When there are three web pages shown in Table 1, the state transition diagram that represents a user's state is depicted as a graph in Figure 1. Each node in the graph shown in Figure 1 corresponds one-to-one to a page in Table 1, and an edge represents a transition between the pages from time $t$ to time $t+1$. The value appended to an edge shows the probability of the transition occurring. Note that when there are no linked pages and a user keeps staying at the same page, it is interpreted as a transition to the same page as time $t$.

**Table 1**
| | Page 1 | Page 2 | Page 3 |
| :--- | :--- | :--- | :--- |
| **Linked Page** | Page 2 | Page 1, 3 | None |

*(Figure 1 Omitted: Shows a directed graph with probabilities 1, 0.5, 0.5, 1 based on the table)*

Answer the following questions.

(1) Given $p^{(0)} = (1, 0, 0)^T$, find $p^{(1)}$ and $p^{(2)}$.
(2) Represent $p_1^{(t)}$ and $p_2^{(t)}$ using $t$. $p^{(0)}$ is the same as in Question (1).
(3) Find $p^{(t)}$ when $t \to \infty$. $p^{(0)}$ is the same as in Question (1).

Next, we introduce an operation called "jump" that occurs during a move between pages from time $t$ to time $t+1$ with a constant probability $\alpha > 0$. When a jump occurs, the user moves to one of $N$ pages (including the current page) with equal probability. When a jump does not occur, the user moves to one of the linked pages with equal probability in the same manner as before (if there are no linked pages, the user will keep staying at the current current page).

(4) We introduce the jump operation into the case in Table 1. Suppose that $\alpha = 1/3$. Draw a state transition diagram for this case. Also, find the transition probability matrix $A$ that satisfies the following equation:
$$p^{(t+1)} = A p^{(t)}$$

(5) When $p^{(t+1)} = p^{(t)} (= p)$, this $p$ is called a stationary distribution. Find the stationary distribution in the case of Question (4).

Finally, we consider the transition probability matrix $R$ and stationary distribution of a general case where the jump operation is introduced. For answering the following questions, you can use the Perron-Frobenius theorem described below.

> **Perron-Frobenius theorem for positive matrices**
>
> A positive square matrix has a positive eigenvalue $k$ that satisfies the following. Here, a positive matrix is a matrix whose elements are all positive real numbers.
>
> (i) For the absolute value of an arbitrary eigenvalue $\lambda$ other than $k$, $|\lambda| < k$ holds.
> (ii) The eigenvalue $k$ is a simple root (i.e., has the multiplicity of 1), and there exists a positive eigenvector that belongs to the eigenvalue $k$. Here, a positive vector is a vector whose elements are all positive real numbers.
> (iii) There are no positive eigenvectors that belong to eigenvalues other than $k$.

(6) Show that $R^T$, the transpose of $R$, has 1 as an eigenvalue, and that this is the eigenvalue with the largest absolute value.

(7) Show that a stationary distribution exists uniquely. Here, you can assume the following fact as given; In general, a square matrix and its transpose have the same set of eigenvalues.

(8) Show that, by iteratively computing $p^{(t)}$ following the equation $p^{(t+1)} = R p^{(t)}$, regardless of the initial probability distribution $p^{(0)}$, $p^{(t)}$ converges to the stationary distribution when $t \to \infty$. You can assume that $p^{(0)}$ can be represented as a linear combination of eigenvectors, $p^{(0)} = \sum_{i=1}^N c_i x_i$. Here, $x_i$ denotes the $i$-th eigenvalue of $R$ while $c_i$ is its coefficient.
