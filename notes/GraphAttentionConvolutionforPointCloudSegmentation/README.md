# [Graph Attention Convolution for Point Cloud Segmentation](https://engineering.purdue.edu/~jshan/publications/2018/Lei%20Wang%20Graph%20Attention%20Convolution%20for%20Point%20Cloud%20Segmentation%20CVPR2019.pdf)
标准卷积由于其特征的各向同性，在语义点云分割中存在固有的局限性。它忽略了物体的结构，导致分割结果中物体轮廓差，假区域小。我们提出了一种新的图形注意卷积(GAC)，它的卷积核可以被动态地雕刻成特定的形状，以适应对象的结构。具体来说，GAC通过给不同的相邻点分配特定的注意权重，根据它们的特点选择性地聚焦于它们最相关的部分。卷积核的形状是由学习到的注意权值分布决定的。GAC虽然简单，但是可以捕捉点云的结构化特征，进行细粒度分割，避免了对象之间的特征污染。从理论上讲，我们对GAC的表达能力进行了深入的分析，展示了它如何学习点云的特征。经验上，通过对室内和室外数据集的挑战实验，我们提出的GAC在现有的深度学习方法的基础上，展示了最先进的性能。
# 针对的问题
![](问题.png)

# 模型流程
![](模型.png)

![](注意力.png)

# 实验结果
![](实验1.png)
![](实验2.png)
![](实验3.png)

# 改进方向

# 疑问
