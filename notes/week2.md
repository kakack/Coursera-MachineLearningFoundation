<h1 align="center">第二周「感知器假设集」</h1>



## 目录

* [笔记](#笔记)
  * [目录](#目录)
  * [课程介绍](#课程介绍)
  * [感知器假设集](#感知器假设集)
  * [感知器学习算法PLA](#感知器学习算法PLA)
  * [感知器的保证](#感知器的保证)
  * [不可分离数据](#不可分离数据)



## 感知器假设集

一个简单的感知机模型

| 年龄     | 23岁    |
| -------- | ------- |
| 年收入   | $100000 |
| 工作时长 | 1年     |
| 当前负债 | $200000 |

- 对于每一个$x=(x_1, x_2,...,x_d)$的顾客特征，计算一个带权重的score，并且有：

​	$\left\{\begin{matrix} approve\ when\ \sum^d_{i=1}w_i x_i > threshold \\ deny\ when\ \sum^d_{i=1}w_i x_i \leq threshold \\ \end{matrix}\right.$

- $y: \{+1(good), -1(bad)\}$， 0 ignored——线性方程$h \in H$:

  $$ \begin{align} h(x)&=sign((\sum^d_{i=1}W_iX_i)-threshold) \\ &=sign((\sum^d_{i=1}W_iX_i)+(-threshold) \cdot (+1) \\ &=sign(\sum^d_{i=0}W_iX_i) \\ &=sign(W^TX) \end{align}$$

  

以上即称为感知机perceptron



## 感知器学习算法PLA



## 感知器的保证



## 不可分离数据

