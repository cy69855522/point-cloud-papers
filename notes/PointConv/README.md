# [PointConv: Deep Convolutional Networks on 3D Point Clouds](http://arxiv.org/pdf/1811.07246v1.pdf)
与在常规密集网格中表示的图像不同，3D点云是不规则且无序的，因此对它们应用卷积可能是困难的。在本文中，我们将动态滤波器扩展为一个名为PointConv的新卷积运算。PointConv可以应用于点云以构建深度卷积网络。我们将卷积核视为由权重和**密度**函数组成的3D点的局部坐标的非线性函数。关于给定点，利用多层感知器网络学习权重函数，并且密度通过核密度估计来起作用。为了有效地计算权重函数，提出了一种新颖的重构方法，这使我们能够大幅度扩展网络并显着**提高其性能**。学习的卷积核可用于计算3D空间中任何点集上的平移不变和置换不变卷积。此外，PointConv还可以用作反卷积运算符，以将子采样点云中的要素传播回其原始分辨率。ModelNet40，ShapeNet和ScanNet上的实验表明，基于PointConv构建的深度卷积神经网络能够在3D点云上实现具有挑战性的语义分割基准测试的最新技术。此外，我们将CIFAR-10转换为点云的实验表明，构建在PointConv上的网络可以匹配类似结构的2D图像中卷积网络的性能。

# 论文动机
- 密度
- 效率

# 模型流程
## 蒙特卡罗卷积
![](公式4.png)
- Sum(MLP1(△p) * f / MLP2(d))     p 是坐标 h 是特征
## 上采样
![](特征传播.png)
- 插值 + 拼接 + PointConv
## 前向传播
![](模型.png)
## 效率模型
![](效率模型.png)
- 每个通道共享一组卷积核
# 实验结果
## ModelNet40 CAD模型分类
![](实验1.png)
## ShapeNet 零件分割
![](实验2.png)
## ScanNet 真实场景语义分割
![](实验3.png)
## Cifar10
![](实验4.png)
## 消融实验
![](实验5.png)
# 改进方向
- 1、。。。
  - 
# 疑问
![](疑问1.png)
- 蒙特卡罗采样

# 参考
- 
