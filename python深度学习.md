第二章

1、小批量随机梯度下降

（1）抽取训练样本x和对应目标y组成的数据批量

（2）在x上运行网络【这一步叫做前向传播】，得到预测值y_pred

（3）计算网络在这批数据上的损失，用于衡量y_pred和y之间的距离

（4）计算损失相对于网络参数的梯度【一次反向传播】

（5）将参数沿着梯度的反方向移动一点，比如w-=step*gradient,从而使这批数据上的损失减小一点。

2、动量

动量在许多优化器中都有应用，动量解决了SGD的两个问题：收敛速度和局部极小点。
使用动量方法可以避免陷入局部极小点，动量方法的实现过程是每一步都移动小球，不仅要考虑当前的斜率值（当前的加速度），还要考虑当前的速度
（来自于之前的加速度），这在实践中是指，更新参数w不仅要考虑当前的梯度值，还要考虑上一次的参数更新。

3、局部极小点、全局最小点

在某个参数值附近，有一个局部极小点：在这个点附近向左移动和向右移动都会导致损失值增大。如果使用小学习率的SGD进行优化，那么优化过程可能
会陷入局部极小点，导致无法找到全局最小点。

4、链式求导：反向传播算法

假设函数是可微的，因此可以明确计算其导数，在实践中，神经网络函数包含许多连接在一起的张量运算，每个运算都有简单的、已知的导数。
反向传播从最终损失值开始，从最顶层反向作用至最底层，利用链式法则计算每个参数对损失值的贡献大小。

5、梯度下降的具体方法由第一个参数给定，即rmsprop优化器

6、小结：

  ①学习是指找到一组模型参数，使得在给定的训练数据样本和对应目标值上的损失函数最小化。
  
  ②学习的过程：随机选取包含数据样本及其目标值的批量，并计算批量损失相对于网络参数的梯度。随后将网络参数沿着梯度的反方向稍稍移动（移动距离由学习率指定）
  
  ③整个学习过程之所以能够实现，是因为神经网络是一系列可微分的张量运算，因此可以利用求导的链式法则来得到梯度函数，这个函数将当前参数和当前数据批量映射
   为一个梯度值。
   
  ④损失是在训练过程中需要最小化的量，因此，它应该能够衡量当前任务是否已成功解决
  
  ⑤优化器是使用损失梯度更新参数的具体方式，比如RMSProp优化器、带动量的随机梯度下降（SGD）等

第三章

1、训练神经网络主要围绕以下四个方面：

  ①层，多个层组合成网络（或模型）
  
  ②输入数据和相应的目标
  
  ③损失函数，即用于学习的反馈信号。
  
  ④优化器，决定学习过程如何进行。
