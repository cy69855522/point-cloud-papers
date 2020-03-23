# DGCNN
1. Input: 点云`X[N, 3]`
2. 通过KNN获得索引，进一步得到中心点`X_i[N, k, C]`和邻点`X_j[N, k, C]`
3. 计算边特征：`e = Cat(x_i, x_j - x_i) # [N, k, C]`
4. 升维：`e = MLP(e) # [N, k, C]`
5. Output: `Max(e) # [N, C]`

# GSCNN
![](示意图.png)

1. Input: 点云`X[N, 3]`
2. 通过KNN获得索引，进一步得到中心点`X_i[N, k, C]`和邻点`X_j[N, k, C]`；通过特征值获得索引，进一步得到中心点`X_i[N, k, C]`和特征值邻点`X_j[N, k, C]`
3. 计算边特征：`e = Max(MLP(Cat(x_j, x_j - x_i, x_j_eig, x_j_eig - x_i))) # [N, k, C]`
4. 升维：`e = MLP(e) # [N, k, C]`
5. Output: `Max(e) # [N, C]`

![](结果对比.png)
