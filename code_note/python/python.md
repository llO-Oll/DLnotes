# 多线程

多线程类似于同时执行多个不同程序，多线程运行有如下优点：

> - 使用线程可以把占据长时间的程序中的任务放到后台去处理。
> - 用户界面可以更加吸引人，这样比如用户点击了一个按钮去触发某些事件的处理，可以弹出一个进度条来显示处理的进度
> - 程序的运行速度可能加快
> - 在一些等待的任务实现上如用户输入、文件读写和网络收发数据等，线程就比较有用了。在这种情况下我们可以释放一些珍贵的资源如内存占用等等。

# with

文件管理器

# lambda函数

匿名函数lambda

是指一类无需定义标识符（函数名）的函数或子程序。

```python
lambda [arg1 [,arg2,...argn]]:expression
```

1. ```python
   def sum(x,y):
       
   sum = lambda x,y : x+y
   print(sum(1,2))
   ```

```python
sum = lambda x,y : x+y
print(sum(1,2))
```

# `if __name__ == '__main__':`

当我们把模块A中的代码在模块B中进行import A时，只要B模块代码运行到该import语句，模块A的代码会被执行。

```python3
# 模块A

a = 100

print('你好，我是模块A……')

print(a)
```

```python3
# 模块B

from package01 import A

b = 200

print('你好，我是模块B……')

print(b)
```

```python3
你好，我是模块A……
100
你好，我是模块B……
200
```

```python3
# 模块A

a = 100

print('你好，我是模块A……')

if __name__=='__main__':

    print(a)
```

```python3
你好，我是模块A……
你好，我是模块B……
200
```

# assert

```
assert expression
```

等价于

```
if not expression:
    raise AssertionError
```

后面可以加参数

```
assert expression [, arguments]
```

```
if not expression:
    raise AssertionError(arguments)
```

# 正则化

```
^once
```

只匹配那些以 **once** 开头的字符串。

```
bucket$
```

匹配以bucket结尾的字符串。

```
^bucket$
```

只匹配字符串`bucket`。

```
[a-z] // 匹配所有的小写字母 
[A-Z] // 匹配所有的大写字母 
[a-zA-Z] // 匹配所有的字母 
[0-9] // 匹配所有的数字 
[0-9\.\-] // 匹配所有的数字，句号和减号 
[ \f\r\t\n] // 匹配所有的白字符
```

只能表示一个字符。

前面曾经提到`^`表示字符串的开头，但它还有另外一个含义。当在一组方括号里使用 `^`时，它表示"**非**"或"**排除**"的意思，常常用来剔除某个字符。还用前面的例子，我们要求第一个字符不能是数字：

```
^[^0-9][0-9]$
```

这个模式与 "&5"、"g7"及"-2" 是匹配的，但与 "12"、"66" 是不匹配的。下面是几个排除特定字符的例子：

```
[^a-z] //除了小写字母以外的所有字符 
[^\\\/\^] //除了(\)(/)(^)之外的所有字符 
[^\"\'] //除了双引号(")和单引号(')之外的所有字符
```

特殊字符 `.`(点，句号)在正则表达式中用来表示除了"新行"之外的所有字符。所以模式`^.5$` 与任何两个字符的、以数字5结尾和以其他非"新行"字符开头的字符串匹配。模式 `.`可以匹配任何字符串，**换行符（\n、\r）除外**。

跟在字符或字符簇后面的花括号`{}`用来确定前面的内容的重复出现的次数。

| `^[a-zA-Z_]$`      | 所有的字母和下划线                |
| ------------------ | ------------------------ |
| `^[[:alpha:]]{3}$` | 所有的3个字母的单词               |
| `^a$`              | 字母a                      |
| `^a{4}$`           | aaaa                     |
| `^a{2,4}$`         | aa,aaa或aaaa              |
| `^a{1,3}$`         | a,aa或aaa                 |
| `^a{2,}$`          | 包含多于两个a的字符串              |
| `^a{2,}`           | 如：aardvark和aaab，但apple不行 |
| `a{2,}`            | 如：baad和aaa，但Nantucket不行  |
| `\t{2}`            | 两个制表符                    |
| `.{2}`             | 所有的两个字符                  |

特殊字符 ? 与 {0,1} 是相等的，它们都代表着： **0个或1个前面的内容** 或 **前面的内容是可选的** 。

## 匹配所有汉字

```text
[\u4e00-\u9fa5]
```

## 前瞻，后顾，负前瞻，负后顾

```
// 前瞻：
exp1(?=exp2) exp1后边是exp2就匹配
// 后顾：
(?<=exp2)exp1 exp1前边是exp2就匹配
// 负前瞻：
exp1(?!exp2) exp1后边不是exp2就匹配
// 负后顾：
(?<!exp2)exp1 exp1前边不是exp2就匹配
```



```python
^ 匹配字符串开头
$ 匹配末尾
. 匹配任意字符, 除了换行
[...] 表示一组字符, 单独列出: [amk]匹配 'a', 'm', 'k'
[^...] 不在[]中的字符, [^abc], 匹配除了'a', 'b', 'c'
* 匹配>=0个表达式
+ 匹配>=1个表达式
? 匹配前面的字符0次或1次
{n} 精确匹配n个前面表达式 如o{2}能匹配"food"中的两个o
{n,} 如o{2,} 能匹配fooood中所有的o
{n,m} 匹配n到m前面的正则片段, 贪婪
a|b 匹配a或b
() 匹配括号内的表达式

# \w 匹配字母数字下划线
# \W 匹配非字母数字及下划线
# \s 匹配任意字符空白
# \S 匹配任意非空白字符
# \d 匹配任意数字, 定价于[0-9]
# \D 匹配任意非数字
# \A 匹配字符串开始
# \Z 匹配字符串结束,
# \z 匹配结束


```

## re正则匹配

```python
## re.compile 编译正则模式
## re.match    从头匹配, group获取

## re.search    包含匹配, 

## re.findall    多个匹配    

## re.sub        匹配并替换
## re.split    以匹配的字符, 当做列表分隔符 
```

### 匹配邮箱地址

```python
email_pattern = re.compile(r'^[a-zA-Z0-9_-]+(\.[a-zA-Z0-9_-]+){0,4}@[a-zA-Z0-9_-]+(\.[a-zA-Z0-9_-]+){0,4}$')
a = re.match(email_pattern, 'django@pyghon.org')
print(a) 
# <_sre.SRE_Match object; span=(0, 17), match='django@pyghon.org'>

```



### 提取数字

```python
# '\d{4}'代表一个正整数重复4次，即四位整数
year_pattern = re.compile(r'\d{4}$') # 四位整数，匹配年份
string1 = '我在1998和1999年'
match1 = re.match(year_pattern, string1)
print(match1) # None

match2 = re.search("\d{4}", string1)
print(match2) # <_sre.SRE_Match object; span=(2, 6), match='1998'>
print(match2.group())  # 1998
```





### 利用findall提取多组匹配字符串

```python
# 例1 提取年份
year_pattern = re.compile(r"\d{4}")
string1 = "ahgk1314asg0999fa2222l"
a  = year_pattern.findall(string1)
print(a)
year_pattern = re.compile(r"\d{4}$") # 注意加上$表示匹配最后
string1 = "ahgk1314asg0999fa2222"
year_pattern.findall(string1)
#['1314', '0999', '2222']
```

```python
s = '《电网建设安规》  3.5.5.8  接地装置的敷设应符合GB0194《建设工程施工现场供用电 安全规范》的规定并应符合下列基本要求：a）人工接地体的顶面埋设深度不宜小于0.6m。b）人工垂直接地体宜采用热浸镀锌圆钢、角钢、钢管，长度宜为2.5m。人工水平接地体宜采用热浸镀锌的扁钢或圆钢。圆钢直径不应小于12mm；扁钢、角钢等型钢的截面积不应小于90mm2，其厚度不应小于3mm；钢管壁厚不应小于2mm。人工接地体不得采用螺纹钢。'
# 加上`?`:非贪婪模式
match1 = re.findall(r"《.*?》", s)
print(match1)
# ['《电网建设安规》', '《建设工程施工现场供用电安全规范》']
```



# 内置函数

## any & all

```python
'''
判断一个tuple或者list是否全为空，0，False。
如果全为空，0，False，则返回False；
如果不全为空，则返回True。
'''
any()


'''
all函数正好和any相反：
判断一个tuple或者list是否全为不为空，0，False。
如果全不为空，则返回True；否则返回False。
'''
all()
```

## zip() 函数

**zip()** 函数用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的列表。

```python
a=[1,2,3]
b=[4,5,6]
c=[4,5,6,7,8]
zipped = zip(a,b)
zipped
# output:<zip object at 0x103abc288>
list(zipped)
# output:[(1,4),(2,5),(3,6)]
list(zip(a,c))
# output:[(1,4),(2,5),(3,6)]    #与最短列表对齐
```