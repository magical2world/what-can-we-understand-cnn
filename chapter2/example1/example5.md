# 2.1.5 多层神经网络的训练

正如前文所述，各种多层架构的成功很大程度上依赖于它们的学习算法的成功。然而神经网络通常会先依赖于基于无监督学习的预训练，如2.1.1节描述的那样。然后会使用大多数多层架构都会使用的监督学习策略进行进一步训练。这一训练过程通常依赖于基于梯度的误差反向传递算法。由于梯度下降法的简单性，它被广泛的应用到多层结构的学习中。它通过最小化一个平滑的误差函数$$E\left(w\right)$$,利用下面的公式进行不断地迭代：
$$
w_{k}=w_{k-1}-\alpha\frac{\partial E(w)}{\partial w}\tag {2.11}
$$
这里$$w$$是网络的参数，$$\alpha$$是控制收敛速度的学习率，$$\frac{\partial E(w)}{\partial w}$$是在训练集上计算得到的误差的梯度。由于链式求导法则来计算误差对于不同层的网络参数的导数使得梯度下降法很适合用来训练多层网络。然而虽然误差反向传递算法已经提出好多年了\[16,146\]，但它真正是在多层框架的背景下才得到普及的\[125\]。事实上真正被广泛应用的是随机梯度下降法，它通过使用整个数据集的子集来代替整个数据集来计算误差的梯度，使得训练时间大大减少。 梯度下降法的一个严重的问题是学习率$$\alpha$$的选择。学习率选的太小会导致收敛速度很慢，学习率选的很大可能会导致一直围绕着极值点反复波动而无法到达最佳状态。因此，有很多方法被提出来对随机梯度下降法进行改进。它们之中最简单的就是在随机梯度算法中添加动量\(momentum\)\[137\]，通过跟踪一次迭代到另一次迭代的更新量，如果梯度的方向在一次次更新中始终保持相同，则动量会利用进一步推动整个学习过程，其公式如下所示：
$$
w_{k}=w_{k-1}-\alpha\frac{\partial E(w)}{\partial w}-\gamma (\frac{\partial E(w)}{\partial w})_{t-1}\tag {2.12}
$$
这里$$\gamma$$控制着动量的大小。另一种简单的方法是让学习率随着时间的推移来逐渐下降，但是学习率该在何时下降很难在训练过程开始之前就预先设定，而且学习速率该在何时下降还与数据的分布情况有着很大的联系。其他的一些方法（例如Adagrad\[34\],Adadelta\[152\],Adam\[86\]）能够使学习率在训练过程中随着每个参数$$w_{i}$$来自行改变,对变化幅度大的参数使用小的学习率，对变化小的参数使用大的学习率。具体的关于这三种优化算法的比较可以参见文献\[124\]。 使用梯度下降法及其变体的一大缺点是需要大量的带标签数据来训练。避免这一问题的方法是采用无监督学习。一个流行训练浅层神经网络的无监督学习方法是基于预测稀疏分解（PSD）\[85\]的方法。PSD通过学习完全的滤波器的集合来重构图像
$$
L\left(X,Y;B\right)=\begin{Vmatrix} X-BY \end{Vmatrix}^2_{2}\tag {2.13}
$$
PSD是将稀疏编码与卷积结构相结合的产物，它的优化过程是通过最小化下面的重构误差来实现的：
$$
L\left(X,Y;B\right)=\begin{Vmatrix} X-BY\end{Vmatrix}^2_{2}+\lambda\begin{Vmatrix} Y \end{Vmatrix}_{1}+\alpha\begin{Vmatrix}F(X;G,W,D)\end{Vmatrix}^2_{2}\tag {2.14}
$$
这里$$F\left(X;G,W,D\right)=Gtanh\left(WX+D\right)$$，$$W$$,$$D$$,$$G$$分别是网络的权重、偏差及收益（或者是标准化因素）。通过最小化公式2.14，该算法可以学习到一个输入图像的表示$$Y$$来重构输入$$X$$，它和预测的表示$$F$$相似。而公式2.14的第二项可以使学到的表示具有稀疏性。实际上，网络的优化分为两步，先是固定参数$$\left(B,G,W,D\right)$$来通过最小化公式2.14来优化$$Y$$，然后再固定$$Y$$来学习其它参数。需要注意的是，PSD对于每个图像的补丁都有一组参数需要从图像的不同补丁处来训练$$\left(G,W,D\right)$$，换句话说就是对于图像的不同部分，都有一系列的核需要去学习来对图像进行重组。

