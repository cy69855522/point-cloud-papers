# [Graph Attention Convolution for Point Cloud Segmentation](https://engineering.purdue.edu/~jshan/publications/2018/Lei%20Wang%20Graph%20Attention%20Convolution%20for%20Point%20Cloud%20Segmentation%20CVPR2019.pdf)
  标准卷积由于其特征的各向同性，在语义点云分割中存在固有的局限性。它忽略了物体的结构，导致分割结果中对物体轮廓的描述较差，有小部分伪区域。作者提出了一种新的图形注意卷积(GAC)，它的卷积核可以被动态地雕刻成特定的形状，以**适应对象的结构**。具体来说，GAC通过给不同的相邻点分配特定的注意权重，根据它们的特点选择性地聚焦于它们最相关的部分。卷积核的形状是由学习到的注意权值分布决定的。GAC虽然简单，但是可以捕捉点云的结构化特征，进行**细粒度**分割，避免了对象之间的**特征污染**。从理论上讲，我们对GAC的表达能力进行了深入的分析，展示了它如何学习点云的特征。经验上，通过对室内和室外数据集的挑战实验，我们提出的GAC在现有的深度学习方法的基础上，展示了最先进的性能。
# 论文动机
![](问题.png)
- 标准图卷积具有**各向同性**，如上图左，对来自不同方向的节点一视同仁。GAC 旨在利用**注意力**机制为不同的相邻点分配不同权重，避免**特征污染**。
  - Left: The weights of standard convolution are determined by the neighbors’ spatial positions, and the learned feature at point 1 characterizes all of its neighbors indistinguishably.
  - Right: In GAC, the attentional weights on ”chair” (the brown dotted arrows) are masked, so that the convolution kernel can focus on the points of ”table”.

# 模型流程
![](模型.png)
- 

![](注意力.png)

# 伪代码

# 实验结果
![](实验1.png)
![](实验2.png)
![](实验3.png)

# 改进方向
- 1、注意力机制的归一化操作仅考虑自身节点，缺乏邻域节点度信息
  - 可以参考归一化的拉普拉斯阵，除了考虑聚合节点 i 的度 Di，还应该考虑被聚合节点 j 的度 Dj [参考：空域角度GCN](https://www.zhihu.com/question/54504471/answer/611222866)
  
  ![](对称归一化.png)

- 2、没有 Bn层，如果层数加深应该增加
- 3、浅层感受野太小
  - 由于网络结构不深，浅层网络所观察到的范围很有限，可以引入全局信息，参考 PointNet
- 4、结构感受野限定
  - 注意力机制的参考点为｛一阶相对位置，一阶特征差分｝，仅考虑了一阶邻域内的结构特征，不能通过网络层级的提升获得更高的感受野即无法获得二阶邻域的结构特征（除了混淆在特征中的信息），可以 ①扩大参考点范围 ②类比卷积，聚合邻域注意力
- 5、下采样部分没有快捷连接
  - 虽然网络利用 U-Net 结构在上采样部分引入恒等映射，但对于下采样部分却没有，可以引入线性层构造残差学习
- 6、逐层池化不仅破坏特征信息还破坏了结构信息
  - 引入胶囊，将低层次的信息传递到被认为能最好地处理这些信息的胶囊
- 7、FPS 采样对噪声鲁棒性不强
  - 考虑排除 outer，或构建可学习的 FPS
- 8、透视角度易引起点云采样不均，疏密程度受影响，除此之外网络也应该对物体的刚性变换具有强鲁棒性
  - 引入 STN 对点云进行仿射矫正
# 疑问
