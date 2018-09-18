# 2.1 多层结构
在深度学习发展起来之前，最先进的视觉识别系统主要依靠于两个即独立又相关的步骤。首先，通过人工设计来提取输入数据的特征（如基于集合的卷积、局部或全局编码等方法），这种方法可以使人们根据自己的任务需求将输入数据转化为一种抽象的表示，以方便使用分类器对数据进行分类。然后就是利用分类器（例如SVM）对转换后的数据进行识别。分类器的效果如何，通常和提取的特征有着很大的关联。
多层结构提供了一种全新的解决问题的方法，在学习过程中，模型不仅能够学习如何对数据进行分类，而且能够自动的学习数据的转换。这种学习方式通常被称为表示学习[7,90]，对于深度多层结构，一般被称为深度学习。
多层结构可以被定义为一个可以从数据中提取多个抽象层次的计算模型。通常情况下，多层结构自在在高层部分放大输入的重要部分，而对不重要的部分变得不敏感。大多数的多层结构都是简单的线性或非线性模块的堆砌。近些年来，很多多层框架被提出，而这部分将会介绍计算机视觉中应用最广泛的一些结构。尤其是人工神经网络将会作为重点被介绍。为了简洁起见，下面我们将简称人工神经网络为神经网络。

