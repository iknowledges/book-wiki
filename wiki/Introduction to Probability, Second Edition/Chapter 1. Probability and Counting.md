## 1.2 Sample spaces and Pebble World

#### **Sample space and event**

The sample space $S$ of an experiment is the set of all possible outcomes of the experiment. An event $A$ is a subset of the sample space $S$, and we say that $A$ occurred if the actual outcome is in $A$.

> page 3

## 1.3 Naive definition of probability

#### **Naive definition of probability**

Let $A$ be an event for an experiment with a finite sample space $S$. The naive probability of $A$ is

$$
P_{\mathrm{naive}}(A)=\frac{|A|}{|S|}=\frac{\text{number of outcomes favorable to }A}{\text{total number of outcomes in }S}.
$$

(We use $|A|$ to denote the size of A.)

> page 6

## 1.4 How to count

#### **Multiplication rule**

Consider a compound experiment consisting of two sub-experiments, Experiment A and Experiment B. Suppose that Experiment A has $a$ possible outcomes, and for each of those outcomes Experiment B has $b$ possible outcomes. Then the compound experiment has $ab$ possible outcomes.

> page 8

#### **Sampling with replacement**

Consider $n$ objects and making $k$ choices from them, one at a time with replacement (i.e., choosing a certain object does not preclude it from being chosen again). Then there are $n^k$ possible outcomes (where order matters, in the sense that, e.g., choosing object 3 and then choosing object 7 is counted as a different outcome than choosing object 7 and then choosing object 3.)

> page 11

#### **Sampling without replacement**

Consider $n$ objects and making $k$ choices from them, one at a time without replacement (i.e., choosing a certain object precludes it from being chosen again). Then there are $n(n-1)\cdots(n-k+1)$ possible outcomes for $1\leq k\leq n$, and 0 possibilities for $k>n$ (where order matters). By convention, $n(n-1)\cdots(n-k+1)=n$ for $k=1$.

> page 12

#### **Permutation**

A permutation of $1,2,\ldots,n$ is an arrangement of them in some order, e.g., $3,5,1,2,4$ is a permutation of $1,2,3,4,5$.

> page 12

#### **Binomial coefficient**

For any nonnegative integers $k$ and $n$, the binomial coefficient $\binom{n}{k}$, read as “$n$ choose $k$”, is the number of subsets of size $k$ for a set of size $n$.

> page 15

#### **Binomial coefficient formula**

For $k\leq n$, we have

$$
\binom{n}{k}=\frac{n(n-1)\cdots(n-k+1)}{k!}=\frac{n!}{(n-k)!k!}.
$$

For $k>n$, we have $\binom{n}{k}=0$.

> page 15

## 1.5 Story proofs

#### **Story proof**

A story proof is a proof by interpretation. For counting problems, this often means counting the same thing in two different ways, rather than doing tedious algebra. A story proof often avoids messy calculations and goes further than an algebraic proof toward explaining why the result is true. The word “story” has several meanings, some more mathematical than others, but a story proof (in the sense in which we’re using the term) is a fully valid mathematical proof.

> page 20

## 1.6 Non-naive definition of probability

#### **General definition of probability)**

A probability space consists of a sample space $S$ and a probability function $P$ which takes an event $A\subseteq S$ as input and returns $P(A)$, a real number between 0 and 1, as output. The function $P$ must satisfy the following axioms:

1. $P(\emptyset)=0$, $P(S)=1$.
2. If $A_1,A_2,\ldots$ are disjoint events, then

$$
P\!\left(\bigcup_{j=1}^{\infty} A_j\right)=\sum_{j=1}^{\infty}P(A_j).
$$

(Saying that these events are disjoint means that they are mutually exclusive: $A_i \cap A_j=\emptyset$ for $i\neq j$)

> page 22

#### **Properties of probability**

Probability has the following properties, for any events $A$ and $B$.

1. $P(A^c)=1-P(A)$.
2. If $A\subseteq B$, then $P(A)\leq P(B)$.
3. $P(A\cup B)=P(A)+P(B)-P(A\cap B)$.

> page 23

#### **Inclusion-exclusion**

For any events $A_1,\ldots,A_n$,

$$
P\!\left(\bigcup_{i=1}^{n}A_i\right)=\sum_{i}P(A_i)-\sum_{i<j}P(A_i\cap A_j)+\sum_{i<j<k}P(A_i\cap A_j\cap A_k)-\cdots+(-1)^{n+1}P(A_1\cap\cdots\cap A_n).
$$

> page 25
