# [A Graph-CNN for 3D Point Cloud Classification](http://arxiv.org/pdf/1812.01711v1.pdf)
图形卷积神经网络（Graph-CNN）扩展了传统的CNN，以处理图形支持的数据。在图上处理数据时的主要挑战是支持集（图的顶点）通常不具有自然排序，并且通常，图的拓扑结构不是规则的（即，顶点并非都是相同的邻居数量）。因此，Graph-CNN具有处理从点状流采样获得的3D点云数据的巨大潜力。在本文中，我们开发了一个GraphCNN，用于分类3D点云数据，称为PointGCN。该架构将本地化图形卷积与两种类型的图形下采样操作（也称为池化）相结合。通过使用Graph-CNN对点云局部结构的有效探索，所提出的架构在3D对象分类基准ModelNet上实现了竞争性能，并且我们的架构比竞争方案更稳定。

# 论文动机
- 在点云结构上构造谱卷积
# 模型流程
## 前向传播
![](模型.png)
# 实验结果

## 语义分割

# 改进方向
- 1、
  - 
# 疑问
- 

# 好句
- Previous work has taken different approaches to classifying 3D point clouds [14, 15, 16, 17, 18, 19, 20, 21], including rendering and processing a collection of 2D images (projections of the points onto an image plane from different perspectives), or binning the points into voxels. However, the former involves extensive data augmentation, preprocessing and heavy computation, and the latter introduces discretization error as well as use a relatively sparse format to represent the 3D data. 

# 参考
- 
