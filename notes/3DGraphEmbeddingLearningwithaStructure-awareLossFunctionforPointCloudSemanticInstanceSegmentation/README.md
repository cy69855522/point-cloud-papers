# [3D Graph Embedding Learning with a Structure-aware Loss Function for Point Cloud Semantic Instance Segmentation](https://arxiv.org/pdf/1902.05247.pdf)
![](介绍.png)
本文介绍了一种新的点云三维语义实例分割方法。称为子流形稀疏卷积网络的三维卷积神经网络用于同时生成语义预测和实例嵌入。为了获得每个3D实例的判别嵌入，提出了结构感知损失函数，其考虑**结构信息**和**嵌入信息**。为了为每个3D实例获得更一致的嵌入，建议基于注意力的k最近邻居（KNN）为不同的邻居分配不同的权重。基于基于注意力的KNN，作者在稀疏卷积网络之后添加图形卷积网络以获得重新嵌入。网络可以端到端地进行培训。利用简单的均值漂移算法对重新嵌入的嵌入进行聚类，以获得最终的实例预测。因此，作者的框架可以输出语义预测和实例预测。实验表明，作者的方法优于ScanNet基准测试和NYUv2数据集的所有最新方法。

# 论文动机
## 前向传播
![](模型.png)
- 

# 模型流程

# 实验结果

## 语义分割

# 改进方向
- 1、
  - 
# 疑问
- 

# 参考
- 