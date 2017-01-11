---
title: 基于深层神经网络的语音合成
date: 2016-04-21 19:33:08
tags: 
- 语音合成
- 机器学习
---

## 简介
随着深度学习在各个领域取得了优异的性能，例如计算机视觉、自然语言处理领域。深度学习也被应用到语音合成中，并取得了不错的效果。本文就简单介绍基于深层神经网络的语音合成。

## 基于DBN的语音合成
深层置信网络（Deep Neural Network，DBN）是概率生成模型，其中包含了多个隐层。

![基于DBN的语音合成系统框图](/paper_image/DBN_based_speech_synthesis.png)

## 基于DNN的语音合成
深层神经网络（Deep Neural Network，DNN）是一种前馈神经网络，除了输入层和输出层，包含多个隐层。

![基于DNN的语音合成系统框图](/paper_image/DNN_based_speech_synthesis.png)


## 基于RNN的语音合成
循环神经网络（Recurrent Neural Network，RNN）包含循环连接，可以获取输入序列任意时刻的信息。

![基于RNN的语音合成系统框图](/paper_image/DBLSTM_RNN_TTS.png)

## 总结
- 在客观指标方面，基于深层神经网络的语音合成显著优于传统的语音合成（例如基于HMM的语音合成）。
- 在主观听感方面，基于深层神经网络的语音合成整体高于基于HMM的语音合成，但是某些地方会出现较差的情况。
- 基于深层神经网络的语音合成需要更多的计算量。


## 参考文献
- S.-Y. Kang, X.-J. Qian, and H. Meng, “Multi-distribution deep belief network for speech synthesis,” in Proc. IEEE Int. Conf. Acoustics, Speech and Signal Pro- cessing (ICASSP), 2013, pp. 8012–8016.
- H. Zen, A. Senior, and M. Schuster, “Statistical parametric speech synthesis using deep neural networks,” in Proc. IEEE Int. Conf. Acoustics, Speech and Sig- nal Processing (ICASSP), 2013, pp. 7962–7966.
- Y. C. Fan, Y. Qian, F. L. Xie, F. K. Soong. TTS synthesis with bidirectional LSTM based recurrent neural networks.[C]. Interspeech. 2014, pp. 1964–1968.