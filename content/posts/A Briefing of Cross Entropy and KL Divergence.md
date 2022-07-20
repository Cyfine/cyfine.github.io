---
title: "A Briefing of Cross-Entropy and KL Divergence"
date: 2022-07-19T19:33:24+08:00
draft: false
categories: ["Information Theory",  "Statistics"]
tags: ["Entropy", "KL Divergence"]
description: "CE and KL divergence are important concepts to measure how different two distributions are from each other on a statistics point of view. Also, viewing from information theory, KL Divergence measures the information loss / extra information when using distribution q to approximate the distribution p KL(p||q)"
---
## The Entropy and Cross-Entropy
### Self Information
Considering the scenario that we transport information of a random variable $X$ having different states.
The information can be represented using bits. For instance, if a random variable has two states, it can be represented using a single bit. The amount of bits representing the random variable $X$ is $\log_{2}{2}$. Similarly, if $X$ has three states, the number of bits representing $X$ will be $\log_{2}{8}=3$. 

 The actual information contained in each state is correlated to its probability. From the perspective of how many bits to be transferred, the self information is:
$$I(x) =  -\log_2{p(x)}$$

#### More precise definition from Shannon: 
>Claude Shannon's definition of self-information was chosen to meet several axioms:
> 1. An event with **probability 100%** is perfectly unsurprising and yields **no information**.
> 2. The **less probable** an event is, the **more surprising** it is and the **more information** it yields.
> 3. If two independent events are measured separately, the total amount of information is the sum of the self-informations of the individual events.
### Entropy and Cross Entropy
Encoding the each value using number of states of random variables is assuming that each state has equal probability, complying uniform distribution. If $x_i$ has different probability to appear, transmitting $\log_2{n}$ bits for each state is not a optimal solution. For example, all possible values of $X$ are $X = \\{x_1, x_2, x_3\\}$, and the probability distribution of $X$ is
$$ p(x_1)=0.5, p(x_2)=0.25,p(x_3)=0.25$$
We need to use $\log_{2}{3}$, approximately 1.68 bits to encode each state. However, if we use 1 bit for $x_1$, and 2 bits for $x_2$ and $x_3$ (using more bits to encode the value with less probability, vice versa), on average the number of bits that we need to transmit are
$$p(x_1)\log_2{\frac{1}{p(x_1)}} + p(x_2)\log_2{\frac{1}{p(x_2)}} +p(x_3)\log_2{\frac{1}{p(x_3)}}$$
$$0.5\times1 + 2\times(0.25\times 2) = 1.5$$ 
which is less than 1.68, even though we need to use more bits to represent for some states.
The entropy, measuring how chaos, a lower bound indication of information of the random variable with probability distribution $p$ of its values is defined as follows:
$$H(p) = -\sum_{i\in N}p(x_i)\log_{2}{p(x_i )},  \ X=\\{x_1, x_2,\dots, x_N\\}$$

In the actual transmission of the random variable $X$, we use another distribution $q$ guiding us to encode each value of random variable $X$. We are trying to approach the real distribution of random variable $X$ with $q$ to obtain better encoding with fewer bits transferred. The measurement of how similar two distributions is cross-entropy. The cross-entropy is being represented as:
$$
H(p||q) = -\sum_{i\in N}p(x_i)\log_2{q(x_i)} 
$$
## Kullback-Leibler Divergence (KL Divergence) 
Extending from cross entropy, the KL divergence is: 
$$\begin{aligned}
KL(p||q) &= H(p||q) - H(p) \\\\\
        &= -\sum_{i \in N}p(x_i)\log_2{q(x_i)}  - \sum_{i\in N}p(x_i)\log_2{p(x_i)}  \\\\
        &= -\sum_{i \in N}p(x_i)\log_2{\frac{q(x_i)}{p(x_i)}}
\end{aligned}$$
Measuring if using distribution $q$ to approximate $p$, the extra information loss/overhead. So, smaller the KL divergence is, the more similar two distributions are. 

### Properties
#### Positive Definiteness  
$$D_{K L}(p \| q) \geq 0$$

By Gibbs Inequality:
if $\sum_{i=1}^{n} p_{i}=\sum_{i=1}^{n} q_{i}=1$ and $p_{i}, q_{i} \in(0,1]$, then
$$-\sum_{i}^{n} p_{i} \log p_{i} \leq-\sum_{i}^{n} p_{i} \log q_{i}$$
The equal signs takes if and only if $p_{i}=q_{i} \forall i$
#### Asymmetric
$$D(p \| q) \neq D(q \| p)$$

## References
* [KL Divergence Explained](https://www.countbayesie.com/blog/2017/5/9/kullback-leibler-divergence-explained)
*  [Self-information - Wikipedia](https://en.wikipedia.org/wiki/Information_content)