<h1 align="center">第二周「感知器假设集」</h1>



## 目录

* [笔记](#笔记)
  * [目录](#目录)
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

![](https://raw.githubusercontent.com/kakack/Coursera-MachineLearningFoundation/main/md_imgs/w2_1.png)



## 感知器学习算法PLA

已知$H$是空间内所有感知机，那如何选择最好的$g$？

需要在空间中找到一个感知机，能将现有所有样本区分正确，即$g(x_n)=f(x_n)=y_n$。但是还是会有无数个解。

我们的一个方法：先随意找一个感知机，然后不断修正，达到我们期待的范围。例如随机初始化得到$w_0$，并且不断地在$D$s上修正错误。

Cyclic PLA：

对于$t=0,1,...$

1. 找到下一个关于$w_t$计算错误的值为$(x_{n(t)}, y_{n(t)})$，有$sign(w^T_tx_{n(t)}) \ne y_{n(t)}$

	2.	修正这个错误，通过$w_{t+1}\leftarrow w_t + y_{n(t)}x_{n(t)}$

直到一整个cycle里都不再存在错误。

（也被称为知错能改算法）

但是这个算法存在一个问题，这个cycle是否一定能停下来。

## 感知器的保证

数据的线性可分性质linear separability：

如果PLA算法能停下来（在当前数据集上没有错误了），也就是$D$允许一些$w$不犯任何错误，或者说存在一些perceptrons能在$D$上完美分割数据，那么我们就称$D$为线性可分。

$D$是线性可分的$\Leftrightarrow $存在一个完美的$w_f$使得$y_n=sign(w^T_fx_n)$

- 如果存在完美$w_f$，因此对于每一个$x_n$都能正确地从直线离开：$y_{n(t)}w^T_fx_{n(t)} \ge min_ny_nw^T_fx_n>0$
- $w^T_fw^t \uparrow$通过任何的犯错误点$(x_{n(t)}, y_{n(t)})$进行更新：$w^T_f$和$w^t$的内积越来越大，也就是二者夹角越来越小，二者越来越接近（不考虑长度变化）

​			$$\begin{align}w^T_fw_{t+1} &= w^T_f(w_t+y_{n(t)}x_{n(t)}) \\ & \ge w^T_fw_t + min_ny_nw^T_fx_n \\ &> w^T_fw_t +0\end{align}$$

PLA另一个性质是有错才更新$\Leftrightarrow $$sign(w^T_tx_{n(t)}) \ne y_{n(t)}$$\Leftrightarrow $$y_{n(t)}w^T_tx_{n(t)} \le 0$。可以以此来限定$w^T_f$和$w_t$的长度：即$\left\| w_t+1\right\|^2$的值不会比$\left\| w_t\right\|^2$增加过多

$$\begin{align} \left\| w_t+1\right\|^2 &= \left\| w_t+y_{n(t)}x_{n(t)}\right\|^2 \\ &= \left\| w_t\right\|^2 + 2y_{n(t)}w^T_tx_{n(t)} + \left\| y_{n(t)}x_{n(t)}\right\|^2 \\ & \le \left\| w_t\right\|^2 + 0 + \left\| y_{n(t)}x_{n(t)}\right\|^2 \\ & \le \left\| w_t\right\|^2 + max_n \left\| y_nx_n\right\|^2\end{align}$$

假如从$w_0=0$开始，经过$T$个错误修正后：

$\frac{w^T_f}{\left\|w_f\right\|}\frac{w_T}{\left\|w_T\right\|} \ge \sqrt{T} \cdot \frac{R^2}{\rho^2}$

其中$R^2=max_n \left\| x_n\right\|^2$，$\rho=min_ny_n\frac{w^T_f}{\left\| w_f\right\|}x_n$



总结：PLA的保证：只要是线性可分且通过错误修正：

	- $w_f$和 $w_t$的内积迅速增大，而$w_t$的长度增长缓慢；
	- PLA表示的直线会越来越和$w_f$对齐$\Rightarrow$PLA算法停止。

PLA的优点：

	-	实现起来简单，快速，可以在任何维度$d$上实现

PLA的缺点：

	-	需要假设在$D$上线性可分才能停止，这个性质是事先未知的；
	-	不能完全确认多久后算法停止（$\rho$依赖于$w_f$）



## 不可分离数据

那么假如$D$不是线性可分的怎么办？

假如数据集中含有一定噪声：

	-	假设噪声较少：$y_n=f(x_n) \ usually$
	-	如果是这样的话， $g\approx f \ on\ D \Leftrightarrow y_n=g(x_n) \ usually$
	-	也就是说，$w_g \leftarrow argmin_w \sum^N_{n=1} [y_n \ne sign(w^Tx_n)]$，找不到完全不犯错误的，那就找一个犯错误最少的
	-	然而这是一个NP-Hard问题

口袋算法Pocket Algorithm（一种贪心策略）：通过保持pocket中最好的权重来修改PLA算法。

初始化pocket weights $\hat w$:

对于$t = 0, 1, ...$:

	1.	找到一个随机的错误$w_t$，称为$(x_{n(t)}, y_{n(t)})$；
	1.	尝试修正错误，通过$w_{t+1} \leftarrow w_t+y_{n(t)}x_{n(t)}$；
	1.	如果$w_{t+1}$比$\hat w$犯错要少，那么用$w_{t+1}$替换$\hat w$

直到迭代足够多次数

返回$\hat w$作为$g$

