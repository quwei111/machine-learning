# 线性回归

线性回归是最基础的统计学习模型。

在监督学习中，需要有学习的材料-特征，也有学习的目标-label。当label是连续量时，被称为回归。

## 1.最小二乘法 （矩阵表达，几何意义）

$$ y=w^Tx +b $$

$$ w,b=\mathop {argmin} _{w,b}Loss $$

Loss: 

$$ L=\frac{1}{n}\sum_{i=1}^{n}{(y-\hat{y})^2} $$

$$ L= (y-w^TX)^{T}(y-w^TX) $$

$$ L=y^Ty-y^Tw^TX-X^Twy+y^Ty+X^Tww^TX $$

$$ \frac{\partial{L}}{\partial{w}}=2X^TXw-2X^Ty$$

## 2.最大似然
最小二乘与最大似然的等价

$$ w,b= argmax(logP(x|w)) $$

频率派与贝叶斯派，

$$ P(w|X)=\frac{P(X|W).P(w)}{P(X)} $$


最大似然需要假设分布，对于一般线性回归的假设即是


## 3.最大后验

L1与L2理论涉及到朗格朗日优化。

### L1正则

#### 几何解释
#### MAP
$$ w=argmax(P(w|X))=argmax(P(X|w).P(w)) $$

### L2正则





## 4.高斯过程


## 5.场景优化

## 代码
 

```
# 2018.01.26 Learning_rate too large cause the gradient explosion
import numpy as np
import matplotlib.pyplot as plt
np.random.seed(1)


class LinearRegression(object):
    def __init__(self):
        self.w=None
        self.b=None

    def fit(self,x,y):
        batch_size,feature_size=x.shape
        self.w=np.random.random((feature_size, 1))
        self.b=np.random.random(1)
        self._gradient_descent(x,y)

    def eval(self):
        pass

    def predict(self,x):
        y_hat=np.dot(x,self.w)+self.b
        return y_hat

    def plot(self,x,y,y_pred):
        plt.plot(x, y, 'r-')
        plt.plot(x, y_pred, 'b.')
        plt.show()

    def _gradient_descent(self,x,y,learning_rate=0.0001,epoch=100):
        for i in range(epoch):
            y_hat=self.predict(x)  # => batch_size*1
            loss=np.dot((y_hat-y).T,(y_hat-y))
            w_gradient = np.dot(x.T, x).dot(self.w) - np.dot(x.T, (y-self.b))
            b_gradient=self.b-np.mean(y-np.dot(x,self.w))
            self.w = self.w - learning_rate * w_gradient
            self.b=self.b-learning_rate*b_gradient
            print('step:', i, 'Loss:', loss[0][0])

    def __str__(self):
        return 'weights\t:%s\n bias\t:%f\n' % (self.w, self.b)


def generate_data():
    '''generate the examples to implement linear regression by numpy
    #arguments: None
    #return: x and y
    x.shape=[],y.shape=[]'''
    x = np.linspace(1, 30, num=30).reshape(-1, 3)
    x1 = np.ones(10).reshape(-1, 1)
    x_extended = np.column_stack((x, x1))
    y = np.linspace(1, 10, num=10) + np.random.random(10)
    y = y.reshape(-1, 1)
    return x,y


if __name__ == "__main__":
    x, y = generate_data()
    lr = LinearRegression()
    lr.fit(x, y)
    y_hat = lr.predict(x)
    lr.plot(x, y, y_hat)
    print(y)
    print(y_hat)
    print(lr)
```
## 问题

- 为什么需要对数值类型特征进行归一化

使用梯度下降优化的模型，归一化容易更快通过梯度下降找到最优解。包括线性回归、逻辑回归、支持向量机、神经网络。

- 如何判断是否该用线性回归模型

检查预测值与真实值的residual残差是否为高斯分布

## 参考
- https://www.stat.cmu.edu/~cshalizi/mreg/15/lectures/04/lecture-04.pdf
- http://dengcai.zjulearning.org.cn/Courses/ml/ppt/04_LinearRegression.pdf
- [为什么L1和L2正则化可防止过拟合 - 大龙的文章 - 知乎](https://zhuanlan.zhihu.com/p/85630046)
