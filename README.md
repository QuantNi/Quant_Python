# 【2021】Python数据清洗方法汇总



## Tips 

```python
#公式用法
np.random.randint?
help(np)

#可以加那些后缀
dir(np)

#包导入
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import re
import os
import statsmodels.api as sm
import statsmodels.formula.api as smf
import time
import scipy.stats as stats

#快速查看文件内容
!type ex5.csv

#查看dataframe属性
data.info()

plt.rcParams['font.sans-serif']=['SimHei']#中文乱码
plt.rcParams['axes.unicode_minus']=False#中文乱码
```

## 基础运算

| 运算符 | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| +      | 加 - 两个对象相加                                            |
| -      | 减 - 得到负数或是一个数减去另一个数                          |
| *      | 乘 - 两个数相乘或是返回一个被重复若干次的字符串              |
| /      | 除 - x除以y                                                  |
| %      | 取模 - 返回除法的余数                                        |
| **     | 幂 - 返回x的y次幂                                            |
| //     | 取整除 - 返回商的整数部分（向下取整）                        |
| ==     | 等于 - 比较对象是否相等                                      |
| !=     | 不等于 - 比较两个对象是否不相等                              |
| >      | 大于 - 返回x是否大于y                                        |
| <      | 小于 - 返回x是否小于y。所有比较运算符返回1表示真，返回0表示假。这分别与特殊的变量True和False等价。 |
| >=     | 大于等于 - 返回x是否大于等于y。                              |
| <=     | 小于等于 - 返回x是否小于等于y。                              |
| &      | 按位与运算符：参与运算的两个值,如果两个相应位都为1,则该位的结果为1,否则为0 |
| \|     | 按位或运算符：只要对应的二个二进位有一个为1时，结果位就为1。 |
| ^      | 按位异或运算符：当两对应的二进位相异时，结果为1              |
| ~      | 按位取反运算符：对数据的每个二进制位取反,即把1变为0,把0变为1 。~x 类似于 -x-1 |
| <<     | 左移动运算符：运算数的各二进位全部左移若干位，由 << 右边的数字指定了移动的位数，高位丢弃，低位补0。 |
| >>     | 右移动运算符：把">>"左边的运算数的各二进位全部右移若干位，>> 右边的数字指定了移动的位数 |

| =    | 简单的赋值运算符 | c = a + b 将 a + b 的运算结果赋值为 c |
| ---- | ---------------- | ------------------------------------- |
| +=   | 加法赋值运算符   | c += a 等效于 c = c + a               |
| -=   | 减法赋值运算符   | c -= a 等效于 c = c - a               |
| *=   | 乘法赋值运算符   | c *= a 等效于 c = c * a               |
| /=   | 除法赋值运算符   | c /= a 等效于 c = c / a               |
| %=   | 取模赋值运算符   | c %= a 等效于 c = c % a               |
| **=  | 幂赋值运算符     | c = a 等效于 c = c  a                 |
| //=  | 取整除赋值运算符 | c //= a 等效于 c = c // a             |

| 运算符 | 逻辑表达式 | 描述                                                         |
| ------ | ---------- | ------------------------------------------------------------ |
| and    | x and y    | 布尔"与" - 如果 x 为 False，x and y 返回 False，否则它返回 y 的计算值 |
| or     | x or y     | 布尔"或" - 如果 x 是非 0，它返回 x 的计算值，否则它返回 y 的计算值。 |
| not    | not x      | 布尔"非" - 如果 x 为 True，返回 False 。如果 x 为 False，它返回 True。 |

| 运算符 | 描述                                                    | 实例                                            |
| ------ | ------------------------------------------------------- | ----------------------------------------------- |
| in     | 如果在指定的序列中找到值返回 True，否则返回 False。     | x 在 y 序列中 , 如果 x 在 y 序列中返回 True。   |
| not in | 如果在指定的序列中没有找到值返回 True，否则返回 False。 | x 不在 y 序列中 , 如果 x 不在 y 序列中返回 True |

| 运算符优先级                           | 描述                                                   |
| -------------------------------------- | ------------------------------------------------------ |
| **                                     | 指数 (最高优先级)                                      |
| ~ 、+、 -                              | 按位翻转, 一元加号和减号 (最后两个的方法名为 +@ 和 -@) |
| * 、/、 %、 //                         | 乘，除，取模和取整除                                   |
| + 、-                                  | 加法减法                                               |
| >> 、<<                                | 右移，左移运算符                                       |
| &                                      | 位 'AND'                                               |
| ^、 \|                                 | 位运算符                                               |
| <=、 <、 >、 >=                        | 比较运算符                                             |
| ==、 !=                                | 等于运算符                                             |
| = 、%=、 /=、 //=、 -=、 +=、 *=、 **= | 赋值运算符                                             |
| is、 is not                            | 身份运算符                                             |
| in 、not in                            | 成员运算符                                             |
| not、 and、 or                         | 逻辑运算符                                             |

## 数据类型

### 字符串

```python
#创建一个字串符
a='a'
#以切的方式截取成员，切片区间是左闭右开
text[1:3]

#大小写转换
s.upper()                               #全部大写
s.lower()                               #全部小写
s.swapcase()                            #大小写互换
s.capitalize()                          #字符串的首字母大写,其余小写
s.title()                               #每個詞的首字母大写

#填充
s.ljust(12,'0')      #获取固定长度的字符串,左对齐,右边不够用空格补齐
s.rjust(width [, fillchar])      #获取固定长度,右对齐,左边不够用空格补齐
s.just(width [, fillchar])       #获取固定长度,中间对齐,两边不够用空格补齐
s.zjust(width [, fillchar])      #获取固定长度,原字符串右对齐，前面填充0
s.expandtabs([tabsize=8])        #把字符串中的 tab 符号('\t')转为空格，tab 符号('\t')默认的空格数是 8。

#查找
s.find(str, beg= 0,end=len(string))     #搜索指定字符串,找到返回位置索引，没有返回-1
s.rfind(str, beg= 0,end=len(string))    #返回字符串最后一次出现的位置(从右向左查询)，如果没有匹配项则返回-1
s.lfind(str, beg= 0,end=len(string))    #返回字符串最后一次出现的位置(从左向右查询)，如果没有匹配项则返回-1
s.index(str, beg= 0,end=len(string))    #跟find()方法一样，只不过如果str不在字符串中会报一个异常
s.count(str, beg= 0,end=len(string))    #统计指定的字符串出现的次数

#替换
s.replace(old, new [, max])             #把将字符串中的 old 替换成 new,如果 max 指定，则替换不超过 max 次。
s.translate(table, deletechars="")      #根据 str 给出的表(包含 256 个字符)转换 string 的字符, 要过滤掉的字符放到 deletechars 参数中

#删减
s.strip()                                  #去两边空格或指定字符
s.lstrip()                                 #截掉字符串左边的空格或指定字符
s.rstrip()                                 #去右边空格截掉字符串左边的空格或指定字符
s.split(str="", num=string.count(str))     #以 str 为分隔符截取字符串，如果 num 有指定值，则仅截取 num+1 个子字符串. 切位列表
s.splitlines([keepends])                   #按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数 keepends 为 False，不包含换行符，如果为 True，则保留换行符。

#布尔判断
s.startswith()                    #判斷是否以指定字符开头
text.endswith()                   #判斷是否以指定字符结尾
text.isalpha()                    #判斷是否是否全字母
text.islower()                    #判斷是否全小写
text.isupper()                    #判斷是否全大写
text.istitle()                    #判斷首字母是否为大写
text.isspace()                    #判斷字符是否全为空格

#连接
seperator = "-"                   #分隔符，可以為空:
sequence = ['what','a','good','day','！']    #要連結的元素: str, list, tuple, dict 都可以
print (seperator.join(sequence))  #返回一個以分隔符號sep連接多個元素的字符串
```

## 条件语句

```python
#if
#if - else
#if - elif - else
if x > 5:
    print('x is greater than 5')
elif x < 5:
    print('x is less than 5')
else:
    print('x equals 5')
    
# and/or 
if (x > 3) and (x < 10):
    print('x is between 3 and 10')
else:
    print('x is either less than or equal to 3 or greater than or equal to 10')

# try/except 如果代码可运行，则跳过except，反之亦然
xxx = '123'
try:
    yyy = int(xxx)
    print('try works')
except:
    yyy = -1
    print('except works')
print(yyy)

#while loop 条件循环
n = 5
while n > 0:
    print(n)
    n = n - 1
print('finished!')

#continue break
while True:
    ch = input('please enter anything: ')
    if ch == 'no print':
        continue                            #继续执行，指导输入正确才能跳出
    if ch == 'done':
        break                               #跳出循环
    print(ch)
print('Done!')

#for loop 依次输出目标数据中的内容
li = [1, 2, 5, 8]
for i in li:
    print(i)
    
#for zip 同时循环XY
for x,y in zip(X,Y)：
	
```



## 时间

```python
#时间
import datetime 
datetime.date.today() 
#datetime.date(2021, 12, 15)

datetime.date.today().day                      #输出日
datetime.date.today().month                    #输出月
datetime.date.today().year                     #输出年

datetime.date.isoformat(datetime.date.today())
#'2021-12-15'

time.strftime("%a:%H:%M")  #time.strftime()函数:返回以可读字符串表示的当地时间
#'Wed:11:06'

#多时间序列
pd.date_range('1/1/2000', periods=7)

#时间序列resample汇总
rng = pd.date_range('1/1/2012', periods=100, freq='S')
ts = pd.Series(np.random.randint(0, 500, len(rng)), index=rng)
s3=ts.resample('3s').sum()                      #三秒建立一个集

#加时区
ts_utc = ts.tz_localize('UTC')                 #设置为UTC时间
ts_utc.tz_convert('US/Eastern')                #转变为US/Eastern

#建立月数据
rng = pd.date_range('1/1/2012', periods=5, freq='M')
ps = ts.to_period()                            #只保留月份
ps.to_timestamp()                              #设置为每月第一天

#建立季度数据
prng = pd.period_range('1990Q1', '2000Q4', freq='Q')

#添加时间数据 由年季度--年月日时（季度）
ts.index = (prng.asfreq('M', 'e') + 1).asfreq('H', 's') + 9
```

## 列表

```python
#创建列表
s1=[]                                          #創建了一個空列表
s2=[32.0,212.0,0.0,81.8,100.0,45.3]            #創建了一個浮點數列表
s3=['toyota','rav4',2.2,]                      #創建了一個含不同類型數據的列表
list_of_list=[temps, car_details]              #創建了一個所含對象為列表的列表       
list('asda')                                   #字符串转成list

#元素
len(list) #列表元素个数
max(list) #返回列表元素最大值
min(list) #返回列表元素最小值
list(seq) #将元组转换为列表
list.count(obj) #统计某个元素在列表中出现的次数

#编辑列表
found.append('a')                              #添加单个
nums.remove(2)                                 #移除第二个
nums.pop(2)								       #移除倒数第二个
nums.extend([3,4])                             #添加多个
nums.insert(2,'hello')                         #在第二个位置插入
nums.reverse()                                 #顺序反转
third=first.copy()                             #复制
letter[start:end:step]                         #列表切片
list.clear()                                   #清空列表
list.sort( key=None, reverse=False)            #对原列表进行排序
```

| 列表运算表达式                        | 结果                         | 描述                 |
| ------------------------------------- | ---------------------------- | -------------------- |
| len([1, 2, 3])                        | 3                            | 长度                 |
| [1, 2, 3] + [4, 5, 6]                 | [1, 2, 3, 4, 5, 6]           | 组合                 |
| ['Hi!'] * 4                           | ['Hi!', 'Hi!', 'Hi!', 'Hi!'] | 重复                 |
| 3 in [1, 2, 3]                        | True                         | 元素是否存在于列表中 |
| for x in [1, 2, 3]: print(x, end=" ") | 1 2 3                        | 迭代                 |

## 元组

不可修改性

```python
#创建元组
vowels2=('a','e','i','o','u')                  #建立元组
T = tuple([1,2,3,4])                           #list转成tuple
tuple('spam')                                  #字符串转成tuple

#元组查找
list/tuple.index(x, start, end) 
T = (1, 3, 2, 4, 2, 5, 2)
T.index(4), T.index(2,3), T.count(2), T.index(2, T.count(2))
#(3, 4, 3, 4)
```

## 集合

```python
#创建集合
vowels={"a",'e','e','i','o','u','u'}            #建立集合
set([1,2,3,4,5,2,3])  					      #list转set
vowels2=set("aeeiou")					      #字符串转set

#增加删除元素
set.add(obj)
set.update(obj)                                 #添加元素，且参数可以是列表，元组，字典等
set.remove(item)                                #移除指定元素
set.remove( obj )                               #如果元素不存在，则会发生错误
set.discard( obj )
set.pop()                                       #随机删除集合中的一个元素

#并集
u=v1.union(set(v2))
set.symmetric_difference(set)                   #返回两个集合中不重复的元素集合

#差集
d=v1.difference(set(v2))
set.symmetric_difference_update(set)            #移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中。

#交集
i=v1.intersection(set(v2))
set.intersection(set1, set2 ... etc)           #返回多个集合的交集，返回一个新的集合
set.intersection_update(set1, set2 ... etc)    #返回多个集合的交集，移除不重叠的元素

#布尔判别
set.issubset(set)                             #判断指定集合是否为该方法参数集合的子集
set.issuperset(set)                           #判断该方法的参数集合是否为指定集合的子集,倒过来
set.isdisjoint(set)                           #判断两个集合是否包含相同的元素
```

## 字典

```python
#建立字典
Dict1={}                                         #建立空词典
Dict2={'name':'Allen','age':21,'gender':'male'}  #建立词典
Dict3['gender']='male'                           #赋值法/增加新值
dict(name='Allen', age=21, gender='male')        #dict内建函数
dict([('name','Allen'),('age',21),('gender','male')])       #键值对列表（k，v）

#属性
person3['Name']								  #获取对应值
person3.keys()                                   #获取键
person3.values()                                 #获取对应键
person3.items()                                  #获取对应键值对

#编辑
del person3['age']                               #删除
D.pop("ham")                                     #删除
D.update(D2)                                     #将新值更新到旧字典中

#元素查找
dict.get(key, default=None)                      #返回指定键的值，如果值不在字典中返回default值
dict.has_key(key)                                #如果键在字典dict里返回true，否则返回false

#检查成员关系
vowels=['a','e','i','o','u']
word=input("Provide a word to search for vowels:")
found={}
for letter in word:
    if letter in vowels:
        found.setdefault(letter,0)               #初始化
        found[letter] +=1
print(found)

#遍历取值
for k, v in sorted(found.items()):               #前一个取Keys；后一个取Values
    print(k, 'was found', v, 'time(s).')

#合并数据集
import pprint                                    # 优化数据结构的形式
pprint.pprint(people)

#读取数据
people['003']                                    #单层
people['003']['gender']                          #多层
```

## 函数定义

```python
#无参数函数，需要输入
def search4vowels():                            
    vowels=set('aeiou')
    word=input('Provide a word to search for vowels:')
    found=vowels.intersection(set(word))
    for vowel in found:
        print(vowel)
        
#参数函数
def search4vowels(word):
    vowels=set('aeiou')
    found=vowels.intersection(set(word))
    for vowel in found:
        print(vowel)
        
#多参数函数
def F1 ( x, y ):                                #計算並返回x 除以 y 的余数与商的函数
    a = x % y
    b = (x-a) / y
    return  (a,b)                               # 也可以写作 return a, b
(c,d) = F1(9, 4)                                # 也可以写作 c ,d = F1 ( 9, 4 )
print (c,d)

#进阶函数
def search4letters(phrase:str, letters:str)->set:   
   return set(phrase).intersection(set(letters))

#可变参数
def sum_my(*n):                                 #输入时由([1, 2, 3])简化为(1, 2, 3)
    d = 0
    for n in n:
        d = d + n 
    return d

#函数默认
def number(a, b=0, *c, **d):                    #a必须定义，b默认为0，c可多定义，d为小字典，可额外补充。
    
#Global Variables & Local Variables
#--local variables are inside the function
#--global variables are in the main program
```

## 文件读写

```python
#写入文件
todos=open('todos.txt','w')                     #清空原来的文件，写一个新文件
todos.writelines(["put out the trash.","Feed the cat.", "Prepare tax return."]) #写入数据, 不會自動增加换行符（\n）。
todos.close()  


#读取文件
#read
tasks=open('todos.txt')                         #打开一个文件，返回文件对象tasks
tasks_content=tasks.read()
print(type(tasks_content))
print(tasks_content)
tasks.close()
#readline
tasks=open('todos.txt')     
tasks_line=tasks.readline()
print(type(tasks_line))
print(tasks_line)
tasks.close()
#readlines
tasks=open('todos2.txt')     
tasks_lines=tasks.readlines()
print(tasks_lines)
tasks.close()
#一站式读取
with open('todos.txt') as tasks:
    tasks_content=tasks.read()
    print(tasks_content)
    
#多文件对比是否一直 输出True/False
import filecmp
r = filecmp.cmp('lecture3-cmp1.txt', 'lecture3-cmp2.txt')
print(r)
```

## CSV文件读写

```python
#路径设置
import os 
#os库是Python标准库，提供通用的、基本的操作系统交互功能，包含几百个函数，常用的有路径操作、进程管理、环境参数等。
os.getcwd() 
os.chdir("") 

#导出数据
df.to_csv('foo.csv')                  #将df导入到foo.csv为csv格式
df.to_hdf('foo.h5','df')              #将df导入foo.h5为hdf格式
df.to_excel('foo.xlsx', sheet_name='Sheet1')      #将df导入foo.xlsx为xlsx格式 


#读取CSV文件 
#pd.read_csv(filepath_or_buffer, sep=',',header='infer',names=None,index_col=None, encoding=None，skiprows=[0, 2, 3]，nrows=5)
data = pd.read_csv("7.1.csv")
data = pd.read_table('ex1.csv', sep=',') 
!type ex2.csv

#读取Excel文件  
#pd.read_excel(io, sheetname=0, header=0, index_col=None, names=None)
data = pd.read_excel("ex1.xlsx",sheet_name = 0)

#读取JSON
data = pd.read_json('example.json')

#写入数据
data.to_csv('out.csv'，sep='|'， index=False, header=False，columns=['a', 'b', 'c'])#默认分割逗号，是否田添加行列，自行添加列标
```

## NumPy

```python
#建立array
arr = np.array([0, 1, 2, 3, 4, 5, 6, 7])

#特殊数组
np.zeros((2,5))                #零数组
np.ones((6,7))                 #1数组
np.empty((3,3))                #空数组
np.arange(1,100,5)             #序列数组
np.linspace(1,100,5)           #等差序列数组
np.full((3,4), 1.0)            #size为（3，4）全为1.0的数

#等差数量
np.linspace(-1.4, 1.4, 30)     #（min，max，bin）

#正态分布
x = np.
random.randn(8)
#array([-1.10095156, -0.68793958, -0.44880688,  0.15520171,  0.85216375,-0.55215269, -0.90874604,  0.98619793])

#生成8个0，1的数
x = np.random.rand(8)
#array([0.63663356, 0.74770339, 0.94942448, 0.25861892, 0.13224901,0.34169378, 0.19222976, 0.57935704])

#生成一个随机数
x = np.random.randint(8)
#5

#生成array，限制区间
x = np.random.randint(low=0,high=10,size=(2,2))
#array([[8, 0],[4, 9]])

#choice  随机选择一个数
a = ['a','b']
choice(a)


#取两个array中大的数
np.maximum(x, y)
#array([0.73945297, 0.99010878, 0.10009918, 0.84977493, 0.43784594,0.04473167, 1.056885  , 0.85558624])

#分离数的整数和小数部分
remainder, whole_part = np.modf(arr)
remainder
#array([ 0.32326675, -0.77144607, -0.15537755, -0.70869285,  0.9733596 ,-0.64643437, -0.50897606])
whole_part
#array([ 6., -1., -4., -2.,  6., -4., -7])

#累加
arr.cumsum(axis=0)                               # 沿着列方向累加

#累乘
arr.cumprod(axis=1)                              # 沿着行方向累乘

#排序
arr.sort(axis=)
df1.sort_values(by="Name")

#set
arr.unique()

#测试values里的数值是否在[2,3,6]内
np.in1d(values, [2, 3, 6])

#多维数据变为一维
g.ravel()

#a，b大小比较
np.greater(a, b)

#a,b取大值
np.maximum(a, b)

#数据结构转变
b.reshape(4,2,6)                                  #4组，2行，6列
t.transpose((1,2,0))                              # (depth→width, height→depth, width→height)
```

### Array矩阵运算

```python
#矩阵点乘
a*b 

#矩阵点积
np.vdot(a,b)

#逆矩阵
b = np.linalg.inv(a)

#矩阵乘法
np.dot(a,b)

#矩阵标量
np.linalg.det(a)

#矩阵求解方程
np.linalg.solve(A,B)

#矩阵二维分解
q, r = linalg.qr(m3)
```

## Pandas

### Series

```python
#输入列index和元素values
s2=Series([5,'Research Methodology','Python'],index=['coursecode', 'course name', 'software'])

#判断缺失值
s3.isnull()
s3.notnull()

#布尔
s3.isnull().any()
s3.isnull().all()
s3.isnull().sum()

#元素查看
s5.index
s5.values
s5.detype
s5.size
s5.items
s[True,True,False]

#索引
s['a']
s['a'：'c']
s[['a','c']]
s[[True,True,False]]
a = np.array([1, 5, 3, 19, 13, 7, 3])
a[2::2]                                   #从第2个开始依次2跳跃
a[::-1]                                   #从后往前

#loc
s.loc['a']
s.loc['a'：'c']
s.loc[['a','c']]
s.loc[[True,True,False]]

#iloc
s.iloc[0] 
s.iloc[0:2]
s.iloc[(0,2)] 
s.iloc[[True,True,False]]

#布尔索引
s[s <= 10]                                # 选取所有 value 小于 10 的 s
s[s.between(10, 20)]                      # 选取所有 value 大于等于 10，小于 等于20 的 s
s[s.isin([10, 30])]                       # 选取所有 value 等于 10 或 30 的 s
#等效的三种表达方法
s.iloc[(s>10).values]
s.loc[(s.values>10)]
s.loc[(s>10).values]
#查看空缺行
df1[df1['score'].isnull()== True]

#替换
s1.replace(-999, np.nan)                  #单对象替换
s1.replace([-999, -1000], np.nan)         #多对象替换
s0.replace(to_replace=[12,23], value=[10, 20], inplace=False)        #多对象指定替换
s1.replace({-999: np.nan, -1000: 0})

#删除
del s0['d']
#df6.drop(index=df6.loc['D':'f'].index,columns=None, axis=0, inplace=True)
s0.drop(['d', 'c'])

#排序
s7.sort_index()
```

### DataFrame

```python
#建立DataFrame
d = np.random.rand(5,3)                               #2D ndarray     
indexd = ['2001', '2002', '2003', '2004', '2005']
columnd = ['CN', 'US', 'UK']
df0 = pd.DataFrame(d, index=indexd, columns=columnd)

a = [[1,np.nan,2],[NA,4,None]]                        #array法
data = pd.DataFrame(a)

#新行列增加
funddata['rank'] = funddata[c]*100
funddata[c+' rank'] = funddata[c].rank(ascending = False)

#查看属性
df0.index
df0.columns
df0.shape
df0.size

#文件合并
df1+df2
pd.concat([df4, df4_2], axis=0)                       #axis： 需要合并链接的轴，0是行，1是列
#Series与DataFrame相加
df4+df4.iloc[0]

#文件相减
#DataFrame.sub(other, axis='columns', level=None, fill_value=None) 获取DataFrame和其他元素的减法
df4.sub(df4.iloc[:,0],axis=0)

#Dataframe读取
pd.options.display.max_rows = 10

#行列重新命名
df4.rename(index=str.title, columns=str.upper)

#数据标签
df = pd.DataFrame({"id":[1,2,3,4,5,6], "raw_grade":['a', 'b', 'b', 'a', 'a', 'e']})  #源文件
df['grade'] = df['raw_grade'].astype("category")      #转类型为分类
df["grade"].cat.categories = ["very good", "good", "very bad"]       #添加分类（一一对应）
df["grade"] = df["grade"].cat.set_categories(["very bad", "bad", "medium", "good", "very good"])                                         #当出现一对多时，则按照自身性质顺序对应
df.groupby("grade").size()                            #对每一类进行统计

data1['alpha'].idxmax()          #最大值的位置
data1.loc[data1['alpha'].idxmax()]     #最大值所在位置的行
```

## 数据处理

```python
#缺失值处理
#查看缺失值
df1[df1['score'].isnull()== True]                    #某列有
data[data.isnull().values== True]                    #但凡有

#Series的缺失值过滤
s[s.notnull()]
s.dropna() 
df1.dropna(axis=1)
df1.dropna(inplace=True) 
df2.dropna(how="all")                                #当整一行都是na时删除

#过滤特定列的缺失值
housing.dropna(subset=["total_bedrooms"])

#保留NA
df2.dropna(thresh=2)                                 #传入thresh=n保留至少有n个非NaN数据的行

#把部分值转成缺失值
result = pd.read_csv('ex5.csv', na_values=['one'])
df.replace(0,np.nan)

#把缺失值赋值
df3.fillna(0)  
df3.fillna({1: 0.5, 2: 0.2})                         #不同的列使用不同的缺失值
df4.fillna(method='ffill')                           #前向填充，即使用上一行的值进行填充
df4.fillna(method='ffill',axis=1)                    #列进行填充；前向填充，即使用左边一列的值进行填充
df4.fillna(method='ffill', limit=2)                  #limit : int, 默认值 None； 指定连续的前向/后向填充的最大数量。
df4.fillna(method="bfill")                           #后向填充，使用下一行的值,不存在的时候就不填充
df5.fillna(df5.mean())                               #平均值填补
df5.fillna(df5.median(axis=1))                       #中位数（行中位数）填补

#检测重复值
df1.duplicated()

#删除重复值
df1.drop_duplicates(['k1']) 
df1.drop_duplicates(['k1', 'k2'], keep='last')        #保留最后一个值

#数据映射map
#map()函数会对一个序列对象中的每一个元素应用被传入的函数，并且返回一个包含了所有函数调用结果的一个列表。
df2['animal'] = lowercasedF.map(meat_to_animal)       #LowercasedF为映射的x，meat_to_animal为映射标准;df2为目标映射区

#匿名函数
a = map(lambda x: x ** 2, [1, 2, 3, 4, 5, 6, 7, 8, 9])
df2['food'].map(lambda x: meat_to_animal[x.lower()])  #返回字典data中food列作為meat_to_anmiaml字典中的鍵值所被映射到的value.

#离散&箱化
ages = [20, 22, 25, 27, 21, 23, 37, 31, 61, 45, 41, 32]
bins = [18, 25, 35, 60, 100]                          #通过给定端点，定义分组的区间
cats = pd.cut(ages, bins)
pd.cut(ages, [18, 26, 36, 61, 100], right=False)
group_names = ['Youth', 'YoungAdult', 'MiddleAged', 'Senior']
pd.cut(ages, bins, labels=group_names)
pd.cut(data, 4, precision=2)

#属性
cats.categories                                       #輸出category的label
cats.codes                                            #輸出数据归于第幾個category
pd.value_counts(cats)                                 #輸出每一類別的頻數分佈表

#检测过滤异常值
df6.describe()
col = df6[2]#标准差
df6[np.abs(col) > 3]     
df6[(np.abs(df6) > 3).any(1)]
funddata[(funddata['growth_overall_income_growth_ratio rank'] < int(len(indexstock))*0.3) & (funddata['growth_np_atsopc_dnrgal_yoy rank'] < int(len(indexstock))*0.3)]                             #过滤体哦阿健

#随机抽样
sample1 = np.random.permutation(5) 
df7.take(sample1,axis=0)

#抽样个数
df7.sample(n=3)

#字符串分割
val.split(',')
pieces = [x.strip() for x in val.split(',')]          #先分割再移除字符串头尾的空格

#字符串合并
'，'.join(pieces)

#np array合并
np.vstack((q1, q2, q3))                               #纵向合并
np.hstack((q1, q3))                                   #横向合并
np.concatenate((q1, q2, q3), axis=0)                  #调整axis实现合并
merge(left,right)
np.stack((q1, q3))                                    #创建新的axis

#np array拆分
np.vsplit(r, 3)                                       #横向拆分(目标数据，分成几组)
np.hsplit(r, 2)                                       #纵向拆分(目标数据，分成几组)

#字符串查找                      
print('a' in info)                                    #返回True False
print(info.find('a'))                                 #返回位置，若没有返回-1
print(info.index('a'))                                #返回位置，若没有报错
print(info.rfind('a'))                                #从末尾开始找，同上
print(info.rfind('a'))                                #从末尾开始找，同上  

#字符串统计
info.count('a')

#字符串替换
#replace()： 把字符串中的 old（旧字符串） 替换成 new(新字符串)，如果指定第三个参数max，则替换不超过 max 次。
str.replace("is", "was", 2)

#双中括号得出为dataframe不是series
housing_ocean_proximity = housing[["ocean_proximity"]] # one bracket vs two brackets
```


## JSON DATA

```python
#解码
result = json.loads(obj)   

#编译
asjson = json.dumps(result)

#输出
data.to_json()
data.to_json(orient='records')                       #输出的数据结构是 列:变量名->值 的形式

#写文件
with open("outputjson.json","w") as f:
    json.dump(data.to_json(), f)                     #将数据转换成json 格式，再使用 json.dump() 输出文件
!type outputjson.json

# 读文件
with open('outputjson.json', 'r') as f:
    data = json.load(f)                              #使用json.load() 读取JSON数据
print(data)
type(data)
```

## 虚拟变量

```python
#生成虚拟变量
pd.get_dummies(df8['Gender'])
pd.get_dummies(df8['Gender'], prefix='Gender')         #虚拟变量加前缀
df8_with_dummy = df8[['Age']].join(dummies)
```



## 正则表达式

| 正则表达式 | 匹配对象              | 正则表达式                              | 匹配对象                                       |
| ---------- | --------------------- | --------------------------------------- | ---------------------------------------------- |
| '\d'       | 数字                  | [0-9a-zA-Z_]                            | 匹配一个数字、字母或者下划线                   |
| '\w'       | 字母                  | [0-9a-zA-Z_]+                           | 匹配至少由一个数字、字母或者下划线组成的字符串 |
| '\s'       | 空格                  | A\|B                                    | 匹配A或B                                       |
| .          | 任意字符              | ^                                       | ^\d表示行必须以数字开头                        |
| *          | 任意个字符（包括0个） | $             | \d$表示行必须以数字结束 |                                                |
| +          | 至少一个字符          |                                         |                                                |
| ？         | 0个或1个字符          |                                         |                                                |
| {n}        | n个字符               |                                         |                                                |
| {n,m}      | n-m个字符             |                                         |                                                |

```python
import re

#用re.compile编译，节省CPU
regex = re.compile('\s+')
regex = re.compile(r'A\d+', flags=re.IGNORECASE)       #flag是匹配标志位，是否区分大小写，是否多行匹配
regex.split(text)
regex.findall(text)

#查找
re.search(pattern,str1)                                #扫描整个字符串并返回第一个成功的匹配
re.findall(pattern,str1)                               #返回string中所有与pattern相匹配的全部字串，返回形式为数组
re.finditer(pattern,str1)                              #返回string中所有与pattern相匹配的全部字串，返回形式为迭代器

#案例
text = """Dave dave@google.com 
          Steve steve@gmail.com 
          Rob rob@gmail.com 
          Ryan ryan@yahoo.com """
pattern = r'[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}'
regex = re.compile(pattern, flags=re.IGNORECASE)
m = regex.findall(text)
print(m)

```



## Matplotilb

- 颜色字符：'b' 蓝色，'m' 洋红色，'g' 绿色，'y' 黄色，'r' 红色，'k' 黑色，'w' 白色，'c' 青绿色，'#008000' RGB 颜色符串。多条曲线不指定颜色时，会自动选择不同颜色。
- 线型参数：'‐' 实线，'‐‐' 破折线，'‐.' 点划线，':' 虚线。
- 标记字符：'.' 点标记，',' 像素标记(极小点)，'o' 实心圈标记，'v' 倒三角标记，'^' 上三角标记，'>' 右三角标记，'<' 左三角标记...等等。

```python
import matplotlib.pyplot as plt

#创建画板
fig1 = plt.figure(1)                        #创建第一个画板
figure = plt.figure(figsize=(15,6))         #画板尺寸
ax = fig1.add_axes([0,0,1,1])               #在画板上添加一个轴域,即坐标系。0,0表示轴域的坐标点，1,1表示轴域的宽和高，这个是与画板的比例值，这里该轴域与画板一样大。
ax1 = fig1.add_subplot(2, 2, 1)             #figure是2x2（这样一共有4幅子图），而且我们选中4个subplots（数字从1到4）中的第2个。

#创建一个pyplot
xpoints = np.array([0, 6])
ypoints = np.array([0, 100])
plt.plot(xpoints, ypoints，'b')              #b蓝色# 创建 y 中数据与 x 中对应值的二维线图，使用默认样式
plt.show()                                   #plt.show() 默认是在新窗口打开一幅图像

#属性
plt.xlabel("x - label")                      #横坐标
plt.ylabel("y - label")                      #纵坐标
plt.axis([-1,5,-1,20])                       #坐标轴范围plt.axis([xmin, xmax, ymin, ymax])
plt.suptitle("RUNOOB subplot Test")          #子标题
plt.title("RUNOOB TEST TITLE")               #标题
plt.legend(['First series'])                 #图示
plt.grid(True)                               #网格线
plt.show()

#subplot
x = np.linspace(-1.4, 1.4, 30)
plt.subplot(2, 2, 1)  # 2 rows, 2 columns, 1st subplot = top left
plt.plot(x, x)
plt.subplot(2, 2, 2)  # 2 rows, 2 columns, 2nd subplot = top right
plt.plot(x, x**2)
plt.subplot(2, 2, 3)  # 2 rows, 2 columns, 3rd subplot = bottow left
plt.plot(x, x**3)
plt.subplot(2, 2, 4)  # 2 rows, 2 columns, 4th subplot = bottom right
plt.plot(x, x**4)
plt.show()

#subplot子图位置组合
plt.subplot(2, 2, 1)  # 2 rows, 2 columns, 1st subplot = top left
plt.plot(x, x)
plt.subplot(2, 2, 2)  # 2 rows, 2 columns, 2nd subplot = top right
plt.plot(x, x**2)
plt.subplot(2, 1, 2)  # 2 rows, *1* column, 2nd subplot = bottom
plt.plot(x, x**3)
plt.show()

#用subplot2grid来更复杂的确定图表位置（左上角开始为（0，0）
plt.subplot2grid((3,3), (0, 0), rowspan=2, colspan=2)
plt.plot(x, x**2)
plt.subplot2grid((3,3), (0, 2))
plt.plot(x, x**3)
plt.subplot2grid((3,3), (1, 2), rowspan=2)
plt.plot(x, x**4)
plt.subplot2grid((3,3), (2, 0), colspan=2)
plt.plot(x, x**5)
plt.show()
```

### xy轴设置

```python
axes.set_xticks([0,125,250])
axes.set_xticklabels(['2020-01-14','2020-06-11','2021-01-22'].fontsize=14)
```

### 密度图

```python
#密度图
a.plot(kind = 'density', subplots = True, layout=(2,4), sharex = False , figsize = (20,10), fontsize = 15)  #kind图片的类型；subplot=两行四列；sharex是自适应坐标轴函数默认False；figsize图片的大小；
```

### 直方图

- data:必选参数，绘图数据
- bins:直方图的长条形数目，可选项，默认为10
- normed:是否将得到的直方图向量归一化，可选项，默认为0，代表不归一化，显示频数。normed=1，表示归一化，显示频率。
- color:长条形的颜色
- edgecolor:长条形边框的颜色
- alpha:透明度

```python
matplotlib.pyplot.hist(x, bins=None, range=None, density=None, weights=None, cumulative=False, bottom=None, histtype='bar', align='mid', orientation='vertical', rwidth=None, log=False, color=None, label=None, stacked=False, normed=None, *, data=None, **kwargs)

#案例
data = np.random.randn(100)
plt.hist(data,bins=20,orientation='horizontal',color='black',alpha=0.3,)
```

### 散点图

- x：指定 X 轴数据。
- y：指定 Y 轴数据。
- s：指定散点的大小。
- c：指定散点的颜色。
- alpha：指定散点的透明度。
- linewidths：指定散点边框线的宽度。
- edgecolors：指定散点边框的颜色。
- marker：指定散点的图形样式。应参数支持'.'（点标记）、','（像素标记）、'o'（圆形标记）、'v'（向下三角形标记）、'^'（向上三角形标记）、'<'（向左三角形标记）、'>'（向右三角形标记）、'1'（向下三叉标记）、'2'（向上三叉标记）、'3'（向左三叉标记）、'4'（向右三叉标记）、's'（正方形标记）、'p'（五地形标记）、'*'（星形标记）、'h'（八边形标记）、'H'（另一种八边形标记）、'+'（加号标记）、'x'（x标记）、'D'（菱形标记）、'd'（尖菱形标记）、'|'（竖线标记）、'_'（横线标记）等值。
- map：指定散点的颜色映射，会使用不同的颜色来区分散点的值。

```python
matplotlib.pyplot.scatter(x, y, s=None'散点大小', c=None'颜色', marker=None, cmap=None, norm=None, vmin=None, vmax=None, alpha=None'透明度', linewidths=None,  verts=None, edgecolors=None, *, plotnonfinite=False, data=None, **kwargs)

#案例
x =[5, 7, 8, 7, 2, 17, 2, 9, 4, 11, 12, 9, 6]  
y =[99, 86, 87, 88, 100, 86, 103, 87, 94, 78, 77, 85, 86] 
plt.scatter(x, y, c ="blue") 
```


### 热力图

```python
import seaborn as sns

sns.heatmap(indexdf.pct_change().corr().annot = True)
```

[seaborn.heatmap-Seaborn 0.9 中文文档 (cntofu.com)](https://cntofu.com/book/172/docs/30.md)

### Polar环状图

```python
radius = 1
theta = np.linspace(0, 2*np.pi*radius, 1000)

plt.subplot(111, projection='polar')
plt.plot(theta, np.sin(5*theta), "g-")
plt.plot(theta, 0.5*np.cos(20*theta), "b-")
plt.show()
```

### 3D projection

```python
from mpl_toolkits.mplot3d import Axes3D

x = np.linspace(-5, 5, 50)
y = np.linspace(-5, 5, 50)
X, Y = np.meshgrid(x, y)
R = np.sqrt(X**2 + Y**2)
Z = np.sin(R)

figure = plt.figure(1, figsize = (12, 4))
subplot3d = plt.subplot(111, projection='3d')
surface = subplot3d.plot_surface(X, Y, Z, rstride=1, cstride=1,cmap=matplotlib.cm.coolwarm, linewidth=0.1)
plt.show()
```


```python
plt.contourf(X, Y, Z, cmap=matplotlib.cm.coolwarm)
plt.colorbar()
plt.show()
```

### 注释

axes.annotate(s, xy, *args, **kwargs)用于在图形上给数据添加文本注解，而且支持带箭头的划线工具，方便我们在合适的位置添加描述信息。

- s：注释文本的内容
- xy：被注释的坐标点，二维元组形如(x,y)
- xytext：注释文本的坐标点，也是二维元组，默认与xy相同

```python
ax.test()/plot.test(x, y, string, fontsize=15, verticalalignment="top", horizontalalignment="right")

#案例
#箭头
ax = plt.axes() 
ax.arrow(0, 0, 0.6, 0.7, head_width = 0.05, head_length = 0.1)
ax.set_title('matplotlib.axes.Axes.arrow() Example',fontsize = 14, fontweight ='bold')   
plt.show()

#文本注释
ax1.annotate('Starting', xy =(3.3, 1), xytext =(3, 1.8), arrowprops = dict(facecolor ='green', shrink = 1),   ) 

#照片存储
plt.savefig('figpath.png', dpi=400, bbox_inches='tight')
#dpi，控制每英寸长度上的分辨率
#bbox_inches, 能删除figure周围的空白部分

plt.text(x,y+0.01,'{}%'.format(round(y,2)), ha ='center',va='bottom',fontsize = 15)  #x,y是注释的坐标，为了防止遮挡，抬升0.01的位置，{}内为实际内容，ha为左右居中，va为上下居下，字体15号
```





### 全局变量

- matplotlib很多默认的设置是可以自己定义的，通过修改一些全局设定，比如图大小，subplot间隔，颜色，字体大小，网格样式等等。

- pyplot可以使用rc配置文件来自定义图形的各种默认属性，被称为rc参数。rc参数k可以动态修改，在修改后，绘图使用的参数就会发生改变。例如，想要设置全局的图大小为10 x 10，键入：

  plt.rc('figure', figsize=(10, 10))

  rc中的第一个参数是我们想要自定义的组件，比如'figure', 'axes', 'xtick', 'ytick', 'grid', 'legend'，或其他。然后添加一个关键字来设定新的参数。

- 一个比较方便的写法是把所有的设定写成一个dict：

  

  ```python
  font_options = {'family': 'monospace','weight': 'bold','size'  : 'small'}
  ```

  plt.rc('font', **font_options)

更详细的设定可以去看一下文档。



## 统计

```python
#线性回归模型拟合
import statsmodels.api as sm
import statsmodels.formula.api as smf

#拟合回归模型
results = smf.ols('Sales ~ Price + Advertising', data=df1).fit()       #使用statsmodels庫中 OLS对象的 fit() 方法来进行模型拟合
results.params                          #輸出计算出的回归系数
results.summary()                       #輸出回归拟合的統計摘要
df6.describe()

#计算预测值
x = df1[['Price', 'Advertising']]
y_pred = results.predict(x)
df1['sales_pred'] = y_pred
df1
#wls
from statsmodels.sandbox.regression.predstd import wls_prediction_std
prstd, iv_l, iv_u = wls_prediction_std(results)
df1['pred_STD'] = prstd
df1['pred_LowerLimit'] = iv_l
df1['pred_UpperLimit'] = iv_u
df1

#方差分析
import scipy.stats as stats             # 導入 python统计函数库scipy.stats
from statsmodels.formula.api import ols           # ANOVA table for one or more fitted linear models.
from statsmodels.stats.anova import anova_lm      # anova_lm用于一个或多个因素的方差分析,analysis of variance_linear models 

at1 = pd.read_csv("7.1.csv")
model = ols('y ~ C(Variety)',dat1).fit()          # 将Variety作为考察因素，使用最小二乘法OLS
anovat = anova_lm(model)                # 利用analysis of variance_linear models 解讀模型分析結果
print(anovat)
```

## 机器学习scikit-learn

scikit-learn是一个Python第三方提供的非常强力的机器学习库，它包含了从数据预处理到训练模型的各个方面。使用scikit-learn可以极大的节省我们编写代码的时间以及减少我们的代码量，使我们有更多的精力去分析数据分布，调整模型和修改超参。

scikit-learn 包含了很多监督式学习和非监督式学习的模型，可以实现分类，聚类，预测等任务。

这里用一个经典的kaggle（Kaggle是一个数据建模和数据分析竞赛平台。企业和研究者可在其上发布数据，统计学者和数据挖掘专家可在其上进行竞赛以产生最好的模型）比赛数据集来做例子，泰坦尼克生还者数据集。

对于这样的数据集，通常的任务是预测一个乘客最后是否生还。在训练集上训练模型，在测试集上验证效果。

```python
#加载训练集和测试集
train = pd.read_csv('train.csv')
test = pd.read_csv('test.csv')

#中位数填补缺失值
impute_value = train['Age'].median()
train['Age'] = train['Age'].fillna(impute_value)
test['Age'] = test['Age'].fillna(impute_value)
impute_value

#建立虚拟变量
train['IsFemale'] = (train['Sex'] == 'female').astype(int)
test['IsFemale'] = (test['Sex'] == 'female').astype(int)
train.head()

#确定X变量有哪些
predictors = ['Pclass', 'IsFemale', 'Age']    
predictors

#去除对应变量
X_test = test[predictors].values            #取出测试集里相应的X变量的数据
X_test[:5]                                  #试看下前五行的数据
y_train = train['Survived'].values          #取出训练集里相应的y变量的数据
y_train[:5]

#逻辑回归
from sklearn.linear_model import LogisticRegression

#fit拟合
model.fit(X_train, y_train)

#测试机预测
y_predict = model.predict(X_test)
y_predict[:10]

#测试集计算
y_true= pd.read_csv('test.csv')
y_true = y_true['Survived'].values
y_true
(y_true == y_predict).mean()

# 查看第一个和第一个训练样本生存的概率
model.predict_proba(X_train[:1])
```

实际过程中，训练模型的时候，经常用到交叉验证（cross-validation），用于调参，防止过度拟合。这样得到的预测效果会更好，穩健性更强。

交叉验证是把训练集分为几份，每一份上又取出一部分作为测试样本，这些被取出来的测试样本不被用于训练，但我们可以在这些测试样本上验证当前模型的准确率或均方误差（mean squared error），而且还可以在模型参数上进行网格搜索（grid search）。一些模型，比如逻辑回归，自带一个有交叉验证的类。LogisticRegressionCV类可以用于模型调参，使用的时候需要指定正则化项C，来控制网格搜索的密集程度：

```python
from sklearn.linear_model import LogisticRegressionCV

#交叉验证调参数
model_cv = LogisticRegressionCV(10)
model_cv.fit(X_train, y_train)

#交叉验证
#如果想要自己来做交叉验证的话，可以使用cross_val_score函数，可以用于数据切分。比如，把整个训练集分为4个不重叠的部分：
from sklearn.model_selection import cross_val_score
model = LogisticRegression(C=10)         #C为正则化系数λ的倒数，通常默认为1，smaller values specify stronger regularization.
scores = cross_val_score(model_cv, X_train, y_train, cv=4)
scores

#默认的评价指标每个模型是不一样的，但是可以自己指定评价函数。交差验证的训练时间较长，但通常能得到更好的模型效果。
```

## 分组

```python
#原文档
df = pd.DataFrame({'A' : ['foo', 'bar', 'foo', 'bar',
                          'foo', 'bar', 'foo', 'foo'],
                   'B' : ['one', 'one', 'two', 'three',
                           'two', 'two', 'one', 'three'],
                   'C' : np.random.randn(8),
                   'D' : np.random.randn(8)})
#以A为组分类
df.groupby('A').sum()

#所有数据以AB为组分类
df.groupby(['A', 'B']).sum()

#c以AB为组分类统计
df.groupby(['A', 'B'])['c'].count()

#分组统计后汇总为表格
df.groupby(['A', 'B'])['c'].count().reset_index()

#groupby行业排名
adf['ROE-RANK'] = adf.groupby('所属行业')['ROE'].rank(ascending = False)

#stack函数 类似转置
#原文档
tuples = list(zip(*[['bar', 'bar', 'baz', 'baz',
                     'foo', 'foo', 'qux', 'qux'],
                   ['one', 'two', 'one', 'two',
                    'one', 'two', 'one', 'two']]))
index = pd.MultiIndex.from_tuples(tuples, names=['first', 'second'])   #组合为复合索引
df = pd.DataFrame(np.random.randn(8, 2), index=index, columns=['A', 'B'])  #建立dataframe
stacked = df.stack()                     #序列转置
stacked.unstack()                        #恢复原有序列
stacked.unstack(1)                       #第二列index变为values
stacked.unstack(0)                       #第一列index变为values

#数据透视表
#原文档
df = pd.DataFrame({'A' : ['one', 'one', 'two', 'three'] * 3,
                   'B' : ['A', 'B', 'C'] * 4,
                   'C' : ['foo', 'foo', 'foo', 'bar', 'bar', 'bar'] * 2,
                   'D' : np.random.randn(12),
                   'E' : np.random.randn(12)})

#数据透视
df.pivot_table(values='D', index=['A', 'B'], columns='C')

df.pivot(columns='所属板块'，index='上市年份').fillna(0)
```

## 分类Class

```python
#建立属性元素
class Pet():
    def __init__(self, t, n, a, c, g):  # constructor
        self.type = t                   # 元素前均为self
        self.name = n
        self.age = a
        self.color = c
        self.gender = g
    
    def Greeting(self):
        print('hello, my name is '+self.name)
        
        if self.type == 'dog':
            print('woof woof')
        elif self.type == 'cat':
            print('meow meow')
            
p1 = Pet('dog', 'Lucky', 3, 'brown', 'male')
p1.Greeting()           
#输出
hello, my name is Lucky
woof woof

#属性编辑
getattr(p3, 'age')                      #输出元素对应值
hasattr(p3, 'name')                     #判断元素是否存在
delattr(p3, 'age')                      #删除元素
setattr(p3, 'age', 2)                   #修改对应元素值

print(p3.__dict__)                      #元素查看

#Data Structure: Stack
class Stack:
    def __init__(self):
        self.items=[]

    def is_empty(self):
        return self.items == []

    def push(self , item):
        self.items.append(item)

    def pop(self):
        return self.items.pop()

    def get_size(self):
        return len(self.items)

    def top(self):
        return self.items[-1]
    
    def get_stack(self):
        return self.items
#输入    
s1 = Stack()
s1.push(1)
s1.push(3)
s1.push(5)
print(s1.get_stack())
print(s1.top())
s1.pop()
print(s1.top())
print(s1.get_stack())
print(s1.is_empty())
print(s1.get_size())
#输出
[1, 3, 5]
5
3
[1, 3]
False
2

```

------

# **量化**

### 量化包

```python
import talib #技术指标包
```

### 同花顺数据接口

```python
from iFinDPy import*
THS_iFinDLogin('账号','密码')
```

### 成分股获取

```python
stock = get_industry_stocks(indexnum_sw1, date)
get_all_security('stock','2020-07-13')
```

### 绩效反馈

```python
#数据回测表现

def get_performance_analysis(T,year_day = 252):
    #输入净现值序列 
    #输出绩效指标
    
    #新高日期数
    max_T = 0
    #循环净值
    for s in range(2,len(T)):
        #节点划分
        l = T[:s]
        #判断当前节点为最大值
        if l[-1] > l[:-1].max():
        #新高日期+=1
        	max_T += 1
	
    #净值新高占比数
    max_day_rate = max_T/(len(T)-1)
    max_day_rate = round(max_day_rate*100,2)
    
    #获取最终净值
    net_values = round(T[-1],4)
    
    #计算算数年华收益率
    year_ret_mean = T.pct_change().dropna().mean()*year_day
    year_ret_mean = round(year_ret_mean*100, 2)
    
    #计算几何年化收益率
    year_ret_sqrt = net_values ** (year_day / len(T) - 1)
    year_ret_sqrt = round(year_ret_sqrt**100 , 2)
    
    #计算年化波动率
    vol = T.pct_change().dropna().std()*np.sqrt(year_day)
    vol = round(vol*100,2)
    
    #计算夏普，无风险收益率3%
    sharpe = (year_ret_mean - 3%)/vol
    sharpe = round(sharpe,2)
    
    #计算最大回撤
    downlow = maxdrawdown(T)
    downlow = round(downlow*100,2)
    
    #输出
    return[net_values,year_ret_sqrt,downlow,sharpe,vol,max_day_rate]

#最大回测
# 再次定义函数：计算最大回撤
def maxdrawdown(arr):
    '''
    输入：净值序列
    输出：最大回撤
    '''
    # 最大回撤结束点
    i = np.argmax((np.maximum.accumulate(arr) - arr)/np.maximum.accumulate(arr))
    # 开始点
    j = np.argmax(arr[:i]) # start of period
    # 输出回撤值
    return (1-arr[i]/arr[j])
    
```

### 指标打分

```python
#打分法
def get_pct(x):
    #获取当前值所处的百分位0-100分
    return round((x - x.min())/(x.max()-x.min())*100,2)
```

### 净值计算

```python
def get_net(stock,start,end):
    dailyret = get_price(stock,start,end,'1d',['quote_rate'],is_panel =1)['quote_rate'].mean(axis =1)/100+1
    dailynet = dailyret.cumprod()
    return dailynet

indexdf = indexdf / indexdf.iloc[0] 
```

### 标准化处理

```python
# 去极值+标准化
# MAD:中位数去极值
def filter_extreme_MAD(series,n): 
    median = series.quantile(0.5)
    new_median = ((series - median).abs()).quantile(0.50)
    max_range = median + n*new_median
    min_range = median - n*new_median
    return np.clip(series,min_range,max_range)
# 标准化
def standardize_series(series):
    std = series.std()
    mean = series.mean()
    return (series-mean)/std
```

### 财务指标

```python
#### 获取历年财务报告的重要财务指标
finace_datadf = pd.DataFrame()
for d in ['2015','2016','2017','2018','2019']:
    '''
    四大维度,18项指标
     '''
    q = query(asharevalue.symbol, # 股票
              asharevalue.date, # 时间
              
              # 盈利能力
              ashareprofit.roe_ttm, #ROE
              ashareprofit.roa_ttm, #ROA
              ashareprofit.net_sales_rate_ttm, #销售净利率
              ashareprofit.operating_profit_rate_ttm, #营业利润率TTM
              ashareprofit.cost_to_revenue_ttm, #营业总成本/营业总收入
              
              #运营能力
              ashareoperate.total_capital_turnover_ttm,#总资产周转率TTM
              ashareoperate.float_asset_turnover_ttm,#流动资产周转率TTM
              ashareoperate.inventory_turnover_ttm, #存货周转率TTM
              ashareoperate.account_receive_turnover_ttm,#应收账款周转率TTM
              
              # 偿还能力
              asharedebt.quick_ratio_mrq,#速动比率MRQ
              asharedebt.equity_ratio_mrq,#产权比率MRQ
              asharedebt.current_ratio_mrq,#流动比率MRQ
              
              # 成长能力
              growth.basic_eps_year_growth_ratio,#基本每股收益(增长率)
              growth.np_atsopc_dnrgal_yoy,#归属母公司股东的净利润-扣除非经常损益(增长率)
              growth.opt_income_growth_ratio,#营业收入(增长率)
              growth.ncf_of_oa_yoy,#经营活动产生的现金流量净额(增长率)
              growth.diluted_net_asset_growth_ratio,#净资产收益率(摊薄)(增长率)
              
              ).filter(valuation.symbol.in_(stock))
    df = get_fundamentals(q, statDate = d)
    finace_datadf = pd.concat([finace_datadf,df],axis =0)
finace_datadf
```

### 信息添加

```python
# 根据股票代码，使用apply函数求各个字段
finacedf['股票名称'] = finacedf['股票代码'].apply(lambda x : get_security_info(x).display_name)
finacedf['上市时间'] = finacedf['股票代码'].apply(lambda x : get_security_info(x).start_date)
finacedf['所属板块'] = finacedf['股票代码'].apply(lambda x : get_stockindex(x))
finacedf['是否ST'] = finacedf['股票名称'].apply(lambda x : True if 'ST' in x else False)
finacedf['上市年份'] = finacedf['上市时间'].apply(lambda x : x.strftime('%Y'))
finacedf['所属申万3级行业'] = finacedf['股票代码'].apply(lambda x : inddict[get_symbol_industry(x,date).s_industryid3])

#根据股票代码，获取股票所属版块
def get_stockindex(x):
    if x[:3]=='688':
        return '科创版'
    elif x[0]=='3':
        return '创业板'
    elif x[-2:]=='SH':
        return '上证'
    elif x[-2:]=='SZ':
        return '深证'
```

### 统计学检验

```python
#正态分布
stats.kstest(data1,'norm')

#皮尔森相关系数检验
stats.pearsonr(data1,data2)

#T检验：检验两个独立样本的均值是否有差异
stats.ttest_ind(data1,data2)

#方差齐性检验：检验两组或多组数据与其均值偏离程度是否存在差异，是很多检验和算法的先决条件
stats.levene(data1,data2)

#单因素方差分析：检验有单一因素影响的多组样本因某变量的均值是否有显著差异
stats.f_oneway(data1,data2)

#卡方检验：检验两个变量之间是否有关系，返回第一个值的统计量值，第二个为P-value值，即相关性不显著。第三个是自由度，第四个结果的数组是列联表的期望值分布
stats.chi2_contingency(price['000001.SZ'].price['601398.SH'])

#线性回归
#x , y 两组数据
X = sm.add_constant(x)
model = sm.OLS(y,X)
results = model.fit()
results.summary()
# β = str(results.params[1])

```


