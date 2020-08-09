# A Neural Citation Count Prediction Model based on Peer Review Text

## 概述

根据同行评阅数据，使用神经网络，预测论文引用数。

### 难点

1. 以自然语言编写
2. 可能不会侧重于论文的贡献，包括诸如拼写错误、格式错误等内容
3. 侧重不同方面，
4. 在同一方面提出不同的态度
5. 要各个方面都考虑，来对论文影响作出全面决策

### 方法

1. 摘要评论匹配方法
2. 交叉评论匹配机制

### 相关工作

用于论文验收

## 问题表述

$$
f\left(\boldsymbol{x}_{d}, \boldsymbol{a}_{d},\left\{\boldsymbol{r}_{k}\right\}_{k=1}^{K}\right) \rightarrow \hat{c}_{d}
$$

## 模型

![截屏2020-08-08 上午9.58.35](A%20Neural%20Citation%20Count%20Prediction%20Model%20based%20on%20Peer%20Review%20Text.assets/%E6%88%AA%E5%B1%8F2020-08-08%20%E4%B8%8A%E5%8D%889.58.35.png)

![截屏2020-08-08 上午10.04.34](A%20Neural%20Citation%20Count%20Prediction%20Model%20based%20on%20Peer%20Review%20Text.assets/%E6%88%AA%E5%B1%8F2020-08-08%20%E4%B8%8A%E5%8D%8810.04.34.png)

### 深度部分

将摘要和评论句子编码为嵌入向量，然后通过引用摘要从评论文本中提取相关特征。 为了表征多个审阅者之间的互动，设计了一种跨审阅匹配机制，以捕获不同审阅之间的一致性和差异性。

#### 1 编码摘要和评论

#### 2 摘要审阅匹配机制

为了匹配评论中与主题有关的信息，使用基于门控注意力的循环网络，考虑摘要与单个评论间的相互作用

#### 3 交叉审阅机制

通过交叉审阅，综合考虑各个评审员之间的关系

将原始评论分解为并行表示和正交表示

### 广度部分

1. 使用LDA学习主题概率分布
2. 计算主题分布的熵，衡量论文主题的广度
3. 使用出版年份作为时间特征
4. 使用作者人数和平均H指数作为作者特征

### 组合

$$
\hat{c}_{d}=\tanh \left(\boldsymbol{w}_{\text {deep}}^{\top} \cdot \boldsymbol{z}_{d}+\boldsymbol{w}_{\text {wide}}^{\top} \cdot \boldsymbol{x}_{d}+b\right)
$$

$$
L(\theta)=\frac{1}{|\mathcal{D}|} \sum_{d \in \mathcal{D}}\left(\hat{c}_{d}-c_{d}\right)^{2}
$$

正态分布初始化、SGD优化器

## 实验

全面超越

## 总结

摘要审阅匹配机制和交叉审阅机制是该论文的特色，将来可以考虑评论文本的情感建模