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
```
# 第一种实现方法
data = {'name':['Sarah','Mike','Chrisna'],
       'ages':[28,32,25]}
print(pd.DataFrame(data))
print("")
df[['name', 'ages']]
print("")
df.loc[0]

# 第二种实现方法
people = ['Sarah','Mike','Chrisna']
ages = [28,32,25]
df = pd.DataFrame({'name': pd.Series(people),
               'ages': pd.Series(ages)})
print(df)
```
运用**Pandas**和**Numpy**分析索契冬奥会各国的奖牌数量

```python
from pandas import DataFrame, Series

countries = ['Russian Fed.', 'Norway', 'Canada', 'United States',
              'Netherlands', 'Germany', 'Switzerland', 'Belarus',
              'Austria', 'France', 'Poland', 'China', 'Korea', 
              'Sweden', 'Czech Republic', 'Slovenia', 'Japan',
              'Finland', 'Great Britain', 'Ukraine', 'Slovakia',
             'Italy', 'Latvia', 'Australia', 'Croatia', 'Kazakhstan']
gold = [13, 11, 10, 9, 8, 8, 6, 5, 4, 4, 4, 3, 3, 2, 2, 2, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0]
silver = [11, 5, 10, 7, 7, 6, 3, 0, 8, 4, 1, 4, 3, 7, 4, 2, 4, 3, 1, 0, 0, 2, 2, 2, 1, 0]
bronze = [9, 10, 5, 12, 9, 5, 2, 1, 5, 7, 1, 2, 2, 6, 2, 4, 3, 1, 2, 1, 0, 6, 2, 1, 0, 1]
    
olympic_medal_counts = pd.DataFrame({
'Countries': pd.Series(countries),
'Gold': pd.Series(gold),
'Silver': pd.Series(silver),
'Bronze': pd.Series(bronze)
})
olympic_medal_counts_df = pd.DataFrame(olympic_medal_counts)
    
print(olympic_medal_counts_df)

'''
# 输出结果
         Countries  Gold  Silver  Bronze
0     Russian Fed.    13      11       9
1           Norway    11       5      10
2           Canada    10      10       5
3    United States     9       7      12
4      Netherlands     8       7       9
5          Germany     8       6       5
6      Switzerland     6       3       2
7          Belarus     5       0       1
8          Austria     4       8       5
9           France     4       4       7
10          Poland     4       1       1
11           China     3       4       2
12           Korea     3       3       2
13          Sweden     2       7       6
14  Czech Republic     2       4       2
15        Slovenia     2       2       4
16           Japan     1       4       3
17         Finland     1       3       1
18   Great Britain     1       1       2
19         Ukraine     1       0       1
20        Slovakia     1       0       0
21           Italy     0       2       6
22          Latvia     0       2       2
23       Australia     0       2       1
24         Croatia     0       1       0
25      Kazakhstan     0       0       1
'''

```
## 访问数据

- 用`df[ '列的名子' ]`可以调用相应的列的数据。
- 用`df.loc[ '列的索引']`可以调用相应行的数据。


```python
import pandas as pd
import numpy as np

data = {
    'year':[2010,2011,2012,2011,2012,2010,2011,2012],
    'team':['Bears','Bears','Bears','Packers','Packers','Lions','Lions','Lions'],
    'wins':[11,8,10,15,11,6,10,4],
    'losses':[5,8,6,1,5,10,6,12]
    
}

football = pd.DataFrame(data)

print(football)    #完成输出所有数据
'''
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
print(football['year'])    #输出年份列
'''
0    2010
1    2011
2    2012
3    2011
4    2012
5    2010
6    2011
7    2012
Name: year, dtype: int64
'''

print(football.year)    # 上一条语句的 另一种写法

print(football[['year','wins','losses']])    #此语句小括号内的参数必须用 两套 方括号 [[]] 来标示！！
'''
   year  wins  losses
0  2010    11       5
1  2011     8       8
2  2012    10       6
3  2011    15       1
4  2012    11       5
5  2010     6      10
6  2011    10       6
7  2012     4      12
'''

print(football.iloc[[0]])    # 输出第0行的数据， 行号必须用 两套 方括号 [[]] 来标示！！
'''
   year   team  wins  losses
0  2010  Bears    11       5
'''

print(football.loc[[0]])    # 同上一个语句的输出相同，但写法不同，这里需要查询资料确认

print(football[football.wins > 10])    # 输出特定特征变量大于某数值的数据
'''
   year     team  wins  losses
0  2010    Bears    11       5
3  2011  Packers    15       1
4  2012  Packers    11       5
'''

print(football[(football.wins > 10) & (football.team == "Packers")])    # 输出 多个条件 同时具备 的数据
'''
   year     team  wins  losses
3  2011  Packers    15       1
4  2012  Packers    11       5
'''
```
## 向量化输出数据

**lambda**函数是小型的内联函数，是在python中即时定义的。
`lambda x: x >= 1`将接受x输入的值并返回 x >= 1 或等于 True或 False的布尔值。

```python
import pandas as pd
import numpy as np

countries = ['Russian Fed.', 'Norway', 'Canada', 'United States',
              'Netherlands', 'Germany', 'Switzerland', 'Belarus',
              'Austria', 'France', 'Poland', 'China', 'Korea', 
              'Sweden', 'Czech Republic', 'Slovenia', 'Japan',
              'Finland', 'Great Britain', 'Ukraine', 'Slovakia',
             'Italy', 'Latvia', 'Australia', 'Croatia', 'Kazakhstan']
gold = [13, 11, 10, 9, 8, 8, 6, 5, 4, 4, 4, 3, 3, 2, 2, 2, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0]
silver = [11, 5, 10, 7, 7, 6, 3, 0, 8, 4, 1, 4, 3, 7, 4, 2, 4, 3, 1, 0, 0, 2, 2, 2, 1, 0]
bronze = [9, 10, 5, 12, 9, 5, 2, 1, 5, 7, 1, 2, 2, 6, 2, 4, 3, 1, 2, 1, 0, 6, 2, 1, 0, 1]
    
olympic_medal_counts = pd.DataFrame({
'Countries': pd.Series(countries),
'Gold': pd.Series(gold),
'Silver': pd.Series(silver),
'Bronze': pd.Series(bronze)
})
olympic_medal_counts_df = pd.DataFrame(olympic_medal_counts)
    
#print(olympic_medal_counts_df)
#print(olympic_medal_counts_df.Gold)
avg_gold = np.mean(olympic_medal_counts_df.Gold)    #输出金牌平均数
avg_silver = np.mean(olympic_medal_counts_df.Silver)    #输出银牌平均数
avg_bronze = np.mean(olympic_medal_counts_df.Bronze)    #输出铜牌平均数

#print(avg_gold)
#print(avg_silver)
#print(avg_bronze)
avgd = {'Avg Gold':avg_gold,'Avg Silver':avg_silver,'Avg Bronze':avg_bronze}
avg_medal_count = pd.Series(data = avgd, index = ['Avg Gold','Avg Silver','Avg Bronze'])
print(avg_medal_count)

'''
Avg Gold      3.807692
Avg Silver    3.730769
Avg Bronze    3.807692
dtype: float64
'''

```
## 矩阵和向量的乘法

```python
a = [1,2,3,4,5]
b = [2,3,4,5,6]
print(np.dot(a,b))

```

```python
#规定每个金牌4分，每个银牌2分，每个铜牌1分。
#使用numpy.dot函数，创建新的名为“olympic_points_df”的dataFrame，它包含：一列国家名称、一列“point”

# 通过观察之前得到的矩阵可以发现，只要用这个矩阵成以向量[4,2,1]就可以得到每个国家累计得分的数据

countries = ['Russian Fed.', 'Norway', 'Canada', 'United States',
              'Netherlands', 'Germany', 'Switzerland', 'Belarus',
              'Austria', 'France', 'Poland', 'China', 'Korea', 
              'Sweden', 'Czech Republic', 'Slovenia', 'Japan',
              'Finland', 'Great Britain', 'Ukraine', 'Slovakia',
             'Italy', 'Latvia', 'Australia', 'Croatia', 'Kazakhstan']
gold = [13, 11, 10, 9, 8, 8, 6, 5, 4, 4, 4, 3, 3, 2, 2, 2, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0]
silver = [11, 5, 10, 7, 7, 6, 3, 0, 8, 4, 1, 4, 3, 7, 4, 2, 4, 3, 1, 0, 0, 2, 2, 2, 1, 0]
bronze = [9, 10, 5, 12, 9, 5, 2, 1, 5, 7, 1, 2, 2, 6, 2, 4, 3, 1, 2, 1, 0, 6, 2, 1, 0, 1]
    
olympic_medal_counts = pd.DataFrame({
'Countries': pd.Series(countries),
'Gold': pd.Series(gold),
'Silver': pd.Series(silver),
'Bronze': pd.Series(bronze)
})
olympic_medal_counts_df = pd.DataFrame(olympic_medal_counts)

###

olympic_counts_df = pd.DataFrame({'Gold': pd.Series(gold),
                    'Silver': pd.Series(silver),
                    'Bronze': pd.Series(bronze)})    #创建新的矩阵以包含各国的奖牌数

olympic_points_df = np.dot(olympic_counts_df,[4,2,1])

print(olympic_medal_counts_df)    #输出完整数据矩阵
print("")
print(olympic_counts_df)    #仅输出各国各奖牌数据
print("")
print(olympic_points_df)    #输出各国奖牌换算成分数的向量

olympic_counties_points_df = pd.DataFrame({
    'Countries': pd.Series(countries),
    'Points': pd.Series(olympic_points_df)
})    #创建带有国家名称的得分榜
print(olympic_counties_points_df)
'''
         Countries  Points
0     Russian Fed.      83
1           Norway      64
2           Canada      65
3    United States      62
4      Netherlands      55
5          Germany      49
6      Switzerland      32
7          Belarus      21
8          Austria      37
9           France      31
10          Poland      19
11           China      22
12           Korea      20
13          Sweden      28
14  Czech Republic      18
15        Slovenia      16
16           Japan      15
17         Finland      11
18   Great Britain       8
19         Ukraine       5
20        Slovakia       4
21           Italy      10
22          Latvia       6
23       Australia       5
24         Croatia       2
25      Kazakhstan       1
'''
```

# 一点简单的启发
在本练习中，我们将执行一些基本的练习，类似于一位真实的数据科学家。

数据科学家的工作之一就是利用他的**直觉**和**洞察力**来编写算法和启发式方法。数据科学家还创建数学模型根据正在检查的数据的某些属性作出预测。

练习的数据集来自于一下连接：



因为当时乘客在逃离泰坦尼克号时特定的行为特征，因此可以作如下启发：1. 如果乘客是女性，应该假定该乘客幸存；2. 如果乘客是男性，应该假定该乘客没有幸存。

通过passenger['Sex']访问乘客性别，男性为male，女性为female。
将预测写回“predictions”字典，字典的键应该是乘客的ID。通过passenger['PassengerID']访问，若关联值为1，即幸存，为0,即没有幸存。
例如：
passenger_id = passenger['PassengerID']
predictions[passenger_id] = 1

```python

```
