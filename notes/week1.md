<h1 align="center">第一周「课程介绍」</h1>



## 目录

* [笔记](#笔记)
  * [目录](#目录)
  * [Course Introduction](#Course Introduction)
  * [What is Machine Learning](#What is Machine Learning)
  * [Applications of Machine Learning](#Applications of Machine Learning)
  * [Components of Machine Learning](#Components of Machine Learning)
  * [Machine Learning and Other Fields](#Machine Learning and Other Fields)



# Course Introduction



机器学习是一个理论和实践工具的混合体。如果是理论导向，则会深入理解所有内容，但是难以获得通常受众的兴趣；如果是技术导向，则会快速浏览所有当下先进的技术，但是难以选择和正确选用。因此本堂课采用的是基础导向，包括机器学习的哲学阐述、关键理论、核心技术、实践应用和玩笑等。

# What is Machine Learning

学习，即获得技能，通常是通过观察后的经验累积获得：观察->学习->技能。

机器学习就是我们希望计算机来模拟和模仿这个过程。通过数据的计算和累积获得经验和技能。数据->机器学习->得到某一种表现的提高

所谓的技巧就是提高某一种可量化的表现（比如预测准确率）。

机器学习其实是一种构建复杂系统的替代路径。通常使用场景有：

- 某些人类无法直接正确编程开发的系统；
- 某些人类无法轻松定义解决方法时候；
- 需要快速决策且超出人类能力的；
- 当需要大规模面向用户的。

机器学习的三个关键本质：

- 存在一些需要学习的潜在模式underlying pattern——因此可以改进现有的表现衡量；
- 但是没有简单可编程的定义；
- 然而存在一些关于这种模式的数据——机器学习可以以此为输入。

# Applications of Machine Learning

# Components of Machine Learning

基本符号定义：

- Input: $x \in \chi $
- Output: $y \in Y$
- target function: $f: \chi \to Y$
- Data $\Leftrightarrow$ training examples: $D = \{(x_1, y_1),(x_2, y_2), ...,(x_N, y_N),\}$
- Hypothesis $\Leftrightarrow$ skill with hopefully good performance: $g: \chi \to Y$

![](https://raw.githubusercontent.com/kakack/Coursera-MachineLearningFoundation/main/md_imgs/w1_1.png)



# Machine Learning and Other Fields



Machine Learning VS Data Mining：

- Machine Learning使用数据去计算贴合目标f的假设g，而data mining利用巨量数据来找到感兴趣的性质；
- 其中如果感兴趣性质和贴合目标的假设一致，那ML=DM；
- 如果感兴趣性质和贴合目标的假设有关，那么DM可以帮助ML；
- 传统DM同样关注如何高效地在大规模数据集中进行计算。

Machine Learning VS Artificial Intelligence：

- Machine Learning使用数据去计算贴合目标f的假设g，而AI则计算一些能表现出智能行为的东西；
- 如果g约等于f是一些能表现出智能行为的东西，那么ML可以认识到AI；
- 比如下棋：
  - 传统AI：game tree；
  - ML for AI：从棋盘数据中学习

Machine Learning VS Statistics：

- Machine Learning使用数据去计算贴合目标f的假设g，而statistics使用数据去对未知过程进行推论；
- 如果g是一个推论结果，f是未知的，那么统计可以用来实现ML；
- 传统统计学也关注用数学假设证明的结果，不太关心计算