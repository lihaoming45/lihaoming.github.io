---
title: Modular Grasping Policy
tags: paper structure
grammar_cjkRuby: true
---

## Introduction


### Background

 - 论述当前机械爪抓取工作的主要研究方向，指出其中大家比较忽略的问题——专注于提高机械爪对不同物体的抓取泛化能力，但却忽视机械爪之间的泛化能力的研究
 - 论述机械爪之间泛化能力的重要性和机械爪泛化能力的相关工作
 - 介绍模块化方法的优异性和相关工作
### Our work
 - 将模块化方法应用于机械抓取，提出一种能够在保持机械爪能够抓取不同物体的同时，也能提高机械爪之间抓取的泛化能力的通用抓取策略，并简单介绍我们的方法

###  Contribution

 - 将Graph Network应用于机械爪抓取中
 - 训练了一种共享抓取策略，可以有效地解决机械爪之间泛化能力不足的问题
- [==未完成 #F44336== ]   graph attention network

## Related Work

 - 基于图像抓取的相关工作
 - 基于强化学习抓取的相关工作
 - 模块化方法的相关工作


## Modular Grasping Policy

 - Image + Graph + RL
 
	 - Image 降采
	 - Graph 结构描述、节点和边的表示、节点的状态向量
	 - RL obs和reward设计（可参照affordeance那篇论文的表述方法）

- [==未完成 #F44336== ]   Grasp Attention Network
	- 结构描述
	- connectivity mask设计
	- （如果这部分可以做出来需要和前一部分进行再整理）


## Experiment

 - 机械爪模型介绍，被抓取物体介绍
 - exp1: comparison between whole grasping and modular grasping
	 - baseline 介绍(whole grasping) !!!说法可能不正式
	 - 实验设计：跑四个不一样的机械爪环境抓取同一个物体
	 - 实验结果：实验结果对比图（reward曲线）
	 - 实验分析：从收敛速度，收敛高度分析
- exp2: gripper genelization（或称MGSO， multi grippers single object）
	- 实验设计：
		- 使用多个机械爪环境抓取同一个物体，共同训练一个策略
		- 训练好的策略去测试没有在训练中出现的机械爪
	- 实验结果：
		- 训练结果，reward曲线
		- 测试结果，reward曲线
		- 在上述两种曲线中添加对比曲线，即使用modular方法分别跑对应机械爪的reward曲线，比较共同训练和单独训练的差异
	- 实验分析：与实验一类似
- exp3: 多对象泛化实验（或称MGMO, multi grippers multi objects）
	- 实验设计：
		- 使用多个机械爪抓取多个物体进行共同策略的训练
		- 训练好的策略去测试没有在训练中出现的机械爪去抓取没有见过的物体
		- 实验分成两组，简单规则物体与日常生活物体
	- 实验结果：
		- 训练结果，reward曲线
		- 测试结果，reward曲线
		- 在上述两种曲线中添加对比曲线，即使用modular方法分别跑对应机械爪（这个是单爪多物体的环境）的reward曲线，比较共同训练和单独训练
		- 抓取日常生活用品的成功率（表格）可以和整体抓取进行对比
	- 实验分析：
		- T-SNE可视化抓取过程当中关节的特征向量变化，观察关节的聚类情况

## Conclusion

总结提出的方法，提出不足和未来的方向
	   