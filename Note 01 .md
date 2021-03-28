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
