---
title: "A Briefing of Cross Entropy and KL Divergence"
date: 2022-07-19T19:33:24+08:00
draft: true
categories: ["Information Theory"]
tags: ["Entropy", "KL Divergence"]
---
# Information Theory

## The Entropy and Cross-Entropy
### Self Information （自信息）
Considering the scenario that we transport information of a random variable $X$ having different states.
The information can be represented using bits. For instance, if a random variable has two states, it can be represented using a single bit. The amount of bits representing the random variable $X$ is $\log_{2}{2}$. Similarly, if $X$ has three states, the number of bits representing $X$ will be $\log_{2}{8}=3$.  

The above demonstration assuming that each state has equal probability. If $x_i$ has different probability to appear, transmitting $\log_2{n}$ bits for each state is not a optimal solution. For example, if $X$ having three states, the probability distribution of $X$ is
$$ 
p(X=x_1)=0.5, p(X=x_2)=0.25,p(X=x_3)=0.25
$$
We need to use $\log_{2}{3}$, approximately 1.68 bits to encode each state. However, if we use 1 bit for $x_1$, and 2 bits for $x_2$ and $x_3$, on average the number of bits that we need to transmit are
$$
0.5\times1 + 2\times(0.25\times 2) = 1.5
$$ 
which is less than 1.68. Even though for some state we need to use more number of states to represent. The actual information contained in each state is relevant to its probability. Self information is
$$
I(x) =  -\log_2{p(x)}
$$
### Entropy and Cross Entropy
The entropy, measuring how chaos, or much information contained in the random variable having probability distribution $p$.
$$
H(p) = -\sum_{i\in N}p(x_i)\log_{2}{p(x_i )}
$$
The cross entropy is used to measure the difference of two probability distribution. The cross entropy is being represented as:


## Kullback-Leibler Divergence (KL Divergence) 

 
