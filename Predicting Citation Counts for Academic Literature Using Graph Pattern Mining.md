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

