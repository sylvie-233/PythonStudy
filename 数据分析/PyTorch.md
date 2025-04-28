# PyTorch




## 基础介绍

PyTorch 是一个开源的、基于 Python 的深度学习框架，主要用于：
- 神经网络建模
- 机器学习研究
- 快速原型开发
- 大规模生产部署（尤其配合TorchScript、TorchServe）AI框架



## 核心内容
```yaml
torch:
    cuda:
        is_available():
    nn:
        functional:
            relu():
        CrossEntropyLoss: # 交叉熵
            backward(): # 反向传播
        Linear:
        Module: # 神经网络模块
            forward(): # 前向传播
    optim: # 优化器
        SGD:
            step(): # 更新网络参数
            zero_grad():
    ones():
        requires_grad:
    rand():
    randint():
    randn():
```