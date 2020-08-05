# Predicting Citation Counts for Academic Literature Using Graph Pattern Mining

## 概述

1. 通过引用网络来预测引文计数

2. 预测网络中链路的出现

3. 挖掘图模式
4. GERscore

## 方法

1. 分类

   根据给定的特征向量预测引用次数的特定范围

2. 回归

   根据特征向量预测引用次数的值

构建引用网络

![image-20200805185412333](Predicting%20Citation%20Counts%20for%20Academic%20Literature%20Using%20Graph%20Pattern%20Mining.assets/image-20200805185412333.png)

入度代表该论文的入度，年份作为额外属性

## 相关工作

1. 作者先前论文的引用数比较重要
2. 发表的会议和参考文献累积的引用数效果更显著
3. 被高引用的论文在引用其他论文时具有共同的特征
4. 分类与回归两种方式

## GERscore

### 1 挖掘图演化规则

$G=(V, E, \lambda, \tau)$

$\lambda$代表一个函数，为每个节点分配标签，$\tau$定义一个函数描述时间戳

**相对时间戳**：

**演化规则的定义**：

balabala

### 2 计算GERscore

$$
\begin{array}{l}
\text { GERscore }_{1, i}(n)=\sum_{r \in \mathcal{R}_{n}} \text { score }_{i}(n, r), \\
\text { GERscore }_{2, i}(n)=\max _{r \in \mathcal{R}_{n}} \text { score }_{i}(n, r)
\end{array}
$$

GERscore越高，引用数就可能越多

## 实验

### 数据

使用 *Hepth* 和 *ArnetMiner* 第一个是高能物理类，arXiv，1992～2003，第二个是计算机，2000年之前

增加两个属性组：参考文献数量（0-1，2-5，6-14，15+），作者数量（1，2，3，4-6，7+）

计算三个GERscore值

### 设置

**分类任务**：多项式Logistic回归、支持向量机、条件推理树

**回归任务**：线性回归、支持向量回归、分类回归树

增加了几个特征：作者排名，作者过去总影响力（TPIA），作者过去最大影响力（MPIA），地点排名， 场地（TPIV）和场地的最大过去影响（MPIV）

### 分析

1. GERscore效果显著
2. 作者相关的信息很重要
3. CART在回归任务重效果表现较好，logistics在分类任务重表现较好

![截屏2020-08-05 下午10.30.20](Predicting%20Citation%20Counts%20for%20Academic%20Literature%20Using%20Graph%20Pattern%20Mining.assets/%E6%88%AA%E5%B1%8F2020-08-05%20%E4%B8%8B%E5%8D%8810.30.20.png)

