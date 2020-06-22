### 初始Python

##### 简介

1. Python的创始人是吉多·范罗苏姆，曾经参与了ABC(不开源)的设计；

2. Python中最常用的集成开发环境之一：Pycharm；

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

* 代码执行效率低

* 代码不能加密

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

* 编译性语言编写的程序在执行之前需要一个专门的编译过程，先将程序编译成一个机器语言的文件，当程序执行时，那么不再需要对程序重新编译，只需要执行编译的结果就行了；

* 解释性语言编写的程序不需要预先编译，并且是以文本的方式存储程序代码，当程序执行时，会将代码一句一句地直接执行(先解释后执行)。

> 注：
>
> 1. 编译性语言编写的程序代码执行效率高，但跨平台性差；解释性语言编写的程序代码执行效率低，但跨平台性好；
>
> 2. 编译性语言和解释性语言的编译时间点不同。

### 内存

##### 概念

内存也被称为内存储器，是计算机中最重要的部件之一(计算机中所有程序的执行都是在内存中进行的)，并且它是计算机与CPU进行沟通的桥梁。

##### 作用

主要用于暂时存储CPU中运算的数据，以及与硬盘等外部存储器进行交换的数据。

##### 单位换算

Bit Byte Kb Mb Gb Tb
8   1024 1  1  1  1

##### 常用进制

* 二进制(B)

* 八进制(Q)

* 十进制(D)

* 十六进制(H)

    主要用于表示内存地址。

##### 进制间的转换

### 数据存储

##### 概念

计算机存储数据时，先开辟内存空间(计算机开辟内存空间的最小计量单位是1Byte)，再存储数据(计算机存储数据时，用最高位标识符号，`0`表示正数，`1`表示负数，存储的是数据的二进制补码)。

##### 原码、反码和补码

* 原码

    规定了字节数，写明了符号位。

* 反码

    正数的反码是其原码，负数的反码是其原码的符号位不变，其他位取反。

* 补码

    正数的补码是其原码，负数的补码是其原码的反码再加1。
    
    > 附：负数的补码技巧
    >
    > 符号位不变，从最低位开始，再遇见第一个`1`之前什么都不变，遇见第一个`1`时，保留这个`1`，之后按位取反。
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
    > 相对路径：不是从更目录开始链接的路径。

### 输入、打印和注释

##### 输入

```python
input("提示信息")
```

##### 打印

* 打印单条信息

    ```python
    print(信息[, end])
    ```

* 打印多条信息

    ```python
    print(信息1, ...)
    ```

* 打印多行信息

    ```python
    print("""
    信息
    """)
    # 或
    pring('''
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

    `int` `float` 复数 `bool`

* 非数字类型

    `string` `None` `list` `tuple` `dict` `set`

##### 标识符

* 概念

    标识符是一串字符串。

* 书写规则

    1. 首字符必须是字母或下划线，其他字符可以是数字、字母或下划线；
    
    2. 不允许是Python关键字；
    
        > 附：查看Python关键字
        >
        > ```python
        > import keyword
        > 
        > keyword.kwlist
        > ```

    3. 区分大小写。

* 作用

    主要用于给变量、函数或类等命名。

### 变量和常量

##### 变量

* 概念

    变量是程序执行期间可操作的存储空间的名称，并且是程序执行期间可以改变的数据。

* 作用

    主要用于将不同类型的数据存储到内存。

* 定义

    * 单一赋值
    
        ```python
        变量名 = 值
        ```
    
    * 对称赋值
    
        ```python
        变量名1, ... = 值1, .../字符串/列表/元组/字典/集合变量
        ```
    
    * 统一赋值
    
        ```python
        变量名1 = ... = 值
        ```

* 查看变量的类型和地址

    ```python
    type(变量名)
    id(变量名)
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
    str(数值/bool/列表/元组/字典/集合)
    ```

##### 常用数学函数

```python
max/min(数值1, .../字符串/(字符串或)数值列表/元组/字典/集合变量)
sum(数值列表)
pow(数值, n次方)
abs(数值)
round(数值, 保留小数位数)
range([start, ]end[, step])
```

```python
import math

math.ceil/floor(数值)
math.sqrt(数值)
math.modf(数值)
```

```python
import random

random.random()
random.uniform(start, end)
random.randint(start, end)
random.randrange([start, ]end[, step])
random.choice(字符串/列表/元组变量)
random.shuffle(列表变量)
```

### 常用运算符

##### 算术运算符

```python
+
-
*
/
//
**
%
```

##### 赋值运算符

```python
=
```

##### 复合运算符

```python
+=
-=
*=
/=
//=
**=
%=
```

##### 比较运算符

```python
==
!=
>
>=
<
<=
```

##### 逻辑运算符

```python
and
or
not 布尔表达式
```

##### 成员运算符

```python
in
not in
```

##### 身份运算符

```python
is
is not
```

##### 位运算符

```python
&
|
^
~
<<
>>
```

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
    (变量名 = )条件语句为True时返回的值 if 条件语句 else 条件语句为False时返回的值
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
  
    附：
    
    ```python
    for语句/while语句:
      ...
      if 条件语句:
          continue/break
      ...
    ```

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

字符串是用英文状态下的单引号或双引号括起来的任意字符串。

##### 访问

* 单个字符

    ```python
    str[索引]
    ```

* 多个字符

    ```python
    str[[start]:[ end][: step]]
    ```

##### 复制

```python
变量名 = str[索引]/str[[start]:[ end][: step]]
```

##### 拼接和重复

* 拼接

    ```python
    str1 + ...
    ```

* 重复

    ```python
    str * 数字
    ```

##### 大小比较

从字符串中的第一个字符开始比较，谁的ASCII码值比较大谁就大，如果相等，那么继续比较下一个字符，以此类推。

> 注：
>
> 当下一个字符不存在时，那么默认为下一个字符为`\0`。

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
    str.center/ljust/rjust/zfill(width[, fillchar])
    ```

* 修改字符串中字母的大小写

    ```python
    str.capitalize/title/upper/lower/swapcase()
    ```

* 判断字符串中的字符

    ```python
    str.istitle/isupper/islower/isdigit/isalpha/isalnum/isspace()
    ```

* 统计指定子字符串在给定范围的原字符串中出现的次数

    ```python
    str.count("子字符串"[, start, end])
    ```

* 判断指定子字符串是否存在于给定范围的原字符串中，如果存在，那么返回该子字符串在原字符串中第一次出现的位置索引(与`start`无关)，如果不存在，那么返回-1

    ```python
    str.find/rfind/index/rindex("子字符串"[, start, end])
    ```

* 判断指定子字符串是否存在于给定范围的原字符串中的给定位置

    ```python
    str.startswith/endswith("子字符串"[, start, end])
    ```

* 字符串的编码和解码

    ```python
    str.encode/decode(encoding[, errors="ignore"])
    ```

* 删除字符串中的指定字符

    ```python
    str.strip/rstrip/lstrip([char])
    ```

### 列表

##### 概念

列表是由一系列按特定顺序排列的元素组成的序列，用`[]`来表示，元素间用`,`进行分隔。

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
    list[[start]:[ end][: step]]
    ```

##### 复制

```python
变量名 = list[索引]/list[[start]:[ end][: step]]
```

##### 修改

* 单个元素

    ```python
    list[索引] = 新元素
    ```

* 多个元素

    ```python
    list[[start]:[ end][: step]] = 新元素序列
    ```

##### 拼接和重复

* 拼接

    ```python
    list1 + ...
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
    list.index(元素)
    ```

* 浅拷贝和深拷贝

    ```python
    import copy
  
    变量名 = copy.copy/deepcopy(list)
    ```

* 数据类型间的转换

    * 转换成列表
    
        ```python
        list(字符串/元组/字典/集合变量名)
        ```
    
    * 转换成字符串
    
        ```python
        "分隔符".join(列表/元组/字典/集合变量)
        ```
    
### 元组

##### 概念

远足与列表类似，用`()`来表示，并且元组是不可变的，而列表是可变的，所以当需要修改元组中的部分元素时，那么必须重新定义该元组。

##### 创建

```python
变量名 = ()/tuple()
```

> 注：
>
> 当元组中只含有一个元素时，那么必须在该元素之后添加`,`。

##### 访问、复制、拼接和重复

和`list`的一样

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

字典是由一系列键值对组成的序列，在字典中查找数据的速度极快，但占用空间大，内存浪费多。

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
dict.get(key[. default])
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

集合类似于字典，是由一系列无需且无重复的元素组成的序列。

##### 创建

```python
变量名 = set(字符串/列表/元组/字典变量名)
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

    可迭代对象是直接可以被用于`for`循环的对象。

* 分类

    * 容器对象
    
    * `generator`对象

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
    isinstance(object, (数据类型1, ...))
    ```