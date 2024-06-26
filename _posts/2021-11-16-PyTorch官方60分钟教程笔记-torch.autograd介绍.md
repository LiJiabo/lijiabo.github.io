---
layout: article
title: PyTorch官方60分钟教程笔记-torch.autograd介绍
tags: 技术 PyTorch Python 机器学习
sharing: true
key: 05D3E8FA-B586-A3FA-2930-5DC057C54EA0
lang: zh
permalink: 2021/11/16/torchDotAutogradIntro.html
---
**注意：在观看本笔记前，你应该对Python、神经网络有基本的概念上的了解**

torch.autograd是PyTorch的自动微分引擎。

#### 背景

神经网络由许多函数组成，这些函数由一些参数（权重和偏差）定义，参数在PyTorch中存储在tensor中。

训练一个神经网络由2步组成：

1. 正向传播

   在这一步中，神经网络由输入计算出输出。

2. 反向传播

   在这一步中，神经网络根据loss（损失函数）调整自己的参数。它通过从输出反向遍历，收集关于函数参数（梯度）的loss的导数，以及使用梯度下降优化参数做到这一点。[一个来自3Blue1Brown的视频](https://www.bilibili.com/video/BV16x411V7Qg)很好地解释了这个算法。

#### PyTorch中的一般训练流程

```python
import torch, torchvision
model = torchvision.models.resnet18(pretrained=True) # 创建模型
data = torch.rand(1, 3, 64, 64) # 3个颜色通道，64×64分辨率
labels = torch.rand(1, 1000)
prediction = model(data) # 正向传播
loss = (prediction - labels).sum() # 计算损失函数
loss.backward() # 反向传播
#调用backward()后，Autograd会计算每个模型参数的梯度，存储在参数的.grad属性内
optim = torch.optim.SGD(model.parameters(), lr=1e-2, momentum=0.9)
optim.step() # 随机梯度下降优化参数
```

