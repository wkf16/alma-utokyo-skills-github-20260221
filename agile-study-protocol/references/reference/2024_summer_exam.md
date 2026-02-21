# 2024 Summer Entrance Examination
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

In the following, when a sample $X = (x_1, x_2, x_3, ..., x_N)$ consisting of $N$ observations is obtained for a stochastic process, we calculate the parameters of the original stochastic information source by using maximum likelihood estimation. Maximum likelihood estimation is a type of parameter estimation method and is described below.

> Let $f(x; \theta)$ be the density function of the distribution in accordance with the parameter $\theta$. The likelihood function $L(X|\theta)$ when obtaining a sample $X$ is given by $\prod_{n=1}^N f(x_n; \theta)$. Here, $\theta$ that maximizes $L(X|\theta)$ is called a maximum likelihood estimator.

Answer the following questions.

(1) As an example, consider the coin toss. Let $\theta$ be the probability of a coin coming up faces. We obtained the observation that when this coin is tossed $N$ times, faces come up $r$ times. Obtain the likelihood function in this case based on the above definition.

(2) Estimate the probability $\theta$ of a coin coming up faces by using maximum likelihood estimation. First, consider the logarithmic value of the likelihood function (hereafter referred to as the *log-likelihood function*), and then find $\theta$ that maximizes the log-likelihood function by differentiation.

A normal distribution with parameters, the mean $\mu$ and the variance $\sigma^2$, is described as $\mathcal{N}(\mu, \sigma^2)$, and its probability density function is given by
$$ f(x; \mu, \sigma^2) = \frac{1}{\sqrt{2\pi}\sigma} e^{-(x-\mu)^2 / (2\sigma^2)}. $$
Consider the case of observing data generated from multiple normal distributions. This is called the *Gaussian Mixture Model (GMM)*. The data generation process of the GMM is described as follows.

1. Assume a distribution that selects the number $k$ ($k = 1, ..., K$) with probability $\pi_k$ (this is called a categorical distribution C). Also, assume $K$ normal distributions $\mathcal{N}_1(\mu_1, \sigma_1^2), ..., \mathcal{N}_K(\mu_K, \sigma_K^2)$, each of which corresponds to each number.
2. For each element ($n = 1, ..., N$) of sample X:
   2-I: generate number $z_n$ in accordance with the categorical distribution C mentioned above,
   2-II: generate $x_n$ in accordance with the normal distribution $\mathcal{N}_{z_n}(\mu_{z_n}, \sigma_{z_n}^2)$ corresponding to the generated number $z_n$.
3. The generated sequence of $N$ observation values $(x_1, x_2, x_3, ..., x_N)$ is a sample. From this sample, we obtain the GMM parameters $\Theta = \{ \mu_k, \sigma_k, \pi_k \}_{k=1,...,K}$ by maximum likelihood estimation.

First, consider the case of $K = 1$ (data generation from a single normal distribution). When we obtain a sample $X = (x_1, x_2, x_3, ..., x_N)$ consisting of $N$ observations generated from this normal distribution, we want to estimate the parameters (mean $\mu$ and variance $\sigma^2$) by maximum likelihood estimation. Answer the following questions.

(3) Find the log-likelihood function for this case.

(4) Find the value that maximizes the log-likelihood function with respect to the mean $\mu$ (i.e., find the maximum likelihood estimator of the mean $\mu$). Similarly, find the value that maximizes the log-likelihood function with respect to the variance $\sigma^2$ (i.e., find the maximum likelihood estimator of the variance $\sigma^2$).

Next, consider the case of $K \ge 2$. Answer the following questions.

(5) We would like to describe the log-likelihood function in this case as a function of the parameters $\Theta$ and $Z = (z_1, z_2, ..., z_N)$. First, describe the probability $p(Z|\Theta)$ that $Z$ is generated using $\pi_k$. Next, given $Z$, describe the generation probability $p(X|Z, \Theta)$ of $X$. Finally, describe the log-likelihood function using the probabilities $p(Z|\Theta)$ and $p(X|Z, \Theta)$ obtained above.

We want to maximize the log-likelihood function obtained in Question (5) above. However, since this log-likelihood function contains a sum operation $\Sigma$ in the logarithmic function, it is difficult to find $\Theta$ that makes the derivative zero. Therefore, the following "Algorithm A" is used to iteratively maximize (note that here we only focus on local maximization and do not seek global maximization). In Algorithm A, for the objective function $D(\Theta)$ to be maximized, using the auxiliary function $G(\Theta, \theta)$ and the auxiliary variable $\theta$ where $D(\Theta) = \max_{\theta} G(\Theta, \theta)$, the operations [step 1] $\theta \leftarrow \text{argmax}_{\theta'} G(\Theta, \theta')$ and [step 2] $\Theta \leftarrow \text{argmax}_{\Theta'} G(\Theta', \theta)$ are iteratively repeated to calculate the local optimum of $\Theta$. Answer the following questions.

(6) Prove that, when using above Algorithm A, $\Theta$ that is updated by repeating step 1 and step 2 always raises or stops the original objective function $D(\Theta)$.

(7) We use Jensen's inequality to obtain the auxiliary function of the log-likelihood function obtained in Question (5) above. Jensen's inequality for logarithmic functions can be written as $\log (\sum_i \lambda_i y_i) \ge \sum_i \lambda_i \log (y_i)$ (where $y_i$ is a positive variable, $\lambda_i$ is any weight that satisfies $\sum_i \lambda_i = 1$ and $\lambda_i \ge 0$). Prove this inequality.

(8) Using Jensen's inequality, design an auxiliary function for the log-likelihood function obtained in Question (5). Let $\lambda_i$ be the auxiliary variable here. You can derive the auxiliary function by first dividing the individual normal distributions in the sum operation $\Sigma$ by $\lambda_i$ and multiplying them by $\lambda_i$ in front of that.

(9) Execute Algorithm A for the auxiliary function obtained in Question (8) above. First, find $\lambda_i$ that maximizes the auxiliary function as [step 1]. Next, find the parameter $\Theta$ that maximizes the auxiliary function (where the auxiliary variables are fixed) as [step 2].

---

### Problem 2

Let us consider a dataset that consists of $N$ data where each datum is represented in the form $x = (x_1, x_2, ..., x_b)$ ($x_i \in \{0, 1\}, 1 \le i \le b$) which is a bit string of length $b$ ($b \ge 1$). Each datum is assigned a unique data ID (identifier) which is a distinct integer. Let's build a system that searches for data close in distance to an arbitrary input datum (query datum). During a search, the system needs to enumerate the data IDs of all data that satisfy the condition. The distance between two data is defined by the Hamming distance between bit strings. The Hamming distance between two bit strings $x = (x_1, x_2, ..., x_b)$ and $y = (y_1, y_2, ..., y_b)$ is defined as follows.
$$ d(x, y) = \sum_{i=1}^b |x_i - y_i| $$

Answer the following questions.

(1) The table below shows an example of the dataset in the case of $b=4$ and $N=3$.

| Data ID | $x_1$ | $x_2$ | $x_3$ | $x_4$ |
| :---: | :---: | :---: | :---: | :---: |
| 1 | 0 | 1 | 1 | 1 |
| 2 | 1 | 0 | 0 | 1 |
| 3 | 0 | 0 | 1 | 0 |

Assume that a query datum $(1, 1, 0, 1)$ is given. Find the Hamming distance between the query datum and each datum.

Next, we consider a search algorithm using a lookup table. Assume that $b$ is an even number and that the bit strings of data are uniformly distributed. In the following questions, it is not necessary to consider the time complexity of building a lookup table.

(2) We want to search for data whose bit strings are identical to a given query datum. Here, let us consider a lookup table that takes a bit string as an input and outputs a list containing the data IDs of all data that have the bit string. Answer the average time complexity and the space complexity of a search using this lookup table.

(3) We consider an algorithm as follows. We divide a bit string into two bit strings of length $b/2$. We search for candidates by using the lookup table in the same manner as Question (2) for each divided bit string and then return the data IDs of all data matching the query datum. Answer the average time complexity and the space complexity of a search by this algorithm.

(4) By using the same data structure as Question (3), we consider an algorithm to search for data with a Hamming distance of 1 or less from a given query datum. Answer the average time complexity of a search by this algorithm.

Next, we consider the case where $2^b \gg N$. In this case, it is sometimes effective to perform a linear search by actually calculating the Hamming distance between the query datum and each datum. Therefore, let us consider designing a specialized digital circuit to compute the Hamming distance.

(5) Let us consider a 2-input 1-output digital circuit $H_1$ whose inputs are two 1-bit bit strings $x=(x_1)$, $y=(y_1)$ ($x_1, y_1 \in \{0, 1\}$) and output is $z \in \{0, 1\}$ which is the Hamming distance between $x$ and $y$. Draw a table representing the relation of $x, y$, and $z$. Also, draw $H_1$ by using necessary components among AND, OR, and NOT gates.

(6) Draw a 4-input 2-output digital circuit $H_2$ that outputs a binary representation of the Hamming distance between two 2-bit bit strings by using necessary components among AND, OR, NOT gates, and $H_1$.

(7) Draw an 8-input 3-output digital circuit $H_4$ that outputs a binary representation of the Hamming distance between two 4-bit bit strings by using necessary components among $H_2$, half adder $HA$, and OR gate.

---

### Problem 3

Select four items out of the following eight items concerning information systems, and explain each item in approximately from four to eight lines of text. If necessary, use examples, figures or equations.

(1) Dynamic programming
(2) Zero Moment Point (ZMP)
(3) BNF (Backus-Naur Form or Backus Normal Form)
(4) Transparent cache in wide area networks
(5) Dynamic map in self-driving car system
(6) Thread-level parallel speculative execution
(7) Procedural modeling
(8) k-nearest neighbor algorithm
