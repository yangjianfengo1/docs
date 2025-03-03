## [ 组合替代实现 ]torch.nn.init.ones_

### [torch.nn.init.ones_](https://pytorch.org/docs/stable/nn.init.html?highlight=ones_#torch.nn.init.ones_)

```python
torch.nn.init.ones_(tensor)
```

### [paddle.nn.initializer.Constant](https://www.paddlepaddle.org.cn/documentation/docs/zh/develop/api/paddle/nn/initializer/Constant_cn.html)

```python
paddle.nn.initializer.Constant(value=0.0)
```

两者用法不同：torch 是 inplace 的用法，paddle 是类设置的，具体如下：

### 参数映射
| PyTorch       | PaddlePaddle | 备注                                                   |
| ------------- | ------------ | ------------------------------------------------------ |
| tensor        | -          | n 维 tensor。Paddle 无此参数，因为是通过调用类的 __call__ 函数来进行 tensor 的初始化。    |
| -          |  value          | 用于初始化输入变量的值。Pytorch 无此参数，Paddle 默认值为`0.0`，需设置为`1.0`。   |

### 转写示例
```python
# Pytorch 写法
conv = torch.nn.Conv2d(4, 6, (3, 3))
torch.nn.init.ones_(conv.weight)

# Paddle 写法
conv = nn.Conv2D(in_channels=4, out_channels=6, kernel_size=(3,3))
init_constant = paddle.nn.initializer.Constant(value=1.0)
init_constant(conv.weight)
```
