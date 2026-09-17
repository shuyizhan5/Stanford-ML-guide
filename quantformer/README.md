# QuantFormer：Attention 在量化交易中的应用

这是一个面向初学者的学习页，用来把 Transformer / Attention 的核心机制和量化交易场景连接起来。

> 原项目：<https://github.com/zhangmordred/QuantFormer>
>
> 本页是学习笔记与结构化讲解，不是原项目的镜像，也不重新分发其论文或完整源码。

## 1. QuantFormer 在做什么

可以把整体流程理解成：

```text
历史股票序列
    ↓
Transformer / Attention
    ↓
模型输出预测分数
    ↓
横截面排序
    ↓
选择 Top stocks
    ↓
构建并回测组合
```

核心思想不是“Attention 自动赚钱”，而是让模型从历史序列中学习：**当前预测时，哪些历史位置的信息更值得关注。**

## 2. Attention 的核心公式

\[
\operatorname{Attention}(Q,K,V)
=
\operatorname{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
\]

可以直观理解为：

- **Query**：当前时刻在找什么信息；
- **Key**：各历史时刻“有什么信息”；
- **Value**：真正要被传递的内容；
- \(QK^T\)：计算当前位置和其他位置的匹配程度；
- softmax：把匹配程度变成权重；
- 乘 \(V\)：按权重聚合历史信息。

## 3. 在量化时间序列里怎么理解

假设一只股票过去 \(T\) 个时间点，每个时间点有若干特征：

\[
X = [x_1, x_2, \ldots, x_T]^T.
\]

Attention 会给不同历史位置不同权重：

\[
a_{t,1}, a_{t,2}, \ldots, a_{t,T}.
\]

于是当前位置新的表示可以写成：

\[
h_t = \sum_{j=1}^T a_{t,j}v_j.
\]

这相当于让模型自己学习：近期信息、较久以前的异常波动、成交量变化等，哪些对当前预测更重要。

## 4. 建议阅读顺序

1. 先理解 `Q / K / V`；
2. 再看 `Scaled Dot-Product Attention`；
3. 再看 `Multi-Head Attention`；
4. 再看 QuantFormer 的模型输入、训练目标与输出；
5. 最后再看选股排序和回测逻辑。

## 5. 你应该重点关注什么

学习这个项目时，建议把注意力放在这几个问题上：

- 输入张量的 shape 是什么；
- 每个 timestep 放了哪些金融特征；
- Attention 在时间维上如何聚合信息；
- 模型最后预测的 target 是什么；
- 如何从 prediction 变成 ranking；
- ranking 如何变成 portfolio；
- 是否存在 look-ahead bias、数据泄漏或过拟合。

## 6. 原项目与论文

- QuantFormer GitHub：<https://github.com/zhangmordred/QuantFormer>
- 本项目主页：<https://github.com/shuyizhan5/Stanford-ML-guide>

## 7. 说明

本页用于学习和教学，内容是对公开项目的个人理解与重新组织。若你准备复现原论文，请以原论文、原仓库及其许可说明为准。
