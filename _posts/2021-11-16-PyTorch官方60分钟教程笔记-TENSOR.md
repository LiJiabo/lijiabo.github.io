---
layout: article
title: PyTorch官方60分钟教程笔记-TENSOR
tags: 技术 PyTorch Python 机器学习
sharing: true
key: E3332F20-930B-6B0A-76B5-1D782CE9F1F4
lang: zh
permalink: 2021/11/10/pytorchOfficial60mTutorialNoteTensor.html
---
**注意：在观看本笔记前，你应该对Python、神经网络有基本的概念上的了解**
```python
import torch
import numpy as np
```

---

#### tensor初始化

1. 从**Python对象**初始化

   ```python
   data = [[1, 2], [3, 4]]
   x_data = torch.tensor(data)
   ```

2. 从**NumPy array**初始化

   ```python
   np_array = np.array(data)
   x_np = torch.from_numpy(np_array)
   ```

3. 从**另一个tensor**初始化

   ```python
   x_ones = torch.ones_like(x_data) # 保留了x_data的属性
   print(f"Ones Tensor: \n {x_ones} \n")

   x_rand = torch.rand_like(x_data, dtype=torch.float) # 覆盖了x_data的dtype属性
   print(f"Random Tensor: \n {x_rand} \n")
   ```

   输出：

   ```python
   Ones Tensor:
    tensor([[1, 1],
           [1, 1]])

   Random Tensor:
    tensor([[0.1047, 0.4214],
           [0.7751, 0.9202]])
   ```

##### 常用初始化函数：

```python
shape = (2, 3,) # 一个tuple，表示tensor的维度
rand_tensor = torch.rand(shape)
ones_tensor = torch.ones(shape)
zeros_tensor = torch.zeros(shape)
```

---

#### tensor属性

```python
tensor = torch.rand(3, 4)

print(f"Shape of tensor: {tensor.shape}") # 维度
print(f"Datatype of tensor: {tensor.dtype}") # 数据类型
print(f"Device tensor is stored on: {tensor.device}") # 设备
```

输出：

```python
Shape of tensor: torch.Size([3, 4])
Datatype of tensor: torch.float32
Device tensor is stored on: cpu
```

---

#### tensor操作

tensor支持超过100种操作，例如转置、索引、切片、数学操作、随机抽样等，更多描述在[这里](https://pytorch.org/docs/stable/torch.html)

如果可用，将tensor移至GPU上：

```python
if torch.cuda.is_available():
  tensor = tensor.to('cuda')
  print(f"Device tensor is stored on: {tensor.device}")
```

##### 类似numpy的索引和切片操作

```python
tensor = torch.ones(4, 4)
tensor[:,1] = 0
print(tensor)
```

输出：

```python
tensor([[1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.],
        [1., 0., 1., 1.]])
```

##### Join操作

```python
t1 = torch.cat([tensor, tensor, tensor], dim=1)
print(t1)
```

输出：

```python
tensor([[1., 0., 1., 1., 1., 0., 1., 1., 1., 0., 1., 1.],
        [1., 0., 1., 1., 1., 0., 1., 1., 1., 0., 1., 1.],
        [1., 0., 1., 1., 1., 0., 1., 1., 1., 0., 1., 1.],
        [1., 0., 1., 1., 1., 0., 1., 1., 1., 0., 1., 1.]])
```

和join类似的：[stack操作](https://pytorch.org/docs/stable/generated/torch.stack.html)

##### tensor乘法

元素相乘：

```python
# 计算元素范围的乘积
print(f"tensor.mul(tensor) \n {tensor.mul(tensor)} \n")
# 另一种语法
print(f"tensor * tensor \n {tensor * tensor}")
```

计算矩阵乘法：

```python
print(f"tensor.matmul(tensor.T) \n {tensor.matmul(tensor.T)} \n")
# 另一种语法
print(f"tensor @ tensor.T \n {tensor @ tensor.T}")
```

##### 原位操作（会修改一个tensor本身）

有一个“_”后缀的即为原位操作

例：

```python
tensor.add_(5)
```

##### 转换为NumPy array

```python
t = torch.ones(5)
n = t.numpy()
```

**由ndarray转换来的tensor，ndarray变化，tensor也会变，反之亦然**