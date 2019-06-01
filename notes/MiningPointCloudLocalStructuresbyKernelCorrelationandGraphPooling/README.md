# [Mining Point Cloud Local Structures by Kernel Correlation and Graph Pooling](https://arxiv.org/pdf/1712.06760)
与图像不同，由于自然无序的数据结构，使用深度网络的3D点云的语义学习具有挑战性。在现有的作品中，PointNet通过直接学习点集来取得了可喜的成果。然而，它没有充分利用一个点的局部邻域，其中包含细粒度的结构信息，这有助于更好的语义学习。在这方面，我们提出了两项新的业务，以更有效地利用局部结构来改进PointNet。第一个侧重于局部3D几何结构。类似于图像的卷积核，我们将点集内核定义为一组可学习的3D点，它们根据由核相关性测量的几何关系共同响应一组相邻数据点，改编自点云配准的相似性技术。第二个利用局部高维特征结构，通过在最近邻图上从3D位置进行重复特征聚合。实验表明，我们的网络工作可以有效地捕获本地信息，并在主要数据集上稳健地实现更好的性能。

# 论文动机
- PointNet 无法捕捉局部信息
- PointNet++ 速度慢，作者尝试从另一个方向来探索:是否有一种高效的、可学习的局部操作，带有清晰的几何解释，能够在保持其简单架构的同时，直接增强和改进原始切入点?

# 模型流程
![](模型.png)

# 实验结果

## 语义分割

# 改进方向
- 1、
  - 
# 疑问
- 

# 参考
- [泡泡点云时空](https://www.sohu.com/a/251288633_715754)