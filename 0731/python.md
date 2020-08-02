### 初始Python

##### 简介

1. Python的创始人是吉多·范罗苏姆，曾经参与了ABC(不开源)的设计；

2. Python中常用的集成开发环境之一：Pycharm；

3. Python是一门解释性、面向对象和动态数据类型的高级程序设计语言。

##### 优点

* 易学习

* 易阅读

* 易维护

* 拥有广泛的标准库

* 可移植

* 可扩展

* 可嵌入

* GUI编程

##### 缺点

* 代码不能加密

* 代码执行效率低

### 编译器

##### 概念

编译器是一种将其他语言翻译成机器语言的工具。

> 注：
>
> 当编译器以解释的方式执行时，那么编译器也被称为解释器。

##### 编译器编译的方式

* 编译

* 解释

##### 编译性语言和解释性语言

* 编译性语言编写的程序在执行之前需要一个专门的编译过程，先将程序代码编译成一个机器语言文件，当程序执行时，那么不再需要对程序重新编译，只需要执行编译的结果就行了。

* 解释性语言编写的程序不需要预先编译，并且是以文本的方式存储程序代码，当程序执行时会将代码一句一句地直接执行(先解释后执行)。

* 编译性语言编写的程序代码执行效率高，但跨平台性差；解释性语言编写的程序代码执行效率低，但跨平台性好。

* 编译性语言和解释性语言的编译时间点不同。

### 内存

##### 概念

内存也被称为内存储器，是计算机中最重要的部件之一(计算机中所有程序的执行都是在内存中进行的)，并且它是计算机与CPU进行沟通的桥梁。

##### 作用

主要用于暂时存储CPU中运算的数据，以及与硬盘等外部存储器进行沟通的数据。

##### 单位换算

Bit Byte kb Mb Gb Tb

8   1024 1  1  1  1

##### 常用进制

* 二进制(B)

* 八进制(Q)

* 十进制(D)

* 十六进制(H)

    主要用于表示内存地址。

##### 进制间的转换

* 十转二

    倒除法，余数逆序。
    
* 二转十

    每个数字乘以对应的2的位数次方再相加。
    
* 八转二

    `四二一`法，一转三位，转换时按照十进制来转换。
    
* 二转八

    三位一取，从最低位开始取，高位不够补零。
    
* 十六转二

    `八四二一`法，一转四位，转换时按照十进制来转换。
    
* 二转十六

    四位一取，从最低位开始取，高位不够补零。

### 数据存储

##### 概念

计算机存储数据时，先开辟内存空间(计算机开辟内存空间的最小计量单位是1Byte)，再存储数据(计算机存储数据时，用最高位标识符号，0表示正数，1表示负数，存储的是数据的二进制补码)。

##### 原码、反码和补码

* 原码

    规定了字节数，写明了符号位。

* 反码

    正数的反码是其原码，负数的反码是其原码的符号位不变，其他位取反。

* 补码

    正数的补码是其原码，负数的补码是其原码的反码，再加1。
    
    > 技巧：
    >
    > 符号位不变，从最低位开始，再遇见第一个1之前什么都不变，遇见第一个1时，保留这个1，之后按位取反。
    >
    > 注：
    >
    > 补码的补码是其原码。

##### 模式的分类

* 交互模式

* 命令行模式

    > 附：
    >
    > 绝对路径：是从根目录开始链接的路径。
    >
    > 相对路径：不是从根目录开始链接的路径。

### 输入、打印和注释

##### 输入

```python
input(提示信息)
```

##### 打印

* 打印单条信息

    ```python
    print(信息[, end])
    ```

* 打印多条信息

    ```python
    print(信息, ...)
    ```

* 打印多行信息

    ```python
    print("""
    信息
    """)
    print('''
    信息
    ''')
    ```

##### 注释

* 单行注释(也被称为行注释)

    ```python
    # 注释
    ```

* 多行注释(也被称为块注释)

    ```python
    """
    注释
    """
    '''
    注释
    '''
    ```

* 辅助注释

    ```python
    代码  # 注释
    ```

### 数据类型和标识符

##### 数据类型

* 数字类型

    `str` `int` `float` 复数 `bool`

* 非数字类型

    `None` `list` `tuple` `dict` `set`

##### 标识符

* 概念

    标识符是一串字符串。

* 书写规则

    1. 首字符必须是字母或下划线，其他字符可以是数字、字母或下划线；
    
    2. 不允许是Python关键字；
    
        ```python
        import keyword
 
        print(keyword.kwlist)
        ```
        
    3. 区分大小写。

* 作用

    主要用于给变量、函数或类等命名。

### 变量和常量

##### 变量

* 概念

    变量是程序执行期间可操作的存储空间的名称，并且是程序执行期间可以改变的数据。

* 作用

    主要用于将不同数据类型的数据存储到内存。

* 定义

    * 单一赋值
    
        ```python
        变量名 = 值
        ```
        
    * 对称赋值
    
        ```python
        变量名, ... = 值, .../字符串/列表/元组/字典/集合变量名
        ```
        
    * 统一赋值
    
        ```python
        变量名 = ... = 值
        ```    

* 查看变量的类型和地址

    ```python
    id(变量名)
    type(变量名)
    ```

* 删除变量

    ```python
    del 变量名
    ```

##### 常量

常量是程序执行期间不可以改变的数据。

### 数据类型间的转换和常用数学函数

##### 数据类型间的转换

* 转换成整数

    ```python
    int(数值[, base])
    ```

* 转换成浮点数

    ```python
    float(数值)
    ```

* 转换成字符串

    ```python
    str(数值/列表/字典/元组/结合变量名)
    ```

##### 常用数学函数

```python
max/min(数值, .../字符串/(数值或)字符串列表/元组/字典/集合变量名)
abs(数值)
pow(数值, n次方)
round(数值, 保留小数位数)
sum(数值列表/数值元组/数值字典/数值集合)
range([start, ]end[, step])

import math

math.ceil/floor(数值)
math.sqrt(数值)
math.modf(数值)

import random

random.random()
random.uniform(start, end)
random.randint(start, end)
random.randrange([start, ]end[, step])
random.choice(字符串/列表/元组变量名)
random.shuffle(列表变量)
```

### 常用运算符

##### 算术运算符

`+` `-` `*` `/` `**` `//` `%`

##### 赋值运算符

`=`

##### 复合运算符

`+=` `-=` `*=` `/=` `**=` `//=` `%=`

##### 比较运算符

`==` `!=` `>` `>=` `<` `<=`

##### 逻辑运算符

`and` `or` `not 布尔表达式`

##### 成员运算符

`in` `not in`

##### 身份运算符

`is` `is not`

##### 位运算符

`&` `|` `^` `~` `<<` `>>`

### 常用语句

##### 判断语句(也被称为分支语句)

* 单条件判断

    ```python
    if 条件语句:
      ...
    elif 条件语句:
      ...
    ...
    else:
      ...
    ```

* 多条件判断

    ```python
    if 条件语句 and/or 条件语句:
      ...
    else:
      ...
    ```

* 三元表达式

    ```python
    [变量名 = ]条件语句为True时返回的结果 if 条件语句 else 条件语句为False时返回的结果
    ```

##### 循环语句

* `for`循环

    ```python
    for 变量名 in iterable对象:
      ...
    else:
      ...
    ```

* `while`循环

    ```python
    while 条件语句:
      ...
    else:
      ...
    ```
    
    > 附：
    >
    > ```python
    > for语句/while语句:
    >     ...
    >     if 条件语句:
    >         break/continue
    >     ...
    > ```

### `r`和ASCII码转换

##### `r`

Python允许用`r`来表示内部的字符串不转义。

##### ASCII码转换

* 将Python中的单个字符转换成ASCII值

    ```python
    ord("单个字符")
    ```

* 将ASCII值转换成Python中的单个字符

    ```python
    chr(ASCII码值)
    ```

### 字符串

##### 概念

字符串使用英文状态下的单引号或双引号括起来的任意文本。

##### 访问

* 单个字符

    ```python
    str[索引]
    ```

* 多个字符

    ```python
    str[[start]:[end][:step]]
    ```

##### 复制

```python
变量名 = str[索引]/[[start]:[end][:step]]
```

##### 拼接和重复

* 拼接

    ```python
    str + ...
    ```

* 重复

    ```python
    str * 数字
    ```

##### 大小比较

从字符串中的第一个字符开始比较，谁的ASCII码值比较大谁就大，如果想等，那么继续比较字符串中的下一个字符，以此类推。

##### 常用方法

* 计算字符串的长度

    ```python
    len(str)
    ```

* 对字符串进行取值

    ```python
    eval(str)
    ```

* 对齐字符串

    ```python
    str.center/ljust/rjust(width[, fillchar])
    str.zfill(width)
    ```

* 修改字符串中字母的大小写

    ```python
    str.capitalize/title/upper/lower/swapcase()
    ```

* 判断字符串中的字符

    ```python
    str.istitle/isupper/islower/isdigit/sialpht/isspace()
    ```

* 统计指定子字符串在给定范围的原字符串中出现的次数

    ```python
    str.count(子字符串变量名[, start, end])
    ```

* 判断指定子字符串是否存在于给定范围的原字符串中，如果存在，那么返回该子字符串在原字符串中第一次出现的位置索引(与`start`无关)，如果不存在，那么返回-1

    ```python
    str.index/rindex(子字符串变量名[, start, end])
    str.find/rfind(子字符串变量名[, start, end])
    ```

* 判断指定子字符串是否存在于给定范围的原字符串中的给定位置

    ```python
    str.startswith/endswith(子字符串变量名[, start, end])
    ```

* 字符串的编码和解码

    ```python
    str.encode/decode(encoding[, errors="ignore"])
    ```

* 删除字符串中的指定字符

    ```python
    str.strip/rstrip/lstrip()
    ```

### 列表

##### 概念

列表是由一系列按特定顺序排列的元素组成的序列，用`[]`来表示，元素间用英文状态下的`,`进行分隔。

##### 创建

```python
变量名 = []/list()
```

##### 访问

* 单个元素

    ```python
    list[索引]
    ```

* 多个元素

    ```python
    list[[start]:[end][:step]]
    ```

##### 复制

```python
变量名 = list[索引]/[[start]:[end][:step]]
```

##### 修改

* 单个元素

    ```python
    list[索引] = 新元素
    ```

* 多个元素

    ```python
    list[[start]:[end][:step]] = 新元素序列
    ```

##### 拼接和重复

* 拼接

    ```python
    list + ...
    ```

* 重复

    ```python
    list * 数字
    ```

##### 常用方法

* 添加

    * 单个元素
    
        ```python
        list.append(新元素)
        list.insert(索引, 新元素)
        ```

    * 多个元素
    
        ```python
        list.extend(新元素序列)
        ```

* 排序

    ```python
    list.sort([reverse=True/False])
    ```

* 删除

    * 单个元素
    
        ```python
        list.pop([索引])
        list.remove(元素)
        del list[索引]
        ```

    * 多个元素
    
        ```python
        list.clear()
        del list[[start]:[end][:step]]
        del list
        ```

* 计算列表中元素的个数

    ```python
    len(list)
    ```

* 统计指定元素在列表中出现的次数

    ```python
    list.count(元素)
    ```

* 判断指定元素是否存在于给定范围的列表中，如果存在，那么该元素在列表中第一次出现的位置索引(与`start`无关)，如果不存在，那么程序将会报错

    ```python
    list.index(元素[, start, end])
    ```

* 浅拷贝和深拷贝

    ```python
    import copy
    
    copy.copy(list)
    copy.deepcopy(list)
    ```

* 数据类型间的转换

    * 转换成列表
    
        ```python
        list(字符串/元组/字典/集合变量名)
        ```
    
    * 转换成字符串
    
        ```python
        "分隔符".join(列表/元组/字典/集合变量名)
        ```
    
### 元组

##### 概念

元组和列表类似，用`()`来表示，并且元组是不可变的，而列表是可变的，如果要修改元组中的部分元素，那么必须要重新定义该元组。

##### 创建

```python
变量名 = ()/tuple()
```

##### 访问、复制、拼接和重复

和列表的一样。

##### 删除

```python
del tuple
```

##### 常用方法

* 计算元组中元素的个数

    ```python
    len(tuple)
    ```

* 转换成元组

    ```python
    tuple(字符串/列表/字典/集合变量名)
    ```

### 字典

##### 概念

字典是由一系列键值对组成的序列，并且在字典中查找数据的速度极快，但占用空间大，内存浪费多。

##### 键的数据类型

键的数据类型只能是数字、字符串或元组。

##### 创建

```python
变量名 = {}/dict(key=value, ...)
```

##### 添加

* 单个键值对

    ```python
    dict[newKey] = newValue
    ```

* 多个键值对

    ```python
    dict.update(newDict)
    ```

##### 访问

```python
dict[key]
dict.get(key[, default])
```

##### 修改

```python
dict[key] = newValue
```

##### 删除

* 单个键值对

    ```python
    dict.pop(key)
    dict.popitem()
    del dict[key]
    ```

* 多个键值对

    ```python
    dict.clear()
    del dict
    ```

##### 遍历

* 遍历所有的键值对

    ```python
    for k, v in dict.items():
      ...
    ```

* 遍历所有的键或值

    ```python
    for 变量名 in dict.keys/values():
      ...
    ```

##### 常用方法

* 计算字典中键值对的数量

    ```python
    len(dict)
    ```

### 集合

##### 概念

集合和字典类似，是由一系列无序且无重复的元素组成的序列。

##### 创建

```python
变量名 = set()
```

##### 添加

* 单个元素

    ```python
    set.add(新元素)
    ```

* 多个元素

    ```python
    set.update(新元素序列)
    ```

##### 删除

* 单个元素

    ```python
    set.remove(元素)
    ```

* 多个元素

    ```python
    set.clear()
    del set
    ```

##### 运算

* 与

    ```python
    set1 & set2
    ```

* 或

    ```python
    set1 | set2
    ```

* 异或

    ```python
    set1 ^ set2
    ```

* 差

    ```python
    set1 - set2
    ```

##### 常用方法

* 计算集合中元素的数量

    ```python
    len(set)
    ```

* 转换成集合

    ```python
    set(字符串/列表/元组/字典变量名)
    ```

### 可迭代对象和迭代器

##### 可迭代对象

* 概念

   可迭代对象是可以直接被用于`for`循环的对象。

* 分类

    * 容器类型对象
    
    * `generator`

##### 迭代器

* 概念

    迭代器是可以被`next()`方法不断调用，并且返回下一个值的对象。

* 生成

    ```python
    iter(object[, sentinel])
    ```

##### 判断数据类型

* 单种数据类型判断

    ```python
    isinstance(object, 数据类型)
    ```

* 多种数据类型判断

    ```python
    isinstance(object, (数据类型, ...))
    ```

### 函数

##### 本质

函数实际上是对一些功能的封装。

##### 创建

```python
def 函数名(形参, ...):
    """文档字符串的注释"""
    ...
    return ...
```

##### 缺省参数

缺省参数是一个拥有默认值的形参。

##### 传递实参

* 位置传参

    ```python
    函数名(实参, ...)
    ```

* 关键字传参

    ```python
    函数名(形参=实参, ...)
    ```

### 变量进阶

##### 不可变数据类型和可变数据类型

* 不可变数据类型

    不可变数据类型是内存中的数据不允许被修改，例如字符串、`int`、`float`、复数、`bool`、`None`和`tuple`。

* 可变数据类型

    可变数据类型是内存中的数据允许被修改，例如列表、字典或集合.

##### 局部变量

局部变量是定义在函数体内的变量，只能在该函数体内使用。

##### 全局变量

全局变量是定义在函数体外的变量，可以在整个包或包外使用。

##### 形式参数

形式参数是定义函数时使用的变量，只能在该函数体内使用。

##### 函数体内调用变量原理

当调用函数时，那么程序首先会在局部变量中查找该变量，如果存在，那么调用该局部变量，如果不存在，那么程序会继续在全局变量中查找该变量，如果存在，那么调用该全局变量，如果不存在，那么程序会报错。

##### 函数体内修改全局变量

* 全局变量是可变数据类型

    直接在函数体内进行修改。
    
* 全局变量是不可变数据类型

    通过`global 变量名`来进行修改。

### 递归函数

##### 概念

递归函数是一个可以调用自身的函数。

##### 设计

1. 写出临界条件；

2. 找出这一次与上一次的关系。

##### 深度遍历和广度遍历

* 深度遍历

    递归实现。

* 广度遍历

    队列实现。

### 文件处理

##### 结构

`open(file, mode[, encoding, errors])`

##### `.txt`文件处理

* 读取

    ```python
    with open(file, "r"[, encoding, errors]) as file_object:
      contents = file_object.read([字符长度])
      line = file_object.readline([字符长度])
      lines = file_object.readlines()
    ```

* 写入

    ```python
    with open(file, "w"[, encoding, errors]) as file_object:
      file_object.write("内容")
    ```
    
> 附：
>
> ```python
> import pickle
> 
> with open(file, "rb"[, encoding, errors]) as file_object:
>     contents = pickle.load(file_object)
>     
> with open(file, "r"[, encoding, errors]) as file_object:
>     pickle.dump(内容, file_object)
> ```

##### `.json`文件处理

* 读取

    ```python
    import json  
  
    with open(file, "r"[, encoding, errors]) as file_object:
      contents = json.load(file_object)
    ```

* 写入

    ```python
    import json
  
    with open(file, "w"[, encoding, errors]) as file_object:
      json.dump(内容, file_object)
    ```

##### `.csv`文件处理

* 读取

    ```python
    import csv
  
    with open(file, "r"[, encoding, errors]) as file_object:
      reader = csv.reader(file_object)
      for row in reader:
          ...
    ```

* 写入

    ```python
    import csv
  
    with open(file, "w"[, encoding, errors]) as file_object:
      writer = csv.writer(file_object)
      writer.writerow(data)
    ```

### `os`模块

##### 概述

`os`模块是一个包含操作系统功能的模块。

##### `os`

```python
import os

os.name
os.uname()
os.environ
os.mkdir(path)
os.listdir([path])
os.stat(path)
os.path.getsize(path)
os.rename(path, newPath)
os.rmdir(path)
os.remove(path)
os.curdir
os.getcwd()
os.popen("...").read()
```

##### `os.path`

```python
os.path.abspath(相对路径）
os.path.join(path, ...)
os.path.split(path)
os.path.dirname(path)
os.path.basename(path)
os.path.splitext(path)
os.path.isfile(path)
os.path.isdir(path)
os.path.exists(path)
```

### 模块

##### 概述

模块是一个可执行的`.py`文件。

##### 优点

1. 提高代码的可维护性；

2. 提高代码的复用度；

3. 避免程序中的变量名和函数名冲突。

##### 分类

* 内置模块

* 第三方模块

* 自定义模块

##### 引入方式

* 引入指定模块

    ```python
    import module [as 别名], ...
    ```

* 引入模块中特定的变量名、函数名或类名

    ```python
    form module import name [as 别名], ...
    ```

* 引入模块中所有的变量名、函数名或类名

    ```python
    from module import *
    ```

### 包

##### 概述

为了解决模块命名的冲突，引入了按目录来组织模块的方法，其中目录(必须包含一个`__init__.py`文件)被称为包。

##### 特点

只要顶层的包不发生冲突，那么包中的模块也不会发生冲突。

##### 结构

* 引入包

    在`__init__.py`文件中写入

    ```python
    form .module import name [as 别名], ...
    ```

* 导入包

    ```python
    import 包名
    ```

* 使用

    ```python
    报名.name[(实参, ...)]
    ```

##### 安装第三方模块

```python
pip install module
```

### 类简介

##### 概述

* 类对象

    类对象是对一些具有相同特征或相同行为的事物的一个统称，是一个抽象的事物，并且本身不可以被直接使用。

* 实例化对象

    实例化对象是类对象实例化的一个具体存在。

##### 设计

* 类名

* 类属性

* 类方法

##### 创建

```python
class 类名(object):
    """文档字符串注释"""
    def 方法名(self, 形参, ...):
        ...
```

##### 添加属性、方法

* 添加属性

    ```python
    对象.新属性名 = 新属性值
    ```

* 添加方法

    ```python
    def 方法名(self, 形参, ...):
      ...
    
    import types
  
    对象.方法名 = types.MethodType(方法名, 对象)
    ```

##### 访问属性、方法

```python
对象.属性名/方法名(实参, ...)
```

##### 修改属性

* 通过对象进行修改

    ```python
    对象.属性名 = 新属性值
    ```

* 通过类方法进行修改

    ```python
    def 方法名(self, 形参):
      ...
      self.属性 = 形参
    ```

##### 删除属性、方法

```python
del 对象.属性名/方法名
```

### 继承

##### 优点

1. 提高代码的健壮性和安全性；

2. 简化代码，减少冗余。

##### 缺点

耦合性高，内聚性低。

##### 继承

* 单继承

    ```python
    class 子类名(父类名):
      """文档字符串的注释"""
      def __init__(self, 形参, ..., 形参n):
          super(self, 子类名).__init__(形参m, ...)
          ...
    ```

* 多继承

    ```python
    class 子类名(父类名, ...):
      """文档字符串的注释"""
      def __init__(self, 形参, ...):
          父类名.__init__(self, 形参m, ...)
          ...
    ```

### 类的其他知识点

##### 类属性、类方法、静态方法

```python
class 类名:
    属性名 = 属性值
    @classmethod
    def 方法名(self, 形参, ...):
        ...
    
    @staticmethod
    def 方法名(形参, ...):
        ...
```

##### 私有属性的访问、修改、删除和约定私有化

```python
class 类名(object):
    def __init__(self, 形参, 形参1):
        self._属性名 = 形参
        self.__属性名 = 形参1
    @property
    def 属性名(self):
        ...
        return self.__属性名
    
    @属性名.setter
    def 属性名(self, 形参):
        ...
        self.__属性名 = 形参
        
    @属性名.deleter
    def 属性名(self):
        ...
        del self.__属性名
```

##### 面向过程和面向对象

* 面向过程

    由上而下，逐步求精。

* 面向对象(OOP)
    
    * 特点
    
        封装、继承、多态。
    
### 高阶函数

##### `map`

```python
map(函数名, 序列)
```

##### `reduce`

```python
import functools

functools.reduce(函数名, 序列)
```

##### `filter`

```python
filter(函数名, 序列)
```

##### `sorted`

```python
sorted(序列, key=函数名[, reverse=True/False])
```

##### `zip`

```python
zip(序列, 序列)
```

##### `enumerate`

```python
enumerate(序列)
```

### 正则表达式

##### 概述

正则表达式是用来描述字符排列和匹配模式的语法规则，主要用来对字符串进行分隔、匹配、查找和替换。

##### 常用字符

`/` `\` `^、\A` `$、\Z` `*` `+` `?` `{m,n}` `.` `[...]` `[^...]` `\b` `\B` `(?=...)` `(?!...)` `(?<=...)` `(?<!...)` `\d` `\D` `\f` `\r` `\n` `\t` `\v` `\s` `\S` `\w` `\W` `(...)` `(?p<name>...)` `(?P=name)` `\number`

##### 常用修饰符

```python
re.I
re.S
re.M
```

##### 常用方法

```python
import re

re.compile(pattern, flags)
search/match(str[, pos, endpos])
Match对象.group()/group("name"/number)/group("name"/number, ...)/groups()/span()/start()/end()
findall(str[, pos, endpos])
sub/subn(str, repl[, count])
def 函数名(matched):
    ...
split(str[, maxsplit])
```

### 闭包、列表生成式、列表生成器和字典生成式

##### 闭包

* 概述

    闭包是一个引用了定义在函数体内的变量，并且可以在其定义环境之外被执行的函数。

* 优点

    1. 避免污染全局环境；
    
    2. 函数体外可以调用定义在函数体内的变量。

* 缺点

    数据长期驻留在内存中，造成了内存的极大浪费。

##### 列表生成式

* 单层循环列表生成式

    ```python
    [变量名 循环 [判断 ...]]
    ```

* 多层循环列表生成式

    ```python
    [变量名 运算符 变量名 ... 循环 ... [判断 ...]]
    ```

##### 列表生成器

* 概述

    列表生成器与列表生成式类似，用`()`来表示。

* 特点

    可以被`next()`方法不断调用，并且返回下一个值。

##### 字典生成式

```python
{k:v for k, v in zip(序列, 序列)}
```

### 内建函数和工厂函数

##### 内建函数

* 概述

    内建函数(BIF)是Python的内置函数。

* 特点

    1. 内建函数都是功能性函数；
    
    2. 内建函数的类型都是`<class 'builtin_function_or_method''>`。

##### 工厂函数

* 概述

    工厂函数是一些特殊的内建函数。

* 特点

    1. 工厂函数都是类型转换型函数；
    
    2. 工厂函数的类型都是`<class 'type''>`。