# 决策树 (Desicion Tree)
* 已知特征的情况下，构建树形结构进行分析的模型（有监督分类/回归任务）

>* 内部节点：特征的测试
>* 分支：特征取值的可能结果
>* 叶结点：类别

* 主要模型：
>* ID3（基于**信息增益**）
>* C4.5（基于**信息增益比**）
>* CART（基于**二叉决策树**）
>* RF（基于**并行集成**决策树）
>* GBDT/XGBoost/LightGBM（基于**串行集成**决策树）

* 信息熵（entropy）：描述信息**不确定性**的值（也为**信息量**的值，该值越小纯度越高）
> 假设数据集D有x类，其中第k类占比为$p_k$，则信息熵公式为
>$$entropy(D)=-\sum_{i=1}^{x}p_i log_2(p_i)$$
> 信息熵的最小值为0（不确定度最小，纯度最高，概率要么为1要么为0），信息熵最大为$log_2|x|$（均匀分布）
* 信息增益（Information Gain）：选择某个特征属性进行划分时信息熵的变化（描述了该特征带来的信息量的多少）
> $$Gain(D,A)=entropy(D)-entropy(D|A)$$
> $$=-entropy(D)-\sum_{i=1}^{v}\frac{|D_v|}{|D|} entropy(D_v)$$
> 其中entropy(D|A)为特征A给定条件下D的经验**条件熵**（A的取值为{ $a_1,a_2,...,a_v$ }, $D_v$ 为D中A属性为 $a_v$ 的集合）

这里以西瓜数据集为例[1]，瓜分为好瓜、坏瓜，所以$x=2$。其中总瓜数为17，好瓜为8，坏瓜为9。
> 信息熵$entropy(D)=-(\frac{8}{17}\log_2(\frac{8}{17})+\frac{9}{17}\log_2(\frac{9}{17}))$
> 如果使用ID3（基于信息增益），假设所选的特征为色泽：
>> D1（色泽=青绿）的总样本数为6，其中好瓜为3，坏瓜为3，信息熵为$entropy(D_1)=-(\frac{3}{6}log_2(\frac{3}{6})+\frac{3}{6}log_2(\frac{3}{6}))$ <br>
>> D2（色泽=乌黑）的总样本数为6，其中好瓜为4，坏瓜为2，信息熵为$entropy(D_2)=-(\frac{4}{6}log_2(\frac{4}{6})+\frac{2}{6}log_2(\frac{2}{6}))$ <br>
>> D3（色泽=浅白）的总样本数为5，其中好瓜为1，坏瓜为4，信息熵为$entropy(D_2)=-(\frac{1}{6}log_2(\frac{1}{6})+\frac{4}{6}log_2(\frac{4}{6}))$ <br>
> 信息增益为:
> $$Gain(D,A)=entropy(D)-\sum_{i=1}^{3}\frac{|D_i|}{D}entropy(D_i)$$
> $$=-(\frac{8}{17}\log_2(\frac{8}{17})+\frac{9}{17}\log_2(\frac{9}{17}))-\frac{6}{17}(-(\frac{1}{2}log_2(\frac{1}{2})+\frac{1}{2}log_2(\frac{1}{2})))-\frac{6}{17}(-(\frac{2}{3}log_2(\frac{2}{3})+\frac{1}{3}log_2(\frac{1}{3})))-\frac{5}{17}(-(\frac{1}{5}log_2(\frac{1}{5})+\frac{4}{5}log_2(\frac{4}{5})))$$

* 信息增益率（Gain Ratio）
>* 信息增益较容易受到特征取值的数量的影响（通常来说，特征取值数量越多（上面的x越大），越倾向于产生熵较小的划分结果，此时信息增益较大，故使用信息增益倾向于取值较多的特征）。
>* 信息增益率公式：
>> $$GainRatio(D,A)=\frac{Gain(D,A)}{IV(A)}$$
>> $$IV(A)=-\sum_{i=1}^{v}$$
> $$Gain(D,A)=entropy(D)-entropy(D|A)$$




# GBDT (Gradient Boosting Decision Tree)
* GBDT中的决策树为回归树
* 


[1]https://www.showmeai.tech/article-detail/190
