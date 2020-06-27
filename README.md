## translate-GoogleNet

## Going deeper with convolutions

### Abstract
我们提出了一个深度卷积神经网络框架，代号Inception。该框架在ILSVRC-2014竞赛中创造了新的成绩。该框架的主要特征是，对网络精心设计，提升了网络的计算效率，在保持计算资源不变的情况下，使得我们可以增加网络的深度和宽度。为了优化结果，框架的决策是基于Hebbian principal 和 intuition of multi-scale processing。我们在ILSVRC-2014竞赛中提交的版本叫做GoogleLeNet。这是一个 22 层的深度网络，本文主要介绍了它的分类能力和物体识别能力。

### 1 Introduction
在过去三年，随着深度网络的发展，主要集中在卷积神经网络上，图像识别和物体识别能力取得了 dramatic 进步。这些进步不仅仅由于我们拥有更强大的硬件，更大的数据集，更大的网咯，还主要来自于新的想法，新的算法的产生，新的框架的改进。ILSVRC竞赛一直用的是同样的数据集来进行分类任务。相比两年前ILSVRC-2012竞赛中表现最好的框架(Krizhevsky et al)我们的框架的参数量比它少 12 倍，而且性能更好。单单使用更深的网络无法有效帮助物体检测 object-detection 取得大的进步，它需要深度框架和 classical computer vision共同来促进物体检测 object-detection 的进步，就像 R-CNN 算法一样。

另一个重要的因素是移动设备的发展，需要我们的算法的计算效率和内存使用效率变得很重要。我们设计深度框架主要也是这个原因，而不是出于对网络accuracy的考虑。在我们的实验中，我们把模型的整个训练过程的计算量控制在15亿次 multiply-adds 。我们要训练一种网络不只是从学术上考虑，还要让他在现实生活中可以拿来使用。

本文，我们集中精力为机器视觉computer vision创建一种有效的深度神经网络，取名Inception 。本文中，‘deep’一词有两种含义，一种是引入一种新的组织结构，一种是增加网络深度。Inception 模型拥有很复杂的逻辑，主要参考的是 Arora et al[2]中的理论成果。我们的模型最终在ILSVRC-2014的分类和检测classification and detection比赛中获得了头奖，并且远远超出其他选手。

### 2 Related Work
从LeNet-5开始，卷积神经网络有一种标准的结构，就是，把一个个卷积层叠加起来，中间可选择性的插入contrast normalization层，max-pooling层，最后跟几个全连接层。有很多各种各样的网络应用在图像分类任务中，比如MNIST,CIFAR，还有ImageNet分类挑战赛，都取得了最好的成绩。对于像ImageNet这样大的数据集来说，最近总的趋势是增加层数以及每层的宽度，然后用dropout方法来解决过拟合问题。


尽管max-pooling层会损失一些空间精度，但是卷积神经网络框架已经成功应用在定位localization,物体检测object detection, 人姿态检测human pose estimation 。受灵长类视觉皮层的神经学模型的启发，Serre et al.[15] 使用一系列的不同大小的Gabor filters来处理多尺度图像。本文中的Inception模型也是这么做的。然而，相比Serre et al.[15]中固定两层的参数不变，我们的Inception模型并没有这么做，而是学习所有的参数。另外，Inception模型中的层多是重复的层，深度达到22层。
















