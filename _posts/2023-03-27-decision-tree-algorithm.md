---
layout: post
title: Decision Tree Algorithm
date: 2023-3-27
categories: blog
tags: [Machine Learning,Classical Algorithm,学习笔记]
description: Decision Tree Algorithm。
---


#### Synopsis

决策树模型层树形结构，在分类问题中，表示基于特征对实例进行分类的过程。它可以被认为是if-then规则的集合，也可以认为是定义在特征空间与类空间上的条件概率分布。

决策树学习通常包括3个步骤：特征选择、决策树生成和决策树的修剪。

#### Defination

分类决策树模型是一种描述对实例进行分类的树形结构。决策树由点（Node）和有向边（directed edge）组成。节点有两种类型：内部节点（internal node）和叶节点（leaf node）。内部节点表示一个特征（pattern）或者属性（feature），叶节点表示一个类（label）。

用决策树对需要测试的实例进行分类：从根节点开始，对实例的某一特征进行测试，根据测试结果，将实例分配到其子节点；这时，每一个子节点对应着该特征的一个取值。如此递归的对实例进行测试并分类，直至到达叶节点。最后将实例分配到叶节点的类中。

#### Information entropy & Information gain

熵（entropy）：熵指的是体系的混乱的程度，在不同的学科中也有引申出的更为具体的定义，是各领域十分重要的参量。

信息论（information theory）中的熵（香农熵）: 是一种信息的度量方式，表示信息的混乱程度，也就是说: 信息越有序，信息熵越低。例如: 火柴有序放在火柴盒里，熵值很低，相反，熵值很高。

信息增益（information gain）: 在划分数据集前后信息发生的变化称为信息增益。

#### 创建决策树

```
def createBranch():
'''
此处运用了迭代的思想。 感兴趣可以搜索 迭代 recursion， 甚至是 dynamic programing。
'''
    检测数据集中的所有数据的分类标签是否相同:
        If so return 类标签
        Else:
            寻找划分数据集的最好特征（划分之后信息熵最小，也就是信息增益最大的特征）
            划分数据集
            创建分支节点
                for 每个划分的子集
                    调用函数 createBranch （创建分支的函数）并增加返回结果到分支节点中
            return 分支节点
```

分析数据

其中p(x_i)是选择该分类的概率。

为了计算熵，我们需要计算所有类别所有可能值包含的信息希望值，通过下面公式得到：
$$
H=-\sum^{n}_{i=1}{p(x_i)log_2p(x_i)}
$$

#### 算法特点

优点: 计算复杂度不高，输出结果易于理解，数据有缺失也能跑，可以处理不相关特征。 

缺点: 容易过拟合。 适用数据类型: 数值型和标称型。