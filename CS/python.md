# 基本语法

## 变量类型

### 基础变量类型

- int
  - 任意精度
- float
  - 对应c中double
- bool
  - 首字母大写True/False
- str
  - 无需\0
  - 不可对单个字符修改
  - 支持负索引，相当于循环回末尾
- None
  - 代表空值？？？
  - 判断空值`if x is None:`
  


> / 是浮点数除法
>
> // 是整数除法

### 复合变量容器

- 列表list
  - `list = [elem1, elem2, ...]`
  - 第一个元素为0
  - 支持负索引 `lst[-1]`，范围**[-n, n-1]** (n为元素个数)
  - 修改 ：`lst[2] = 10`
  - 删除 ：`pop(index = -1)`
  - 增加 ：`append()`
  - 插入 ：`insert(index, obj)`
  - 长度 ：`len()`
- 元组tuple
  - `t = (1,2,3,4,5) `
  - 相当于 const数组
- 字典dict
  - 键值对结构 ：`student = {"name":"张三", "age":18, "score":90}`
  - 通过键取值 ：`student["name"]`
  - 修改或新建：
    - `dict_name[key] = value`，*如果不想赋值，使用cillections标准库defaultdict*
    - 一次多个：`dict_name.update({key:value, key:value, ...})`
- 集合 set
  - `s = {1, 2, 3, 3, 3}` 自动去重为 `{1,2,3}`

> 所有容器都不要求元素类型一致

## 流程控制

- if-elif-else
  - 数值0，0.0，None，所有空容器都会被判定为False
  - not取反
- while循环
- while-else
  - while结束后进入else部分
  - break会跳到else后头
- for循环
  - `for i in range(...):`
    - 在for循环内为i赋值不产生效果，因为在`for i in range(...):`会重新赋值
    - `range(end)` : `for(int i = 0; i < end; i++)`
    - `range(start, end)` : `for(int i = start; i < end; i++)`
    - `range(start, end, step)` : `for(int i = start; i < end; i += step)`
  - `for elem in container:`
    - 自动遍历容器的每一个元素
    - 如果container是字符串，遍历每一个字符
  - `for idx, elem in enumerate(elem_list):`
    - 可以为enumerate添加第二个参数，从哪开始
- break
  - 立即跳出循环
- continue
  - 跳过本次循环剩余代码


## 函数

```python
def function(a, b):
    #function
    return c
```
### 返回值

1. 无返回值
    函数无return，默认返回None

2. 多返回值
    return后用逗号分隔，调用时接收的变量也用逗号分隔

### 参数

1. 位置参数
    按参数的位置顺序传参
2. 默认参数
    默认参数在函数定义时只创建一次，后续调用会复用同一个对象，因此绝对不要用列表、字典等可变对象作为默认参数
    > 默认参数在内存中最好是一个const值
3. 关键字参数
    调用函数时，通过参数名=值的形式传参，不用按位置顺序传
4. 可变参数
    - *args：接收**任意**多个位置参数，打包成一个元组tuple
    - **kwargs：接收**任意**多个关键字参数，打包成一个字典dict


# python特性

## 切片操作

**序列[起始索引:结束索引:步长]**

> **左闭右开**，以步长取其中元素，生成新序列
> 可用的序列：
> - 列表 list
> - 元组 tuple
> - 字符串 str
> - 字节串 bytes


### 默认参数

> 第一给冒号不可省略，第二个冒号可随步长省略

- 起始索引 ：默认为0（第一个元素）
- 结束索引 ：序列长度
- 步长 ：1

### 负步长

- 从右往左倒序取元素
- 左闭右开依然成立
- 不能为0

### 负索引


## 推导式

### 列表推导式

1. 基础语法：`[ 元素处理表达式 for 循环变量 in 可迭代对象 ]`
2. 条件筛选：`[ 元素处理表达式 for 循环变量 in 可迭代对象 if 筛选条件 ]`
   > 多条件组合，直接用多个if语句
3. 嵌套循环：`[num for row in matrix for num in row]`

### 字典推导式

`{ 键表达式: 值表达式 for 循环变量 in 可迭代对象 if 筛选条件 }`
- 多个循环变量用逗号隔开
- 可迭代对象
  - zip(lst1, lst2) 
  - dict.items():给出key&value
  - dict.keys()
  - dict.values()
  - enumerate(dict.items(), start = 0) : idx, (key, value)

### 集合推导式

`{值表达式 for 循环变量 in 可迭代对象 if 筛选条件 }`

自动去重


## OOP

### 构造函数 \_\_init\_\_

第一个参数一定是 self 

### 创建实例

实例 = 类名(构造函数所需变量)

### self关键字

- 使用self.变量名来访问实例成员
  - self.实例变量
  - 类名.类变量
- 只要是实例方法，第一个参数必须写self，调用时不用写self
  

### 实例变量与类变量

|概念|定义|规则|
|---|---|---|
|实例变量|self.变量名, 在构造函数中定义|每个类的实例独有|
|类变量|在类体里定义|所有实例共有，修改后同步生效|

> 所有变量都是public，没有权限上的限定，没有封装


> 可以在任意地方定义实例变量，会动态添加，但不推荐！最好还是在构造函数里定义


### 继承

只有public继承
  
1. 基础语法
    `class 字类名(父类名):`
2. 父类构造函数调用：super()
    `super().__init__(name)`
    在子类构造函数中，要调用父类的构造函数
3. 多继承


### 多态

- 无需同一个父类，无需虚函数，只要两个类有同名方法，就能统一调用

- 子类重写父类方法，自动覆盖，无需使用虚函数

   


## 异常处理

### try-except

```python
try:
    # 这里放「你觉得可能会出错的代码」
    # 只要这里的代码触发了异常，就会立刻跳到except块执行
except 异常类型:
    # 这里放「出错后要执行的代码」
    # 只有try里的代码触发了对应类型的异常，才会执行这里
```
> 可以写多个except，也可以把多个类型塞到一起

```python
try:
    #代码

# 两种错误，共用一套提示
except (ValueError, ZeroDivisionError) as e:
    print(f"输入不合法，错误：{e}")
```

```python
 except TypeError as e:
        print(f"类型错误：{e}")
    except ValueError as e:
        print(f"数值错误：{e}")
    except Exception as e:
        print(f"未知错误：{e}")
```

e变量存储错误描述消息


### else

else里的代码，只有 try 块里没有触发任何异常、正常执行完毕时，才会运行

```python
try:
    #可能出错的代码
except 异常类型:
    #出错了执行的代码
else:
    #没出错，才会执行的代码
```


### finally

```python
try:
    #可能出错的代码
except 异常类型:
    #出错了执行的代码
else:
    #没出错执行的代码
finally:
    #无论如何，一定会执行的代码
```

### raise

主动抛出异常

`raise 异常类型("错误描述信息")`

raise错误后，所在函数立即停止并跳过

### 异常类型

|异常类型|触发场景|
|---|---|
|ZeroDivisionError|除以 0 的时候|
|ValueError|类型转换失败、参数值不合法（比如int("abc")）|
|TypeError|用了错误的数据类型（比如10 + "abc"）|
|NameError|访问了不存在的变量|
|IndexError|列表 / 字符串索引越界（比如lst = [1,2]，访问lst[5]）|
|KeyError|字典里访问了不存在的 key（比如d = {"a":1}，访问d["b"]）|
|FileNotFoundError|打开不存在的文件|
|AttributeError|访问对象不存在的属性 / 方法|

# 标准库

## 文本读写

```python
with open("文件路径", "打开模式", encoding="utf-8") as 文件变量名:
    # 在这里写读/写文件的代码
    # 缩进内的代码执行完，文件会自动关闭，不用手动写close
```

### open函数

```python
open(file, mode='r', encoding=None)
```

#### 文本路径

- 相对路径
- 绝对路径
  
Windows上复制过来的路径是反斜杠\，要改成正斜杠/或双反斜杠\\

#### 打开模式

|代码|名称|效果|
|---|---|---|
|r|只读模式（默认）|文件必须存在，不存在会报错|
|w|覆盖写模式|文件不存在会自动创建；文件已存在会直接清空全部内容，再写|
|a|追加写模式|文件不存在会自动创建；文件已存在会在末尾追加内容，不会清空原内容|
|rb|二进制只读模式|读图片、视频、exe 等非文本文件|
|wb|二进制覆盖写模式|写图片、视频等非文本文件|

#### 返回值

返回值即打开的文件

### 文件对象的函数

1. 读文件方法（r模式）
   1. read(size = -1) :一次性读取文件全部内容，返回字符串
   2. readline(size = -1) :逐行读取，保留换行符\n
   3. readlines(hint = -1) :返回值是一个列表，每一行是列表的一个元素，保留换行符\n
    > 可以使用strip()函数去除字符串的头尾空白符（空格、换行）
2. 写文件方法（w/a模式）
   1. write(text)
    - 将text写入文件中
    - 不会自动加换行符
    - 返回写入的字符数
   2. writelines(lines_list)
    - 将列表元素连续写入文件中
    - 不会自动加换行符

### 辅助控制函数

1. close()
   - 手动关闭文件，释放资源
   - with语句无需手动调用
2. seek(0)
   - 移动文件指针到指定位置（字节数）
3. tell()
   - 返回当前指针位置

## json数据处理

### json库函数

首先需要` import json`

|函数|作用|输入|输出|
|---|---|---|---|
|json.dumps(数据)|py数据->json字符串|字典/列表|字符串|
|json.loads(json字符串)|json字符串->py数据|字符串|字典/列表|
|json.dump(数据，文件对象)|py数据->json文件|字典/列表|无|
|json.load(文件对象)|json文件->py数据|文件对象|字典/列表|

dump()和dumps()
- 可以加上`indent = 缩进`格式化缩进
- 加上`ensure_ascii = False`防止中文乱码

> 可以转换的类型有：dict, list, tuple, str, int/float, bool, None


## collections标准库

### defaultdict

```python
from collections import defaultdic
```

自动给不存在的 key 设**默认值**
- defaultdict(int)：默认值是0，适合计数
- defaultdict(list)：默认值是空列表，适合分组
- defaultdict(set)：默认值是空集合，适合去重分组
- defaultdict(str)：默认值是空字符串

```python
list_dict = defaultdict(list)#创建一个默认值为空列表的dict

list_dict[key_i].append(1)
#key_i没有存在，会直接创建一个value为空列表的元素，然后append(1)
```


### Counter

```python
from collections import Counter
```
统计列表 / 字符串中元素的频率
`cnt = Counter(list/str)`返回一个key=元素，value=频率的字典

**方法**
|方法|作用|示例|
|---|---|---|
|most_common(n)|返回出现次数最多的前 n 个元素|cnt.most_common(2) → [('张三', 3), ('李四', 2)]|
|elements()|返回所有元素的迭代器（按出现次数重复）|list(cnt.elements()) → ['张三','张三','张三','李四','李四','王五']|
|update(iterable)|被统计的容器追加统计新的元素|cnt.update(["张三", "赵六"]) → 张三变成 4，赵六变成 1|

### deque
*双向高效队列*

``` python 
from collections import deque
# 创建双向队列
q = deque([1,2,3])

# 尾部操作（和list一样）
q.append(4)       # [1,2,3,4]
q.pop()           # 4 → [1,2,3]

# 头部操作（O(1)时间）
q.appendleft(0)   # [0,1,2,3]
q.popleft()       # 0 → [1,2,3]
```


## 正则表达式&&re标准库

```python
import re
```

### 正则表达式模式
1. 单字符匹配符

|模式|描述|
|---|---|
|\d|任意数字（0-9）|
|\w|任意字母、数字、下划线|
|\s|任意空白字符（空格、制表符、换行符）|
|.|任意字符（除了换行符）|
|[abc]|中括号内任意一个字符|
|[abc]|除了中括号内任意一个字符|
   
2. 匹配次数控制符
  跟在字符后，控制出现多少次

|模式|描述|
|---|---|
|*|0次或多次|
|+|至少一次|
|?|最多一次|
|{n}|n次|
|{n,m}|n到m次|

> 量词默认贪婪匹配，在后面加上?变成非贪婪匹配

3. 位置符

|模式|描述|
|---|---|
|^|放在开头，表示从字符串开头匹配|
|$|放在末尾，表示从字符串末尾匹配|

4. 其他

|模式|描述|
|---|---|
|()|分组，只提取括号内的内容，用group()方法访问|


