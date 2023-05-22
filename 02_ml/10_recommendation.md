# 推荐系统

## 业务
CVR (Conversion Rate): 转化率

## 思路
召回、排序、策略

### 召回
- 统计类，热度，LBS
- 协同过滤类，UserCF、ItemCF
- U2T2I，如基于user tag召回
- **I2I**，如Embedding（Word2Vec、FastText），GraphEmbedding（Node2Vec、DeepWalk、EGES）
- U2I，如DSSM、YouTube DNN、Sentence Bert

### 排序
learning to rank 流程三大模式（point-wise、pair-wise、list-wise），主要是特征工程和CTR模型预估
- 常见的特征挖掘（user、item、context，以及相互交叉）
- 粗排：**双塔**
- 精排：**MLP**
- CTR预估，如LR、GBDT、FM、FFM、DNN、Wide&Deep、DCN、DeepFM、DIN、DFN
- 多目标多场景：MMOE
- 特征：user, item, context

### 探索与发现（bandit、Q-Learning、DQN）


### 推荐理由
- 统计式，如：全城热搜、区域热搜；
- 行为，如：看过、买过、看了又看、搜了又搜；
- 推荐语生成（抽取式，生成式）


## 问题
### how to scale
### serve personalized recommendations at a low latency

### Bias
- selection bias
- positional bias
- online/offline data distribution bias
- fairness
- popularity bias
- https://zhuanlan.zhihu.com/p/518175104

### 冷启动


### 长尾问题

### 模型细节

item average_pooling和sum_pooling的区别
- 从反向传播角度看相当于学习率砍了N倍。DIN似乎效果一般

[双塔的优化](https://www.zhihu.com/question/314773668/answer/2259594886)
- 让user和item更有效地交互
- 让单路召回达到多路的效果
- 面向后链路的一致性建模
- 各种工业经验trick，包括但不限于特征、结构、loss

## 论文

[Deep Neural Networks for YouTube Recommendations](https://cseweb.ucsd.edu/classes/fa17/cse291-b/reading/p191-covington.pdf)
- 目标：观看时长 （可减少标题党推荐，是否会影响长短视频bias）
  - 通过改变样本权重来预测观看时长。正样本权重就是时长，负样本权重为1

- 召回 
  - 抽象成一个海量类别的多分类问题
  - 单塔: embed -> avg -> concat embed -> MLP
  - 训练：超多分类通过sample negative classes, in-batch loss 随机采样；测试：近邻 
  - 推理：

- 排序

[Sampling-Bias-Corrected Neural Modeling for Large Corpus Item Recommendations]()

- 召回
  - 双塔
  - user在线serving，item离线计算后索引
  - 负样本为王，不光是点击未曝光
  - 无效曝光：返回、遮挡、 重复上报

[Real-time Personalization using Embeddings for Search Ranking at Airbnb]()

## 业务优化
- 多检查数据规律
- 是否share embedding
- 多目标训练


## 参考
- https://github.com/twitter/the-algorithm
- https://github.com/tangxyw/RecSysPapers
- [互联网大厂的这些推荐算法面试题，你都能答上来吗？ - 石塔西的文章 - 知乎](https://zhuanlan.zhihu.com/p/627578461)
- [Swing算法介绍、实现与在阿里飞猪的实战应用](https://zhuanlan.zhihu.com/p/364593067)
- [EasyRec](https://github.com/alibaba/EasyRec)
