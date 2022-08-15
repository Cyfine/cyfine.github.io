---
title: "The Lottery Ticket Hypothesis"
date: 2022-08-02T19:40:52+08:00
draft: false
author: "Carter Yifeng CHENG"
description: ""
summary: ""
tags: ["ICML", "ICML 2019", "Pruning" ]
categories: ["Paper Reading"]
---

## Summary 


## Research Objective 
<!-- 作者的研究目的 -->
There are recent found that, from a large neural trained network, we can  prune and obtain a small sub network (even 90% of the parameters is being pruned), without compromising the performance. It natural to think that, if we could have a way, train **a small network from the scratch**, also obtains similar performance as the large network, **saving the energy for training**. According to current experience, a pruned sparse network is **hard to train from start**.  

## Problem Statement
<!-- 作者解决问题的方法/算法是什么？是否基于前人的方法？基于了哪些？ -->
The author proposed the **Lottery Ticker Hypothesis**, stating:
>A randomly-initialized, dense neural network contains a subnetwork that is initialized such that—when trained in isolation—it can match the test accuracy of the original network after training for at most the same number of iterations.
## Methods
The training is procedures are
1. Init a large dense network, init with $\theta_0$
2. Train the network
3. Find a mask, prune with Least Weight Magnitude
4. Rest the weight to $\theta_0$, and apply the mask
   
Repeat above steps, prune iteratively. 
## Contribution 
1.  The interesting finding of the lottery ticket hypothesis, that existence of sub network reach better performance and higher accuracy than the original network within fewer iterations. The case under the constraint that the parameter should be the same as the initial param of untrained dense network. 

## Evaluation 
<!-- 作者如何评估自己的方法，实验的setup是什么样的，有没有问题或者可以借鉴的地方。 -->
## Conclusion
<!-- 作者给出了哪些结论，哪些是strong conclusions, 哪些又是weak的conclusions（即作者并不确定，只在discussion中提到，或没有给出足够的evidence）? -->
## Notes 
<!-- 不在以上列表中，但需要特别记录的笔记。 -->
## References
<!-- 列出相关性高的文献，以便之后可以继续track下去。 -->
<!-- p1 Find the context papers -->
Background: 
- Geoffrey Hinton, Oriol Vinyals, and Jeff Dean. Distilling the knowledge in a neural network. arXivpreprint arXiv:1503.02531, 2015. 
- Song Han, Jeff Pool, John Tran, and William Dally. Learning both weights and connections for efficient neural network. In Advances in neural information processing systems, pp. 1135–1143,2015.
- Tien-Ju Yang, Yu-Hsin Chen, and Vivienne Sze. Designing energy-efficient convolutional neural networks using energy-aware pruning. arXiv preprint, 2017.
- Jian-Hao Luo, Jianxin Wu, and Weiyao Lin. Thinet: A filter level pruning method for deep neural network compression. arXiv preprint arXiv:1707.06342, 2017.

