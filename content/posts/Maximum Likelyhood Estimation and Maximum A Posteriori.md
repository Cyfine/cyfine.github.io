---
title: "Maximum Likelihood Estimation and Maximum A Posterior"
date: 2022-07-22T20:02:09+08:00
draft: false
author: "Carter Yifeng CHENG"
summary: "Given observed data, MLE and MAP find the parameters of the distribution that maximize the probability of observed data. Compares to MLE, MAP considers prior information of theta while MLE does not"
tags: ["Maximum Likelihood Estimation","Maximum A Posterior"]
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
$$\text { let: } \ln ^{\prime}(p(X \mid \theta))=0, \ \theta=0.6$$
The MLE has no clue about the prior distribution of the parameters $\theta$. **MLE considers no occasionality** of the experiment when the data sample is **insufficient**. Maybe, the real distribution is 90% of the balls are white balls, and we are just lucky to draw six times black balls in the 10-time sampling. Suppose we have some prior information about the real distribution. For example, if our prior information is that the parameter $\theta\sim N(0.1,1)$. According to our prior, $p(\theta=0.6)$ will be very small. If our case in the MLE is exceptional and our prior is close to the real distribution of $\theta$, then the MAP will give a better estimation. The term $\ln(p(\theta))$ is **like a regularization term**, preventing a possible faulty estimation due to exceptional observation of the data. Under the case that the prior distribution of $\theta$ is close to real or the observation of $X$ is sufficient to prevent the exceptional case, MAP and MLE will be similar.
$$
\begin{aligned}
\theta_{\text {MAP }} &=\underset{\theta}{\operatorname{argmax}}\  p(\theta \mid X) \\\\
&=\underset{\theta}{\operatorname{argmax}}\  \ln (p(\theta \mid X))\\\\
&=\underset{\theta}{\operatorname{argmax}}\  \ln (p(X \mid \theta) \cdot p(\theta)) \\\\
&=\underset{\theta}{\operatorname{argmax}}\  \ln (p(X \mid \theta))+\ln (p(\theta))
\end{aligned}
$$
At line 3 of the above equation, the $p(X)$ is omitted, as doing so does not affect the result. The $MAP$ has one extra $\ln(p(\theta))$ term. 