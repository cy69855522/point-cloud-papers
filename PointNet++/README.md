# [PointNet++: Deep Hierarchical Feature Learning on Point Sets in a Metric Space](https://arxiv.org/abs/1706.02413)
以前很少有人研究深度学习在点集中的应用。PointNet是这方面的先驱。然而，PointNet并不能捕捉到由度量（metric）空间点所产生的局部结构，从而限制了它识别分类精密模型（ﬁne-grained patterns）和对复杂场景的通用性。在PointNet++中，我们引入了一个递归地将PointNet应用于输入点集的嵌套分区的层次神经网络。通过度量空间距离，我们的网络能够在增长的上下文尺度中学习局部特征。进一步观察到，点集采样通常是不同密度的，这导致训练在均匀密度下的网络性能大大降低，我们提出了新的集学习层，自适应地结合来自多个尺度的特征。实验表明，我们的PointNet++网络能够高效、鲁棒地学习深度点集特性。特别是，在具有挑战性的3D点云基准测试中，获得了明显优于最先进水平的结果。

## 背景
- 
## 模型流程
![](结构.png)
- 首先，我们用基础空间的距离度量将点集划分为重叠的局部区域。与CNN相似，我们从小区域内提取点云得局部特征，捕捉精细的几何结构;这些局部特征被进一步分组成更大的单元，并被处理用来产生更高级别的特征。重复这个过程直到我们得到整个点集的特征。
## 要点记录
### What
1. PointNet没有捕获到由度量（metric）引起的局部结构特征。
2. 点的密度或其他属性在不同的位置上可能不一致——在三维扫描中，密度变化可以来自透视效果、径向密度变化、移动等。
### How
1. PointNet++使用了分层抽取特征的思想，把每一次叫做set abstraction。分为三部分：采样层、分组层、特征提取层。
  - 首先来看**采样层**，为了从稠密的点云中抽取出一些相对较为重要的中心点，采用FPS（farthest point sampling）最远点采样法。
  - 然后是**分组层**，在上一层提取出的中心点的底层欧式空间中的一个邻居球范围内寻找最近个k近邻点组成patch；
  - **特征提取层**是将这k个点通过小型pointnet网络进行卷积和pooling得到的特征作为此中心点的特征，再送入下一个分层继续。这样每一层得到的中心点都是上一层中心点的子集，并且随着层数加深，中心点的个数越来越少，但是每一个中心点包含的信息越来越多。
2. 
### Why
1. - 与以固定步长扫描空间的体积cnn相比，我们的局部接受域既依赖于输入数据，也依赖于度量，因此更有效。
### Result
- 
### Drawbacks
- 对点集进行采样丢失了信息
- 对点集的采样鲁棒性差，无法避免采样到噪点，影响精度
- 多尺度的特征提取实际上并未解决密度不均匀的问题
## 好句
- CNN介绍：However, exploiting local structure has proven to be important for the success of convolutional architectures. A CNN takes data defined on regular grids as the input and is able to progressively capture features at increasingly larger scales along a multi-resolution hierarchy. At lower levels neurons have smaller receptive fields whereas at higher levels they have larger receptive fields. The ability to abstract local patterns along the hierarchy allows better generalizability to unseen cases.
## 参考
- [博客解析](https://blog.csdn.net/qq_15332903/article/details/80261951)
## 提问
1. 
