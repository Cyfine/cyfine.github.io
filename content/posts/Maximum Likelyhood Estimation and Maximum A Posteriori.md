---
title: "Maximum Likelihood Estimation and Maximum A Posterior"
date: 2022-07-22T20:02:09+08:00
draft: false
author: "Carter Yifeng CHENG"
summary: "Given observed data, MLE and MAP find the parameters of the distribution that maximize the probability of observed data. Compares to MLE, MAP considers prior information of theta while MLE does not"
tags: ["Maximum likelihood estimation","Maximum A Posterior"]
categories: ["Statistics"]
---
Assume we have a box filled with balls in two colors, black and white. We do not know the ratio of black to white balls, and we take a simple random sampling with replacement. The color of the ball is a random variable $X$. The distribution of the balls in the box is represented by the percentage of the black balls, denoted as $\theta$. Assume sampling ten times, and six times the ball is drawn black. We assume the $\theta$ is 0.6 intuitively because we believe it is the most likely distribution to obtain the experiment outcome. In the words of MLE,  we are finding the given $\theta$ that maximizes the probability of the experiment outcome. 

$$ 
\begin{aligned}
\theta_{M L E}&=\underset{\theta}{\operatorname{argmax}} \ p(X \mid \theta)\\\\
&=\underset{\theta}{\operatorname{argmax}} \ \ln (p(X \mid \theta))\\\\
&=\underset{\theta}{\operatorname{argmax}}\  \ln \left(\theta^{6}(1-\theta)^{4}\right)\\\\
&=\underset{\theta}{\operatorname{argmax}}\  6 \ln \theta+4 \ln (1-\theta)\\\\
\end{aligned}
$$
$$\text { let: } \ln ^{\prime}(p(x \mid \theta))=0, \ \theta=0.6$$
The MLE has no clue about the prior distribution of the parameters $\theta$. **MLE considers no occasionality** of the experiment when the data sample is **insufficient**. Maybe, the real distribution is 90% of the balls are white balls, and we are just lucky to draw six times black balls in the 10-time sampling. If we have some prior information about the real distribution. For example, we have a coin and want to measure the probability of the coin giving a head. Using $\theta$ to denote the probability of the coin giving a head. Since most of the coin gives fifty-fifty percent of head or tail, so our prior information is  $\theta=0.5$
$$
\begin{aligned}
\theta_{\text {MAP }} &=\underset{\theta}{\operatorname{argmax}}\  p(\theta \mid x) \\\\
&=\underset{\theta}{\operatorname{argmax}}\  \ln (p(\theta \mid x))\\\\
&=\underset{\theta}{\operatorname{argmax}}\  \ln (p(x \mid \theta) \cdot p(\theta)) \\\\
&=\underset{\theta}{\operatorname{argmax}}\  \ln (p(x \mid \theta))+\ln (p(\theta))
\end{aligned}
$$
At line 3 of the above equation, the $p(x)$ is omitted, as doing so does not affect the result. The $MAP$ has one extra $\ln(p(\theta))$ term. In the regularization