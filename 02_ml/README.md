# 机器学习

- 常见模型的原理和局限
- 手写基础算法
  - 写实现两层fully connected网络
  - 手写CNN
  - 手写KNN
  - 手写K-means
  - 手写softmax的backpropagation
  - 手写AUC
  - 手写SGD
  - 视觉：手写iou/nms

- 延伸
  - 给一个LSTM network的结构，计算how many parameters
  - convolution layer的output size怎么算? 写出公式
  - 设计一个sparse matrix (包括加减乘等运算)

## 八股文

- 怎么解决nn的overfitting/underfitting

过拟合：从数据角度，收集更多训练数据。求其次的话，数据增强方法。降低模型复杂度，如神经网络中的层数、宽度，树模型中的树深度、剪枝。模型正则化方法，如正则约束L2。集成学习方法，bagging方法。

欠拟合：增加新特征，增加模型复杂度，减少正则化系数。训练模型的第一步就是要保证能够过拟合。

- 优化器，如何选择优化器


- 数据收集


- 模型选择


- 推荐，scale\abtesting\trouble shooting
