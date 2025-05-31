### 引入
**例子**：假设你是一个医生，面对一种疾病：

- **已知条件**：
    
    - 人群患病概率（先验概率）P(Disease)=1%P(Disease)=1%。
        
    - 如果患病，检测呈阳性的概率（似然）P(Positive∣Disease)=95%P(Positive∣Disease)=95%。
        
    - 如果未患病，检测呈阳性的概率（假阳性）P(Positive∣No Disease)=5%P(Positive∣No Disease)=5%。

**问题**：如果一个人检测呈阳性，实际患病的概率是多少？求 P(Disease∣Positive)P(Disease∣Positive)？
### Definition
本质理解：A和B同时发生的 = A发生的前提下 B发生了 = B发生的前提下 A发生了

For events $A, B \in \mathcal{F}$ with $P[A] \neq 0$: $$P[B|A] = \frac{P[A \cap B]}{P[A]}$$
### Independence

Events ${A_i}_{i=1}^n$ are **pairwise independent** if for all $i \neq j$: $$P[A_i \cap A_j] = P[A_i]P[A_j]$$

### Bayes' Theorem

Let ${A_i}_{i \in I}$ be a partition of $\Omega$, and $B$ be an event with $P[B] \neq 0$: $$P[A_i|B] = \frac{P[B|A_i]P[A_i]}{\sum_{j \in I} P[B|A_j]P[A_j]}$$

**Special case**: For events $A, B$ with $P[B] \neq 0$: $$P[A|B] = \frac{P[B|A]P[A]}{P[B|A]P[A] + P[B|A^c]P[A^c]}$$
