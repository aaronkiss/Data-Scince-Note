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

- 创建一个名为d的python字典，其中每个键都是一列的名称，而对应的值则是一个python序列
```python
import pandas as pd     # 下边代码只是示例，并不能正确执行
d = {'name:' Series(['Braund','Cummings','Heikkinen','Allen'],index = ['a','b','c','d']),
    'age': Series([22,38,26,35], index = ['a','b','c','d']),
    'fare': Series([7.25,7.83,8.05], index = ['a','b','d']),
    'survived': Series([False,True,True,False], index = ['a','b','c','d'])}
```
可执行代码：
```python
import pandas as pd
series = pd.Series(['Dave','Cheng-Han','Udacity',42,-178910578])
print(series)
##
series = pd.Series(['Dave','Cheng-Han',359,9001],
                  index = ['Instructor','Curriculum Manager','Course Number','Power Level'])
print(series)
##
series = pd.Series(['Dave', 'Cheng-Han', 359, 9001],
                       index=['Instructor', 'Curriculum Manager',
                              'Course Number', 'Power Level'])
print(series['Instructor'])
print("")
print(series[['Instructor', 'Curriculum Manager', 'Course Number']])
##
cuteness = pd.Series([1,2,3,4,5],index = ['Cockroach','Fish','Mini Pig','Puppy','Kitten'])

print(cuteness > 3)
print("")
print(cuteness[cuteness > 3])
```
- 创建**DateFrame**
```python
import numpy as np
import pandas as pd

# 建立二维数据结构

data = {'year':[2010,2011,2012,2011,2012,2010,2011,2012],
       'team':['Bears','Bears','Bears','Packers','Packers','Lions','Lions','Lions'],
       'wins':[11,8,10,15,11,6,10,4],
       'losses':[5,8,6,1,5,10,6,12]}
football = pd.DataFrame(data)
print(football)

'''
输出结果
   year     team  wins  losses
0  2010    Bears    11       5
1  2011    Bears     8       8
2  2012    Bears    10       6
3  2011  Packers    15       1
4  2012  Packers    11       5
5  2010    Lions     6      10
6  2011    Lions    10       6
7  2012    Lions     4      12
'''

##

data = {'year':[2010,2011,2012,2011,2012,2010,2011,2012],
       'team':['Bears','Bears','Bears','Packers','Packers','Lions','Lions','Lions'],
       'wins':[11,8,10,15,11,6,10,4],
       'losses':[5,8,6,1,5,10,6,12]}
football = pd.DataFrame(data)
print(football.dtypes)
print("")
print(football.describe())
print("")
print(football.head())
print("")
print(football.tail())

‘’‘
输出结果
year       int64
team      object
wins       int64
losses     int64
dtype: object

              year       wins     losses
count     8.000000   8.000000   8.000000
mean   2011.125000   9.375000   6.625000
std       0.834523   3.377975   3.377975
min    2010.000000   4.000000   1.000000
25%    2010.750000   7.500000   5.000000
50%    2011.000000  10.000000   6.000000
75%    2012.000000  11.000000   8.500000
max    2012.000000  15.000000  12.000000

   year     team  wins  losses
0  2010    Bears    11       5
1  2011    Bears     8       8
2  2012    Bears    10       6
3  2011  Packers    15       1
4  2012  Packers    11       5

   year     team  wins  losses
3  2011  Packers    15       1
4  2012  Packers    11       5
5  2010    Lions     6      10
6  2011    Lions    10       6
7  2012    Lions     4      12
’‘’
```

