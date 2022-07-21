---
title: "Fisher Information"
date: 2022-07-19T19:32:13+08:00
draft: true
categories: [“Statistics]
---
We may measure a random varaible indirectly. However the indirect measurement is being affect by the noise follows a certain distribution, thus the measurement is represetend by a random variable follows a certain distribution. For example, we want to measure $\theta$, the tempreate of the stomache, it can be measured by measuring the tempreature of the mouth $Y$. 
$$Y = \theta + W$$
$W$ is the noise that folows the normal distribution $N\sim(0,\sigma)$. If $Y$ is very informative regards to $\theta$, the measurement of $Y$ with different $\theta$ will be very different. If $\sigma$ is large, 
$$
I_{Y}(\theta)=E\left[\left(\frac{\partial}{\partial \theta} \ln f(Y ; \theta)\right)^{2}\right]
$$