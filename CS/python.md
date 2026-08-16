# 基本语法

- 变量类型
	- 可以使用`type(变量)`函数查看变量类型
	- 基础变量类型
		- number
			- int
				- 任意精度
			- float
				- 对应c中double
			- bool
				- 首字母大写True/False
			- complex
				  - `a+bj`
				  - `complex(a, b)`
		- str
			- 使用`'`或`"`创建字符串
				- 三引号：允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符
			- 无需\0
			- 访问
				-str[n]
				- 支持负索引，相当于循环回末尾
				- 不可对单个字符修改
			- 字符串运算符
				- a 为"Hello", b为"Python"
				- 
				  |操作符|描述|实例|
				  |---|---|---|
				  |+|字符串连接|a + b 结果为HelloPython|
				  |\*|重复输出字符串|a\*2 结果为HelloHello|
				  |[]|通过索引获取字符串中字符|a[1] 结果为e|
				  |[ : ]|截取字符串中一部分，左闭右开|a[1:4] 结果为 ell|
				  |in|成员运算符，如果字符串中包含给定字符返回True|'H' in a 结果为True|
				  |not in|成员运算符，如果字符串中不包含给定字符返回True|'M' not in a 结果为True|
				  |r/R|原始字符串，所有字符都按字面意思使用，没有转义|r'\n'|
				  |%|格式字符串||
			- 字符串格式化(与c语言printf类似)
				- `"格式字符串" % (数据1, 数据2, ...)`
				- 格式化符号
				  
				  |符号|描述|
				  |---|---|
				  |%c|字符|
				  |%s|字符串|
				  |%d|整数|
				  |%u|无符号整型|
				  |%o|无符号八进制数|
				  |%x|无符号十六进制数|
				  |%f|浮点数|
				  |%e|科学计数法浮点数|
				  |%p|十六进制表示的地址|
				  
				- 辅助指令 %[标志][宽度][.精度][类型码]
				  
				  |符号|描述|
				  |---|---|
				  |\*|定义宽度或小数点精度|
				  |-|左对齐|
				  |+|默认显示加号|
				  |#|八进制前显示0，十六进制前显示0x|
				  |0|默认用0填充|
				  |%|`%%`输出单一的%|
			- f-string
				- `f"内容 {变量}"`
				- `f"内容 {变量 : 格式指令}"`
					- 除以下表格内，其他与字符串格式化的方式一致
					  
					  |符号|作用|
					  |---|---|
					  |`<`|左对齐|
					  |`>`|右对齐（数字默认）|
					  |`^`|居中对齐|
		- None
		  - 代表空值？？？
		  - 判断空值`if x is None:`
		- / 是浮点数除法
		- // 是整数除法
	- 复合变量容器
		- 列表list
			- `list = [elem1, elem2, ...]`
			- 第一个元素为0
			- 支持负索引 `lst[-1]`，范围**[-n, n-1]** (n为元素个数)
			- 可以使用+组合列表，用*重复列表
			- 函数
			  
			  |函数|作用|
			  |---|---|
			  |len(list)|返回列表元素个数|
			  |max(list)|返回列表元素最大值|
			  |min(list)|返回列表元素最小值|
			  |list(seq)|将元组转换为列表|
			  
			- 方法
			  
			  |方法|作用|
			  |---|---|
			  |append(obj)|在列表末尾添加新的对象|
			  |count(obj)|统计某个元素出现次数|
			  |index(obj)|找出某个值第一个匹配的索引位置|
			  |insert(index, obj)|将对象插入列表|
			  |pop(index = -1)|移除列表中元素，返回该元素的值|
			  |remove(obj)|移除列表中某个值的第一个匹配项|
			  |reverse()|反转列表顺序|
			  |clear()|清空列表|
			  |copy()|返回复制后的列表|
			  |len()|返回元素个数|
		- 元组tuple
			- `t = (1,2,3,4,5) `
			- 相当于 const数组
		- 字典dictionary
			- 键值对结构 ：`student = {"name":"张三", "age":18, "score":90}`
			- 通过键取值 ：`student["name"]`
				- 如果键有可能不存在，使用`get(key, default = None)`方法，若不存在返回default设置的值
			- 修改或新建：
			    - `dict_name[key] = value`，*如果不想赋值，使用cillections标准库defaultdict*
			    - 一次多个：`dict_name.update({key:value, key:value, ...})`
		- 集合 set
			- `s = {1, 2, 3, 3, 3}` 自动去重为 `{1,2,3}`
		> **所有复合变量容器都不要求元素类型一致**
- 流程控制
	- if-elif-else
		- 数值0，0.0，None，所有空容器都会被判定为False
		- not取反
	- while循环
	  ```python 
	  while condition:
		  statements
	  ```
	- while-else
	  ```python
	  while condition:
		  statements
	  else:
		  additional_statements
	  ```
		- while结束后进入else部分
		- break会跳到else后头
	- for循环
	  ```python
	  for <variable> in <sequence>:
		  <statements>
	  else:
		  <statements>
	  ```
		- `for i in range(...):`
			- range()函数返回数字组成的列表
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
- 函数
	- 格式
	  
	  ```python
	  def function(a, b):
		  "函数_文档字符串(说明函数)"
		  #function
		  return c
	  ```
	- 返回值
		1. 无返回值
			函数无return，默认返回None对象
		2. 多返回值
			return后用逗号分隔，调用时接收的变量也用逗号分隔
	- 参数
		- 可变类型与不可变类型
			- 传可变参数后改变其值，改变原来的对象；传不可变参数后改变其值，创建新对象，不改变原来对象
			- 可变类型：strings, tuples, 和 numbers
		1. 必须参数re
		    按参数的位置顺序传参
		2. 默认参数
			- 如果没有传递参数则使用默认值
			- `def function_name(arg1 = "default_ref"):`
		    > 默认参数在函数定义时只创建一次，后续调用会复用同一个对象，因此绝对不要用列表、字典等可变对象作为默认参数
			> 默认参数在内存中最好是一个const值
		3. 关键字参数
		    调用函数时，通过参数名=值的形式传参，不用按位置顺序传
		4. 可变参数
		    - *args：一个\*，接收**任意**多个位置参数，打包成一个元组tuple
			    - `def functionname([formal_args,] *var_args_tuple ):`
		    - \**kwargs：两个\**，接收**任意**多个关键字参数，打包成一个字典dict
			    - `def functionname([formal_args,] **var_args_dict ):`
			    - 传参时使用`key = value, ...`的形式
	- 装饰器
		- **在不修改原函数代码的前提下，动态扩展函数或类的功能**
		- 语法
			  - 无参数
			```python
			  def decorator_function(original_function):
				  def wrapper():
					  #在这里完成新的函数，即修饰后的函数
					  return result_function
			  return wrapper
			
			  @decorator_function
			  def target_function():
				  #target_function的定义
				  
				其实等价于
			  def target_function():
				  pass
			  
			  target_function = decorator_function(target_function)
			```
			- 原函数带参数，需要使用该参数
			  ```python
			  def decorator_func(target_func):
				  def wrapper(*args, **kwargs):
				  #完成新函数的定义，调用target_func(*args, **kwargs)
			  return wrapper
			  ```
			- 修饰器带参数
			  ```python
			  def decorator_func(avg):
				  def decorator(target_func):
					  def wrapper(*args, **kwargs):
						  #完成新函数的定义
				  return wrapper
			  return decorator
			  ```
- OOP
	- 构造函数 \_\_init\_\_
		- 第一个参数一定是 self 
	-  self关键字
		- 类定义内，使用self.变量名来访问实例成员
		- self.成员函数
		- self.实例变量
		- 类名.类变量
		- 只要是实例方法，第一个参数必须写self，调用时不用写self
	- 创建实例
		实例 = 类名(构造函数所需变量)
	- 继承
		- 
		    ```python
		    class DerivedClassName(BaseClassName):
		    <statement-1>
		    .
		    .
		    .
		    <statement-N>
		    ```
		- 只有public继承
		- 调用父类构造函数：
			- `父类名.__init__(self, ...)`
				- 使用类名调用函数不会自动传self，使用实例调用函数会自动传self
			- `super(子类名, self).__init__(...)`
			- `super().__init__(...)`
		- 多继承
			- 
			  ```python
			  class DerivedClassName(Base1, Base2, Base3):
			    <statement-1>
			    .
			    .
			    .
			    <statement-N>
			  ```
			- 使用父类方法时，按圆括号内顺序从左到右依次搜索父类的方法，使用第一个同名的
	- 在方法和属性前加两个下划线，变为私有的方法或变量，外部不能使用
	- 实例变量与类变量
		-
		   |概念|定义|规则|
		   |---|---|---|
		   |实例变量|self.变量名, 在构造函数中定义|每个类的实例独有|
		   |类变量|在类体里定义|所有实例共有，修改后同步生效|
		- 可以在任意地方定义实例变量，会动态添加，但不推荐！最好还是在构造函数里定义
	- 多态
		- 无需同一个父类，无需虚函数，只要两个类有同名方法，就能统一调用
		- 子类重写父类方法，自动覆盖，无需使用虚函数
- 模块
	- 
	  ```python
	  import module1[, module2[,... moduleN]
	  from modname import name1[, name2[, ... nameN]]
	  import numpy as np  # 将 numpy 模块别名设置为 np
      from math import sqrt as square_root  # 将 sqrt 函数别名设置为 square_root
	  ```
	- 模块的搜索路径
		1. 当前环境(不会自动搜索文件夹内部)
		2. 环境变量PYTHONPATH指定目录
		3. 标准库目录
		4. .pth文件指定的目录
	- 模块除了方法定义，还可以包括可执行的代码。这些代码一般用来初始化这个模块。这些代码只有在第一次被导入时才会被执行
	- `__name__`属性
		- - 如果模块是被直接运行，`__name__` 的值为 `__main__`
		- - 如果模块是被导入的，`__name__` 的值为模块名
	- 包
		- 包含__init__.py的文件夹
		- 使用'.'来访问上级包，一个'.'是当前包（当前文件夹
		- 例如：
		  ```python
		  文件夹：
		  A/
			  __init__.py
			  B/
				  __init__.py
				  C.py
		  代码：
		  import A.B.C
		  from A.B import C	
		  ```


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
  - dict.items():给出`(key, value)`元组组成的列表
  - dict.keys()
  - dict.values()
  - enumerate(dict.items(), start = 0) : idx, (key, value)

### 集合推导式

`{值表达式 for 循环变量 in 可迭代对象 if 筛选条件 }`

自动去重





- 异常处理
	- try-except
		```python
		try:
		    # 这里放「你觉得可能会出错的代码」
		    # 只要这里的代码触发了异常，就会立刻跳到except块执行
		except 异常类型:
		    # 这里放「出错后要执行的代码」
		    # 只有try里的代码触发了对应类型的异常，才会执行这里
		```
		- 可以写多个except，也可以把多个类型放到一个元组里
			```python
			try:
			    #代码
			# 两种错误，共用一套提示
			except (ValueError, ZeroDivisionError) as e:
			    print(f"输入不合法，错误：{e}")

			try:
				
			except TypeError as e:
			        print(f"类型错误：{e}")
				except ValueError as e:
			        print(f"数值错误：{e}")
			    except Exception as e:
			        print(f"未知错误：{e}")
			```
	- try/excpt...else
		- else里的代码，只有 try 块里没有触发任何异常、正常执行完毕时，才会运行
			```python
			try:
			    #可能出错的代码
			except 异常类型:
			    #出错了执行的代码
			else:
			    #没出错，才会执行的代码
			```
	- try-finally
		- finally内的语句不论有没有出错都会执行
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
	-raise
		- 使用raise语句来主动抛出一个指定的异常
		- `raise 异常类型("错误描述信息")`
		- 单独写一个raise也可以
		- `raise` 主动抛出异常 → 解释器**立刻停止当前代码**，顺着**调用栈向外逐层往上找 `except`**
	- 异常（Exception类）
		- 用户自定义异常
		  ```python
		  class MyError(Exception):  
		  def __init__(self, value):  
			  super().__init__(value)
			  self.value = value  
		  def __str__(self):  
			return repr(self.value)
		  ```
		- 异常类型
		
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
- 标准库
	- 文本读写
		- 
		    ``` python
			with open("文件路径", "打开模式", encoding="utf-8") as 文件变量名:
			# 在这里写读/写文件的代码
			# 缩进内的代码执行完，文件会自动关闭，不用手动写close
			```
		- open函数
			- 
			  ```python
			  open(file, mode='r', encoding=None)
			  ```
			- 文本路径
				- 相对路径
				- 绝对路径
				- Windows上复制过来的路径是反斜杠\，要改成正斜杠/或双反斜杠\\
			- 打开模式
				- |代码|名称|效果|
				  |---|---|---|
				  |r|只读模式（默认）|文件必须存在，不存在会报错|
				  |w|覆盖写模式|文件不存在会自动创建；文件已存在会直接清空全部内容，再写|
				  |a|追加写模式|文件不存在会自动创建；文件已存在会在末尾追加内容，不会清空原内容|
				  |rb|二进制只读模式|读图片、视频、exe 等非文本文件|
				  |wb|二进制覆盖写模式|写图片、视频等非文本文件|
			- 返回值
				- 返回值即打开的文件
		- 文件对象的函数
			- 读文件方法（r模式）
				1. read(size = -1) :一次性读取文件全部内容，返回字符串
				2. readline(size = -1) :逐行读取，保留换行符\n
				3. readlines(hint = -1) :返回值是一个列表，每一行是列表的一个元素，保留换行符\n
					可以使用strip()函数去除字符串的头尾空白符（空格、换行）
			- 写文件方法（w/a模式）
				1. write(text)
				    - 将text写入文件中
				    - 不会自动加换行符
				    - 返回写入的字符数
				2. writelines(lines_list)
				    - 将列表元素连续写入文件中
				    - 不会自动加换行符
			- 辅助控制函数
				1. close()
				   - 手动关闭文件，释放资源
				   - with语句无需手动调用
				1. seek(0)
				   - 移动文件指针到指定位置（字节数）
				1. tell()
				   - 返回当前指针位置
	- requests模块
		- 方法
			- request.get(url, headers = ?) 返回一个response类的实例
			- response对象包含的响应信息：
			  
				|属性或方法|说明|
				|---|---|
				|apparent_encoding|编码方式|
				|close()|关闭与服务器的连接|
				|content|返回响应的内容，以字节为单位|
				|cookies|返回一个 CookieJar 对象，包含了从服务器发回的 cookie|
				|elapsed|返回一个 timedelta 对象，包含了从发送请求到响应到达之间经过的时间量，可以用于测试响应速度。比如 r.elapsed.microseconds 表示响应到达需要多少微秒。|
				|encoding|解码 r.text 的编码方式|
				|headers|返回响应头，字典格式|
				|history|返回包含请求历史的响应对象列表（url）|
				|is_permanent_redirect|如果响应是永久重定向的 url，则返回 True，否则返回 False|
				|is_redirect|如果响应被重定向，则返回 True，否则返回 False|
				|iter_content()|迭代响应|
				|iter_lines()|迭代响应的行|
				|**json()**|返回结果的 JSON 对象 (结果需要以 JSON 格式编写的，否则会引发错误)|
				|links|返回响应的解析头链接|
				|next|返回重定向链中下一个请求的 PreparedRequest 对象|
				|ok|检查 "status_code" 的值，如果小于400，则返回 True，如果不小于 400，则返回 False|
				|**raise_for_status()**|如果发生错误，方法返回一个 HTTPError 对象，requests.RequestException类|
				|reason|响应状态的描述，比如 "Not Found" 或 "OK"|
				|request|返回请求此响应的请求对象|
				|**status_code**|返回 http 的状态码，比如 404 和 200（200 是 OK，404 是 Not Found）|
				|**text**|返回响应的内容，unicode 类型数据|
				|**url**|返回响应的 URL|
	- json模块
		- 函数
		  
			|函数|作用|输入|输出|
			|---|---|---|---|
			|json.dumps(数据)|py数据->json字符串|字典/列表|字符串|
			|json.loads(json字符串)|json字符串->py数据|字符串|字典/列表|
			|json.dump(数据，文件对象)|py数据->json文件|字典/列表|无|
			|json.load(文件对象)|json文件->py数据|文件对象|字典/列表|
			- dump()和dumps()
				- 可以加上`indent = 缩进`格式化缩进
				- 加上`ensure_ascii = False`防止中文乱码
		- 可转化对象
			|Python|JSON|
			|---|---|
			|dict|object|
			|list,tuple|array|
			|str|string|
			|number|number|
			|True|ture|
			|False|false|
			|None|null|
	- pathlib模块
		- 路径对象 Path：`p = Path("文件/文件夹地址")`
			- 路径对象可拼接，使用`/`与`字符串`进行拼接
		- 遍历目录文件
			- 所有文件`for item in folder.iterdir():`
			- 筛选特定文件 `for item in folder.glob("*.文件后缀")`
			- 查找所有层级的特定文件 `for item in folder.rglob("*.文件后缀")`
		- Path(__file__)是当前文件路径
		- .parent为上一级
		







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


