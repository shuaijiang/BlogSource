---
title:  WaveNet--一种应用于原始语音的端到端生成式模型
date: 2016-12-05 08:36:28
tags: 
- PaperReading
- 语音合成
---

#  论文信息
- 作者：Aaron van den Oord, Sander Dieleman, Heiga Zen, Karen Simonyan, Oriol Vinyals, Alex Graves, Nal Kalchbrenner, Andrew Senior, Koray Kavukcuoglu
- 单位：Google, Google Deep Mind
- 发表日期： 2016
- 论文链接：[https://arxiv.org/pdf/1609.03499.pdf](https://arxiv.org/pdf/1609.03499.pdf "https://arxiv.org/pdf/1609.03499.pdf")

# 简介
WaveNet 是一种用于生成原始语音的深层神经网络，基于WaveNet的语音合成比目前性能最好的参数式语音合成和拼接式语音合成有更好的主观评分。
单个WaveNet可以捕获多个说话人的特点，根据说话人的标记可以在不同说话人之间转换。
WaveNet还可以生成美妙动听的音乐，此外还可以作为区分式模型应用到音子识别。

该论文工作的主要贡献包括：
- 验证了WaveNet可以生成语音信号，并且语音的主观评分之高在TTS领域内是前所有未有的。
- 为了更好地处理音频生成过程中的长跨度的时序依赖，基于扩展级联卷积开发了新的网络结构。
- 验证了在不同说话人标记条件下，单个模型可以生成不同的声音。
- 文中的网络结构在小的语音识别数据库中具有很好的效果，并且在生成其他音频例如音乐时具有不错的效果。

# WaveNet
介绍了一种生成式模型，直接对原始语音波形建模。波形$X={x_1,...,x_T}$是条件概率的乘积：$p(x) = \frac{p(x_t|x_1,...,x_{t-1}}$

条件概率分布建模通过卷积层的堆叠实现，但是网络中没有pooling层，同时模型的输出与输入在时序上有相同的纬度。

##  Dilated Causal Convolutions
WaveNet主要由Causal Convolution组成，下图是由多个Causal Convolutional Layers堆叠形成的网络。
![Visualization of a stack of causal convolutional layers](/paper_image/waveNet_cnn.png)

这里采用了一种扩展的卷积网络，随着隐层阶数增加而增加接收范围，但不会明显增加计算量。
![Visualization of a stack of dilated causal convolutional layers](/paper_image/waveNet_dilated_cnn.png)

随着深度的增加，扩展范围指数性增加。

## Softmax Distributions
相关研究工作证明Softmax distribution 对于条件分布建模有更好的效果，尽管数据是连续的。

## Gated Activation Units
文章采用了门限激活单元，与门限PixelCNN中的一致。
![Gated activation units](/paper_image/waveNet_gated_activation.png)
其中，*表示卷积操作。

## Residual and Skip Connections

![Overview of the residual block and the entire architecture](/paper_image/waveNet_architecture.png)


# 实验

# 总结