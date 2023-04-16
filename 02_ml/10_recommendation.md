# 推荐系统
- how to scale

## Bias
- selection bias
- positional bias
- online/offline data distribution bias
- fairness
- popularity bias
- https://zhuanlan.zhihu.com/p/518175104


## 细节

item: average_pooling和sum_pooling的区别，从反向传播角度看相当于学习率砍了N倍。DIN似乎效果一般

## 论文

[Deep Neural Networks for YouTube Recommendations](https://cseweb.ucsd.edu/classes/fa17/cse291-b/reading/p191-covington.pdf)

- 召回 
  - 单塔: embed -> avg -> concat embed -> MLP
  - sample negative classes, in-batch loss 随机采样
  - 线下训练L：
  - 线上推理：
- 排序

[Sampling-Bias-Corrected Neural Modeling for Large Corpus Item Recommendations]()
- 召回
  - 双塔
  - user在线serving，item离线计算后索引
  - 负样本为王，不光是点击未曝光
  - 无效曝光：返回、遮挡、 重复上报

## 参考
- https://github.com/twitter/the-algorithm
- https://github.com/tangxyw/RecSysPapers