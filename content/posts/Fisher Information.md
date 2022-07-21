---
title: "Fisher Information"
date: 2022-07-19T19:32:13+08:00
draft: true
categories: ["Statistics"]
---
## Introduction
We may measure a random variable indirectly. However, the indirect measurement is affected by the noise following a certain distribution. Thus, the measurement is represented by a random variable that follows a certain distribution. For example, we want to measure $\theta$, the temperate of the stomach, and it can be measured by measuring the mouth's temperature $Y$. 
$$Y = \theta + W$$
$W$ is the noise that follows the normal distribution $N\sim(0,\sigma)$. If $Y$ is very informative regarding $\theta$,  $Y$ with different $\theta$ should be distinguishable. If $\sigma$ is large, the distribution of $Y$ is splattered, and the $Y$ with different $\theta$ will 
overlap largely, which is less distinguishable. The less indicative $Y$ contains less information about $\theta$. How informative the random variable $Y$ is regarding $\theta$ can be measured using Fisher information.

$$
I_{Y}(\theta)=E\left[\left(\frac{\partial}{\partial \theta} \ln f(Y ; \theta)\right)^{2}\right]
$$


## References 
1. [What is Fisher information? - YouTube](https://www.youtube.com/watch?v=82molmnRCg0)