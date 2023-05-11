# K-means

* 数据到中心点的距离：l2距离的平方

### K-means算法步骤
采用EM算法
* 更新中心点：初始中心点随机选取；迭代时选择同一类样本点的重心作为新的中心
$$Z_l=\frac{1}{N_l}\sum_{i=1}^Nr_{il}x_i(第l类的重心，r_{il}为数据点i是否属于l类，N_l是l类中点的个数)$$
* 分配数据点：将数据点分配到最近的中心点

$$r_{ik}=
\begin{cases}
1& {k=argmin_l||x_i-z_l||^2}\\
0& {otherwise}
\end{cases}$$

* 直到中心点和数据点都不再发生变化
* 
