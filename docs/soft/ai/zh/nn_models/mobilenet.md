---
title: MobileNet 物体分类模型
---

Mobilenet 网络是由 Google 针对手机和嵌入式场景提出的一种轻量级的深度神经网络，其主要特点是使用深度可分离卷积（depthwise separable convolution）来替代普通卷积，从而减少计算量，提高网络的计算效率。该网络在 ImageNet 数据集上的分类精度达到了 70.8%，在损失了不多精度的情况下，极大地减少了计算量，使神经网络模型在普通单片机上流畅运行也成为了可能！


## 目标

按顺序输入若干张图像，输出每张图像属于哪个分类，以及该分类的置信度。


## 原理


对于不太对详细的原理感兴趣的同学，可以简单理解：

* 卷积计算具有提取特征的作用，比如一幅图像经过一次卷积计算后的结果，会将图像的轮廓提取出来，比如经典的索贝尔边缘检测，比如下图右边是图像输入，左边是经过一次卷积计算后的结果：
![](../../assets/sobel_edge2.jpg)
可以说，通过一次卷积计算，图像的轮廓就被提取出来了，这就是卷积计算的特征提取作用。
如果经过多次卷积计算，不同图像的特征就会被提取出来。 你可以在[tensorspace.org](https://tensorspace.org/html/playground/mobilenetv1.html) 可视化地看到这个过程。

* 经过整个由无数个卷积计算和其它计算组成的网络计算，最后输出一个只有 1000 个像素点的图像，不同分类的图输入，在输出层的 1000 个像素点中，其中一个像素点的值会较大，这个像素点对应的分类就是网络的输出结果。比如一只熊猫图像输入，如果输出层的第 388 个像素点的值较大，并且值为 0.8，我们就通过这个网络识别到了这张图像是一只熊猫，置信度为 0.8。

* 至于 Mobilenet 网络宣称使用了深度可分离卷积（depthwise separable convolution）来替代普通卷积，从而减少计算量，提高网络的计算效率，你可以理解成相比于之前的卷积网络，仍然是卷积计算，只是和在图像上使用的普通卷积计算的方式不同，这样就可以减少计算次数，提高网络的计算效率，具体方式怎么不同请自行进一步阅读相关文章。

* 至于训练，和在基础知识中说到的一样，通过不停向网络输入图像，然后让网络输出正确的分类，然后通过损失函数计算网络输出的分类和正确分类的差距，然后通过反向传播算法，不断调整网络中的参数，使得网络输出的分类和正确分类的差距越来越小，最终网络就能够输出正确的分类。训练实际就是找出适合我们的数据的网络中的参数，比如网络中所有卷积核的值，网络中所有的偏置值等等。



关于 Mobilenet 的具体原理，此处不进行详细介绍，感兴趣的读者可以参考 Mobilenet 论文原文（ [MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications](https://arxiv.org/abs/1704.04861) ） 和其它三方教程


## Mobilenet V2

Mobilenet V2 是 Mobilenet 的升级版，它的主要改进点在于优化了网络的结构，使得网络的计算效率更高，同时网络的精度也更高。


## 试试训练一个模型

在 [MaixHub](https://maixhub.com) 创建一个分类训练项目，然后采集数据，创建一个训练任务，参数选择你有的硬件平台，如果没有开发板可以使用手机，选择 mobilenetv1 或者 mobilenetv2 进行训练即可，训练完成后可以一键部署看看效果。