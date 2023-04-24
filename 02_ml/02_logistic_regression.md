# 逻辑回归

- numpy手写一个logistic regression

```

import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import norm

np.random.seed(1)
class Logistic_regression(object):
    def __init__(self):
        self.w = None
        self.b = None
        self.epsilon = 1e-8
        self.activate=self.sigmoid

    def fit(self,x,y):
        batch_size, feature_size = x.shape
        self.w = np.random.random((feature_size, 1))
        self.b = np.random.random(1)
        self._gradient_descent(x, y)

    def eval(self,x,y):
        pass

    def predict(self,x):
        prob=self.activate(np.dot(x,self.w)+self.b)
        return prob

    def plot(self):
        pass

    def _gradient_descent(self,x, y,learning_rate=10e-4,epoch=100):
        for i in range(epoch):
            y_pred = self.activate(np.dot(x, self.w) + self.b)
            loss = np.mean(-y * np.log(y_pred+self.epsilon) - (1 - y) * np.log(1 - y_pred+self.epsilon))
            w_gradient = np.dot(x.T, (y_pred - y))
            b_gradient = np.mean(y_pred - y)
            self.w = self.w - learning_rate * w_gradient
            self.b = self.b - learning_rate * b_gradient
            print('step:', i, 'Loss:', loss)

    def sigmoid(self,input):
        return 1 / (1 + np.exp(-input))

    def __str__(self):
        return 'weights\t:%s\n bias\t:%f\n' % (self.w, self.b)

def generate_data():
    x0=np.hstack((norm.rvs(2,size=40,scale=2),
                 norm.rvs(8,size=40,scale=3)))
    x1 = np.hstack((norm.rvs(4, size=40, scale=2),
                    norm.rvs(5, size=40, scale=2)))
    x=np.transpose(np.vstack((x0,x1)))
    y=np.vstack((np.zeros((40,1)),
                 np.ones((40,1))))
    #indices=np.random.shuffle(range(len(x)))
    return x,y

if __name__ == "__main__":
    x,y=generate_data()
    lr=Logistic_regression()
    lr.fit(x,y)
    y_hat=lr.predict(x)
    print(y_hat)
    print(y)

```

## 场景优化
- 正负样本不平衡

欠采样（undersampling）和过采样（oversampling）会对模型带来怎样的影响？ - Quan的回答 - 知乎
https://www.zhihu.com/question/269698662/answer/350806067

- 并行
逻辑回归并行化主要是对目标函数梯度计算的并行化

## 问答
- 为什么逻辑回归不用mse做损失函数

[本质是分布不同；公式推导发现容易导致梯度消失，很大的话梯度有一项会趋于0；陷入局部最优](https://zhuanlan.zhihu.com/p/453411383)

- 