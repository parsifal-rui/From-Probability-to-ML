# Quick Start Guide - Probability Theory

## 1. Counting

### Permutation

- For positive integers only
- Formula: $P(n,r) = n(n-1)(n-2)\cdots(n-r+1)$

### Combination

- Formula: $C(n,r) = \binom{n}{r} = \frac{n!}{r!(n-r)!}$
- Note: $C(n,r) = 0$ when $r > n$

### Multinomial Coefficient

**Definition**: For $n \in \mathbb{N}$ and $n_1, n_2, \ldots, n_k \in \mathbb{N}$ such that $n_1 + n_2 + \cdots + n_k = n$:

$$\binom{n}{n_1, n_2, \ldots, n_k} = \frac{n!}{n_1! n_2! \cdots n_k!}$$

**Theorem**: $$\binom{n}{n_1, n_2, \ldots, n_k} = \binom{n}{n_1} \binom{n-n_1}{n_2} \binom{n-n_1-n_2}{n_3} \cdots \binom{n_k}{n_k}$$

This is used to split multinomial expressions into combinations.

## 2. Elementary Probability

### Probability Space

Let $\Omega$ denote a sample space, $\mathcal{F}$ be the collection of all events. A function $P : \mathcal{F} \to [0,1]$ is a **probability measure** if:

- $P[\Omega] = 1$
- For mutually exclusive events ${A_k}_{k \in \mathbb{N}} \subseteq \mathcal{F}$ (i.e., $A_i \cap A_j = \emptyset$ for $i \neq j$): $$P\left[\bigcup_{k \in \mathbb{N}} A_k\right] = \sum_{k \in \mathbb{N}} P[A_k]$$

We work with the probability space $(\Omega, \mathcal{F}, P)$.

### Inclusion-Exclusion Principle

For events $A_1, A_2, \ldots, A_n$: $$P[A_1 \cup A_2 \cup \cdots \cup A_n] = \sum_{i} P[A_i] - \sum_{i<j} P[A_i \cap A_j] + \sum_{i<j<k} P[A_i \cap A_j \cap A_k] - \cdots$$

## 3. Conditional Probability

### 引入题目


### Definition
本质理解：A和B同时发生的 = A发生的前提下 B发生了 = B发生的前提下 A发生了

For events $A, B \in \mathcal{F}$ with $P[A] \neq 0$: $$P[B|A] = \frac{P[A \cap B]}{P[A]}$$
### Independence

Events ${A_i}_{i=1}^n$ are **pairwise independent** if for all $i \neq j$: $$P[A_i \cap A_j] = P[A_i]P[A_j]$$
![[Pasted image 20250531150906.png]]
### Bayes' Theorem

Let ${A_i}_{i \in I}$ be a partition of $\Omega$, and $B$ be an event with $P[B] \neq 0$: $$P[A_i|B] = \frac{P[B|A_i]P[A_i]}{\sum_{j \in I} P[B|A_j]P[A_j]}$$

**Special case**: For events $A, B$ with $P[B] \neq 0$: $$P[A|B] = \frac{P[B|A]P[A]}{P[B|A]P[A] + P[B|A^c]P[A^c]}$$

## 4. Discrete Distributions

### Cumulative Distribution Function (CDF)

For a random variable $X$: $$F_X(x) = P[X \leq x]$$

**Properties**:

- Non-decreasing: $F_X(x_1) \leq F_X(x_2)$ for $x_1 < x_2$
- Right-continuous: $\lim_{y \to x^+} F_X(y) = F_X(x)$
- $\lim_{x \to \infty} F_X(x) = 1$ and $\lim_{x \to -\infty} F_X(x) = 0$

### Discrete Random Variables

A random variable $X$ is **discrete** if its range is countable.

**Probability Mass Function (PMF)**: $$p_X(x) = P[X = x]$$

**Properties**:

- $p_X(x) \geq 0$ for all $x$
- $\sum_{x} p_X(x) = 1$

### Continuous Random Variables

A random variable $X$ is **continuous** if there exists a function $f_X : \mathbb{R} \to \mathbb{R}$ such that: $$F_X(x) = \int_{-\infty}^x f_X(y) , dy$$

The function $f_X$ is called the **probability density function (PDF)**.

### Expected Value

For a discrete random variable $X$: $$E[X] = \sum_i x_i P[X = x_i] = \sum_i x_i p_X(x_i)$$

### Law of the Unconscious Statistician (LOTUS)

For a function $\phi : \mathbb{R} \to \mathbb{R}$ and discrete random variable $X$: $$E[\phi(X)] = \sum_i \phi(x_i) p_X(x_i)$$

_Note: This can be viewed as a consequence of linearity of expectation._

### Variance

For a random variable $X$ with mean $\mu$: $$\text{Var}(X) = \sigma^2 = E[(X - \mu)^2]$$

**Standard deviation**: $\sigma = \sqrt{\text{Var}(X)}$

**Alternative formula**: $$\text{Var}(X) = E[X^2] - (E[X])^2$$

**Properties**:

- $\text{Var}(c) = 0$ for constant $c$
- $\text{Var}(cX) = c^2 \text{Var}(X)$
- If $X$ and $Y$ are independent: $\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y)$


### Moment Generating Functions

### Ordinary Moments

The **$k$-th ordinary moment** of random variable $X$ is: $$E[X^k]$$
### Moment Generating Function (MGF)

The **moment generating function** of $X$ is: $$m_X(t) = E[e^{tX}]$$

provided this expectation is finite for all $t$ in some open interval $(-h, h)$.

**Uniqueness Property**: If $m_X(t) = m_Y(t)$ for all $t$, then $F_X(x) = F_Y(x)$ for all $x$.

#### Example: Geometric Distribution MGF

For $X \sim \text{Geometric}(\theta)$: $$m_X(t) = E[e^{tX}] = \sum_{x=1}^{\infty} e^{tx}(1-\theta)^{x-1}\theta = \frac{e^t\theta}{1-(1-\theta)e^t}$$
#### Example 2: Binomial Distribution MGF

For $X \sim \text{Binomial}(n, p)$ with PMF $p_X(x) = \binom{n}{x}p^x(1-p)^{n-x}$, $x = 0, 1, 2, \ldots, n$:

$m_X(t) = E[e^{tX}] = \sum_{x=0}^{n} e^{tx}\binom{n}{x}p^x(1-p)^{n-x}$

$= \sum_{x=0}^{n} \binom{n}{x}(pe^t)^x(1-p)^{n-x} = (pe^t + (1-p))^n$
#### Theorem
Given independent rv’s X and Y with mgf mX and mY , then for all t,  
mX+Y (t) = mX (t)mY (t)
#### Generating Moments from MGF

The $k$-th moment can be obtained by: $$E[X^k] = \frac{d^k}{dt^k} m_X(t) \bigg|_{t=0}$$

This provides a systematic way to calculate all moments of a distribution.

### 一些distribution
- 1. Bernoulli 分布
	A random variable $X$ has a **binomial distribution** with parameters $n$ and $\theta$ if its PMF is: $p_X(x) = \binom{n}{x}\theta^x(1-\theta)^{n-x}, \quad 0 \leq \theta \leq 1, \quad x = 0, 1, 2, \ldots, n$
	where $n$ is a positive integer. We write $X \sim \text{Binomial}(n, \theta)$.
	**Verification**: Using the binomial theorem: $\sum_{x=0}^{n} p_X(x) = \sum_{x=0}^{n} \binom{n}{x}\theta^x(1-\theta)^{n-x} = (\theta + (1-\theta))^n = 1$

	**CDF**: $F_X(t) = \sum_{x=0}^{\lfloor t \rfloor} \binom{n}{x}\theta^x(1-\theta)^{n-x}$
	negative的Bernoulli会考吗 负二项分布的特例:几何分布
- 2. Gauss 分布
		- **Theorem**:  
		  设随机变量 $X$ 服从均值为 $\mu$ ，方差为 $\sigma^2$ 的正态分布：
		  $$
		  X \sim \mathcal{N}(\mu, \sigma^2)
		  $$
		  其概率密度函数（PDF）为：
		  $$
		  P(X) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left(-\frac{(X - \mu)^2}{2\sigma^2}\right)
		  $$
		
	 **Why Gaussian: 中心极限定理（Central Limit Theorem）**  
		  当大量独立同分布的随机变量求和时，其分布趋于正态分布：
		
		  $$
		  Z = \frac{\sum_{i=1}^{n} X_i - n\mu}{\sqrt{n\sigma^2}} \xrightarrow{n \to \infty} \mathcal{N}(0,1)
		  $$
		
	 **In D dimensions**  
		  若 $\mathbf{x}$ 服从 $D$ 维高斯分布：
		  $$
		  \mathbf{x} \sim \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})
		  $$
		  其概率密度函数（PDF）为：
		  $$
		  P(\mathbf{x}) = \frac{1}{(2\pi)^{D/2} |\boldsymbol{\Sigma}|^{1/2}} \exp\left(-\frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \boldsymbol{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})\right)
		  $$
		
		  方差矩阵的特征分解：
		  $$
	  \boldsymbol{\Sigma} = Q \boldsymbol{\Lambda} Q^T
	  $$
	- 3. Poisson 分布
		- **Theorem**:  
		  泊松分布用于建模单位时间或单位空间内的事件发生次数，设随机变量 $X$ 服从参数为 $\lambda$ 的泊松分布：
		  $$
		  X \sim Poisson(\lambda)
		  $$
		  其概率质量函数（PMF）为：
		  $$
		  P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \dots
		  $$
		  期望：
		  $$
		  \mathbb{E}[X] = \lambda
		  $$
		  方差：
		  $$
		  \text{Var}(X) = \lambda
		  $$
		
		- **Sample (202310B-2)**  
		  示例：假设某个网站的用户在 1 分钟内的访问次数符合泊松分布，且均值为 3，即 $\lambda = 3$：
		  $$
	  P(X = 5) = \frac{3^5 e^{-3}}{5!}
	  $$
		  - poisson process
	  - 4. geometic分布
		A random variable $X$ has a **geometric distribution** with parameter $\theta$ if: $$p_X(x) = (1-\theta)^{x-1}\theta, \quad 0 < \theta \leq 1, \quad x = 1, 2, 3, \ldots$$
		We write $X \sim \text{Geometric}(\theta)$.
		**Verification**: $\sum_{x=1}^{\infty} (1-\theta)^{x-1}\theta = \frac{\theta}{1-(1-\theta)} = 1$
		**CDF**: $F_X(x) = 1 - (1-\theta)^{\lfloor x \rfloor}$
		hypergeometic distribution
- 

	  - 