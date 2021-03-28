### 背景：
1973年，加州大学伯克利分校（UC-Berkeley）因性别歧视被起诉。它的录取数据显示，申请加州大学伯克利分校研究生院的男性比女性更容易被录取。

研究生院刚刚接受了44％的男性申请者，但仅接受了35％的女性申请者。差异是如此之大，以至于不可能是偶然的。

通过更仔细地查看数据，您可能会发现故事的意义远不止这些。

### 数据
您为什么不下载1973年加州大学伯克利分校研究生入学数据，自己看看。该数据集包含有关六个最受欢迎部门的信息。
随时使用您喜欢的工具（例如Excel，R甚至笔和纸）检查和分析数据。

给你的问题
现在，您是否同意加州大学伯克利分校在录取过程中歧视妇女？
是还是不是？

# Pandas
Pandas中的数据经常包含在名为**DataFrame**的结构中。
DataFrame是已标记的**二维数据结构**。数据类型：字符串、整数、浮点、布尔。可以看成是Excel表格。
例如：泰坦尼克号的幸存者数据  
Name|Age|Fare|Survived
---|---|---|---
Braund|22|7.25|False
Cammings|38|71.83|True
Heikkinen|26|NaN|True
Allen|35|8.05|False

1. 创建一个名为d的python字典，其中每个键都是一列的名称，而对应的值则是一个python序列
```python
d = {'name:' Series(['Braund','Cummings','Heikkinen','Allen'],index = ['a','b','c','d']),
    'age': Series([22,38,26,35], index = ['a','b','c','d']),
    'fare': Series([7.25,7.83,8.05], index = ['a','b','d']),
    'survived': Series([False,True,True,False], index = ['a','b','c','d'])}
```
