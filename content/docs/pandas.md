* create dataframe 
```python
fruits = pd.DataFrame({"Apples":[30],"Bananas":[21]})
fruits = pd.DataFrame([[30,21]],columns=['Apples','Bananas'])
```


* rename index or column name


* create 
```python
quantities = ['4 cups', '1 cup', '2 large', '1 can']
items = ['Flour', 'Milk', 'Eggs', 'Spam']
recipe = pd.Series(quantities, index=items, name='Dinner')
```

* read pd from csv, solve the index column
```python
df.rename(index=lambda x: x if x.beginwith("a": x+"b",{"a":"b"}"))
df.set_index('S',drop=False)
```

```python
reviews = pd.read_csv('../input/wine-reviews/winemag-data_first150k.csv', index_col=0)
```

* rename the column
```python
review.rename(columns =dict(region='region_1') )
```
* rename the index name 

``` python
reviews.rename_axis('wine',axis='row')
```



* DecisionTreeRegressor 

```python
from sklearn.tree import DecisionTreeRegressor
#specify the model. 
#For model reproducibility, set a numeric value for random_state when specifying the model
iowa_model = DecisionTreeRegressor(random_state=11)
# Fit the model
iowa_model.fit(X,y)

```

# 1.10
1. 简述机器学习项目的一般流程
  机器学习一般分为抽象问题，获取数据，训练模型整断调优，上线
2. 哪些机器学习算法需要做特征归一化，哪些不需要？为什么？
   需要归于化的模型:KNN,线性回归,逻辑回归，支持向量机，神经网络等 这些模型的训练都依赖于距离或者梯度，否则会弱化某些特征
3. One-hot的作用是什么？为什么不直接使用数字作为表示
  One-hot 就是把类别转化为机器学习算法利用的一种形式过程。类别特征都是独立的，如果使用数字会造成模型学习到类别的顺序性。
  
4. 什么是数据不平衡，如何解决？
   数据不平衡是指数据集中各个类别的数量分布不均衡。不平衡数据一般是由于数据产生的原因导致的，类别少的样本通常是发生的频率低，需要很长的周期进行采集。
   处理办法：处理数据不平衡的主要方法：1.欠采样;2.过采样;3.综合采样;4.模型集成;5.调整类别权重或者样本权重
5. 请比较欧式距离与曼哈顿距离？
   * 欧式距离就是欧式度量，就是起点和终点的直线距离，曼哈顿距离是固定直角坐标系上两点所形成的线段对轴产生的投影的距离总和
   
# 1.11

1. 为什么一些场景中使用余弦相似度而不是欧式距离？
高维度情况下，欧式距离受到维度影响很大
2. 在模型评估过程中，过拟合和欠拟合具体指什么现象
过拟合指的是训练集效果很好，但是测试集的效果差很多
欠拟合指的是模型学习能力弱，数据复杂，训练集和测试集效果都很差
auc
4. 逻辑回归的损失函数  
$$
L_{\log}(y, p) = -(y \log (p) + (1 - y) \log (1 - p))
$$
5. 逻辑回归可以处理多标签分类问题么？  
可以，可以使用sigmoid替代softmax函数



# 1.12
1. 写出全概率公式&贝叶斯公式  
> 全概率公式 $ P(A) = \sum_i P(B_i)P(A|B_i) $  
> 贝叶斯公式 $ P(A|B) = \sum P(B)P(A|B)*P(B)*$  
2. 朴素贝叶斯为什么“朴素naive”？  
它是具有统计特性来给出结果的，需要假定所有数据特征都是独立的
3. 朴素贝叶斯有没有超参数可以调？  
没有
4. 朴素贝叶斯的工作流程是怎样的？  
* 准备阶段
* 训练阶段
* 应用阶段
5. 朴素贝叶斯对异常值敏不敏感？  
不敏感



1. 什么是集成学习算法？  
集成学习是一种训练思路，分为

2. 集成学习主要有哪几种框架, 并简述它们的工作过程？  
集成学习分为bagging和boosting:
* bagging是多个模型分别预测分别给出结果，再采用投票选举方式决定最终结果
* boosting是多个算法联合训练，根据权重来确定各个模型的贡献比例
3. Boosting算法有哪两类，它们之间的区别是什么？
* adaboost和gbdt
4. 什么是偏差和方差？ __，
偏差是实验值或者预测值跟实际值之间的差值的平均
方差是实验值或者预测值跟实际值之间的差值的平方和

5. 为什么说Bagging可以减少弱分类器的方差，而Boosting 可以减少弱分类器的偏差？__
Bagging由于每个算法都是独立训练的，然后选取的是大致一致的值，没有完全参考跟真实值的差值，这样数据更接近所有模型预测的平均值，方差小
Boosting训练是根据每个模型的错误率不断调整权重比例的，这样能够尽可能的减少偏差。




1. 集成学习解决了什么样的问题？或者说集成学习提出的动机是什么？  
突破单个模型的局限性 
2. 简述一下随机森林算法的原理  
随机森林使用了集成学习中的Bagging方法,他是由很多决策树构成的，不同决策树之间没有关联。
当进行分类任务是，使用新样本，随机抽取某些特征，训练森林中的每一个决策树，最终预测结果时，看所有决策树结果哪个分类多，就是预测结果。
3. 随机森林的随机性体现在哪里？  
随机使用样本和随机使用特征
4. 随机森林算法的优缺点  
优点:
* 当数据维度高时不用降维
* 可以判断特征的重要程度
* 判断不同特征之间的影响
* 不容易过拟合
* 训练快，可以并行化
缺点:
* 对于不同取之的属性数据，取值划分比较多的属性对随机森林产生很大影响
* 没有使用所有样本训练，是否由提升空间
5. 随机森林为什么不能用全样本去训练m棵决策树？  
使用全样本会导致训练的树都是一样的， 容易过拟合

1. 随机森林和GBDT的区别？  
随机森林使用的Bagging的思想，GBDT采用Boosting的思想

2. 在训练每颗子树时，该如何决定最优的随机特征个数？  
根据每个特征划分所产生的信息增益或者Gini值最小来确定最优特征
3. 随机森林算法跟深度学习算法相比有哪些优势？  
不会造成过拟合，训练速度快

4. 如果让你在GDBT算法和随机森林算法中选择一个来解决实际问题，你通常会做哪些考量？  
参考数据集的特征维度的多少
5. 简述AdaBoost 算法的工作原理  
AdaBoost是以知一定数量的弱决策树，通过训练调整他们的权重，即提高前一轮弱分类器错误分类的权值，而降低那些分类正确的权重，给出预测
