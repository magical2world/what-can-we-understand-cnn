# 1.1 动机

过去几年对计算机视觉的研究主要集中在卷积神经网络上。这些工作已经让我们在大部分的分类与回归问题上取得了最好的效果。然而，虽然卷积神经网络的发展已经有很多年了，但是如何从理论上解释为什么卷积神经网络能达到这样好的效果仍是一个难题。事实上，目前卷积神经网络在计算机视觉领域取得的很多成果中都仅仅将其作为一个黑匣子，却不清楚它为什么能够很好的工作，从科学角度来看这是不合理的。其实，对于卷积神经网络的理论方面主要存在两个问题：（1）对于学习方面（例如卷积核），它到底学习到了什么？（2）对于结构设计方面（例如网络层数、每层的卷积核数、池化的策略，非线性函数的选取），为什么一些结构会比另一些好呢？如果能够回答这些问题，不仅能够提高对卷积神经网络科学性的解释，而且可以增加他们的实用性。 &emsp&emsp此外，目前的卷积神经网络一般都需要大量的数据来进行训练来达到好的效果。对于卷积神经网络的更深入的理论认识应该实现对数据的依赖。虽然目前已经有很多关于卷积神经网络如何工作的研究，但是到目前为止，这些大都是卷积神经网络内部各层的可视化的研究。
