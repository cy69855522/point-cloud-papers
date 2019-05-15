# [PointNet++: Deep Hierarchical Feature Learning on Point Sets in a Metric Space](https://arxiv.org/abs/1706.02413)
以前很少有人研究深度学习在点集中的应用。PointNet是这方面的先驱。然而，PointNet并不能捕捉到由度量（metric）空间点所产生的局部结构，从而限制了它识别分类精密模型（ﬁne-grained patterns）和对复杂场景的通用性。在PointNet++中，我们引入了一个递归地将PointNet应用于输入点集的嵌套分区的层次神经网络。通过度量空间距离，我们的网络能够在增长的上下文尺度中学习局部特征。进一步观察到，点集采样通常是不同密度的，这导致训练在均匀密度下的网络性能大大降低，我们提出了新的集学习层，自适应地结合来自多个尺度的特征。实验表明，我们的PointNet++网络能够高效、鲁棒地学习深度点集特性。特别是，在具有挑战性的3D点云基准测试中，获得了明显优于最先进水平的结果。

## 背景
- FPS 最远点采样法：Farthest Point Sampling 的原理是先随机选一个点,然后选择离这个点距离最远的点加入点集,然后继续迭代,选择距离点集中所有点最远的点,直到选出需要的个数为止。
## 模型流程
![](结构.png)
- 首先，我们用基础空间的距离度量将点集划分为重叠的局部区域。与CNN相似，我们从小区域内提取点云得局部特征，捕捉精细的几何结构;这些局部特征被进一步分组成更大的单元，并被处理用来产生更高级别的特征。重复这个过程直到我们得到整个点集的特征。
## 要点记录
### What
1. PointNet没有捕获到由度量（metric）引起的局部结构特征。
2. 点的密度或其他属性在不同的位置上可能不一致——在三维扫描中，密度变化可以来自透视效果、径向密度变化、移动等。
### How
1. PointNet++使用了分层抽取特征的思想，把每一层叫做set abstraction。每一层分为三部分：采样层、分组层、PointNet层。
    - 首先来看**采样层**，采样层从输入点中选择一组点，定义局部区域的质心。为了从稠密的点云中抽取出一些相对较为重要的中心点，采用FPS（farthest point sampling）最远点采样法。
    - 然后是**分组层**，分组层通过寻找质心周围的“相邻”点来构造局部区域集。PointNet++在多个尺度上利用邻近球法，获得多组局部特征，以实现健壮性和细节捕获。
    - **PointNet层**使用一个迷你PointNet结构作为局部特征学习模块，将输入编码为特征向量。
    总之就是类比了2D空间中的卷积，以球半径作为卷积核尺寸。
2. ![](多尺度拼接.png)
    通过两种不同的方式获得多组特征后拼接为一组特征向量。
    a. 应用不同尺度的分组层是获取多尺度模式的一种简单而有效的方法，然后根据不同的切入点提取每个尺度的特征。不同尺度的特征被连接起来形成一个多尺度的特征。
    b. 某一层Li区域的特征是两个向量的结合。一个向量（图左）通过运用几何抽象层，并将提取到的Li−1层中的每一组点邻域集特征综合起来的方式来获取，另一个向量(图右)是通过使用单个PointNet层直接处理局部区域中的所有原始点而获得的特性。
### Why
1. - 与以固定步长扫描3D空间的cnn相比，我们的局部接受域既依赖于输入数据，也依赖于度量，因此更有效率和效果。
   - ball query 的局部邻域保证了一个固定的区域尺度，从而使局部区域特征在空间上具有更好的可泛化性。该网络在训练过程中使用dropout，学习自适应地检测不同尺度下的权值模式，并根据输入数据结合多尺度特征。
   - 提取全局特征。
### Result
- 
### Drawbacks
- 对点集进行采样丢失了信息
- 对点集的采样鲁棒性差，无法避免采样到噪点，影响精度
- 多尺度的特征提取并未完全解决密度不均匀的问题
## 好句
- CNN介绍：However, exploiting local structure has proven to be important for the success of convolutional architectures. A CNN takes data defined on regular grids as the input and is able to progressively capture features at increasingly larger scales along a multi-resolution hierarchy. At lower levels neurons have smaller receptive fields whereas at higher levels they have larger receptive fields. The ability to abstract local patterns along the hierarchy allows better generalizability to unseen cases.
## 参考
- [博客解析](https://blog.csdn.net/qq_15332903/article/details/80261951)
- [译文](https://blog.csdn.net/weixin_40664094/article/details/83902950)
## 提问
1. 
