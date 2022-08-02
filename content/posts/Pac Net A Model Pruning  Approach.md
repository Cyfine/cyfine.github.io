---
title: "Pac Net a Model Pruning  Approach"
date: 2022-08-02T11:31:28+08:00
draft: false
author: "Carter Yifeng CHENG"
description: ""
summary: ""
tags: ["ICML 2022", "Pruning", "ICML",  "Transfer Learning"]
categories: ["Paper Reading"]
---

## 1. Abstract

When using over-parameterized model, the author found the model can be pruned without losing most of the accuracy. 
* The author identifies the essential weight using LWM to obtain mask. 
* For pruned model, train on source domain with regularization. 
* Then, transfer the model on the target domain, freeze un-pruned parameter on the source domain, train only the parameter being pruned on the target domain. 

## 2. Contribution 

* Very first using pruning in transfer learning.
* First using transfer learning to solve ODE and PDE. 
* Using pruning with regularization to achieve SOTA as claimed
  
### 2.1. Idea 

* Using prune techniques in transfer learning.
* For a large model, it considers prune as optimal weight search, the unpruned part of the model on the source domain is being freezed when training on the target domain. Utilize the rest of model capacity (the pruned part of the model)on the target domain. 
  
## 3. Proposed Framework
### 3.1. Pruning
Prune using LWM, only preserve the largest K weights of the original source trained model, rest of the weights are being pruned. 
$$
m^{i}= \begin{cases}1, & \text { if }\left|w^{i}\right|>w_{\kappa} \\\\ 0, & \text { otherwise }\end{cases}
$$
### 3.2. Allocation

After pruned the model with the LWM $k$-th largest mask, on the source domain, train the pruned model with regularization. The regularization method being used is  

$$
\Omega(\mathbf{w})=\lambda||\mathbf{w}-\mathbf{w}_{S}||^{2}=\lambda \sum\_{i=1}^{D}||w^{i}-w\_{S}^{i}||^{2}
$$
This is the **starting point regularization**, encourages the transferred target weight should be close to the initial source weight to avoid catastrophic forgetting. 
>It is because some
important weights may be driven far away from their initial $w_S$
### 3.3. Calibration 
This step is train on the target domain. First, unpruned weight train on the source domain is frozen. The parameter update is being applied on the pruned weight. The main idea maybe to utilize the unused capacity of the model.  
