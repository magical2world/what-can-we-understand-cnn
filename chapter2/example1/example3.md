# 2.1.3 卷积神经网络
卷积神经网络是一种特殊的神经网络，它可已通过简单的操作来逐层的提取数据的抽象特征，因此可以很好地解决计算机视觉方面的问题。有两个关键点决定了卷积神经网路的架构可以成功的在计算机视觉中应用。第一，卷积神经网络很好的利用了图像的二维特性及相邻像素之间的相关性。因此，卷积神经网络避免了像素之间一对一的连接（例如大部分神经网络一样），而是使用了组合的局部连接。此外，卷积神经网络的结构依赖于特征共享及每个通道（或者说是输出特征图）都是使用相同的滤波器对所有位置计算得到的，卷积神经网络的结构如图2.5所示。卷积神经网络的这一特性使得其相对于标准神经网络来说，参数大大减少。第二、卷积神经网络也使用了池化操作在一定程度上减少了位置的误差的影响。值得注意的是，池化层的使用，使得网络的受视野增大，这也允许了网络能够逐步的看到输入较大的区域。受视野的增大（与输入分辨率的降低）使得网络随着层数的增加可以从输入中提取更抽象的特征。例如，对于物体识别来说，在开始部分的卷积神经网络层会更注重提取物体的边缘特征，最后才会逐渐的在高层覆盖物体的整体特征。

卷积神经网络的架构很大层度上受到了Hubel及Wiesel在视觉皮层方面研究[74]（将会在第三章进一步描述）的启发。事实上，最早出现的有关卷积神经网络的案例应该是Fukushima的Neocognitron，这种网络也使用了局部连接，而且每个特征图仅仅会最大化响应一个特殊的特征类型。Neocognitron。。。。。。简单神经元执行操作如卷积操作，然后执行整流线性单元（ReLU）的非线性运算，即$$ \varphi\left(x\right)= \begin{cases} x; & \text {if $x\geq0$} \\ 0; & \text {$x$ < 0} \end{cases} $$，而复杂神经元执行的操作类似于平均池化。该模型还包括一个分裂的非线性，以实现类似于现代卷积神经网络中的规范化。
和现代很多标准的卷积神经网络结构[88,91]不同的是，Neocognitron不需要有标注的数据进行学习，因为它是基于自组织图来学习连续层之间的连接。
近些年来在计算机视觉应用方面取得成功的大部分卷积神经网络的架构都借鉴于LeCun在1998年提出的架构，即现在为大家所熟知的用于手写汉字识别的LeNet[91]。如文[77,93]中所述，一个典型的卷积神经网络由4个基本层组成：***(i)卷积层，***(ii)非线性或整流层，***(iii)标准化层及***(iv)池化层。如上面所述，这些成分在Neocognitron中都有体现。而LeNet的关键一点是使用了反向传递算法来对卷积参数进行高效地学习。
虽然卷积神经网络需要学习的参数相较全连接神经网络有了很大的减少，它的主要的缺点还是需要大量的带标签数据进行学习。这种对数据的要求也是为什么卷积神经网络直到2012年才被广泛使用的原因，因为这时出现了大型图像数据集ImageNet[126]及计算资源的快速发展。卷积神经网络在ImageNet上面的成功导致了各种卷积神经网络结构的快速发展，但是卷积神经网络的改变仅仅是对其基本构建模块的改变，这一点将会在第2.2节继续讨论。