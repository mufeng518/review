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

字符串是用英文状态下的单引号或双引号括起来的任意文本。

##### 访问

* 单个字符

    ```python
    str[索引]
    ```
  
    > 注：
    >
    > 索引默认为从`0`开始。

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
    str1 + ...
    ```

* 重复

    ```python
    str1 * 数字
    ```

##### 大小比较

从字符串中的第一个字符开始比较，谁的ASCII值比较大谁就大，如果相等，那么继续比较下一个字符，以此类推。

> 注：
>
> 当字符串中的下一个字符不存在时，那么默认为下一个字符为`\0`。

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
    .center(width[, fillchar])
    .ljust(width[, fillchar])
    .rjust(width[, fillchar])
    .zfill(width)
    ```

* 修改字符串中字母的大小写

    ```python
    .capitablize/title/lower/upper/swapcase()
    ```

* 判断字符串中的字符

    ```python
    .istitle/isupper/islower/isdigit/isalpha/isalnum/isspace()
    ```

* 统计指定子字符串在给定范围的原字符串中出现的次数

    ```python
    .count(子字符串变量名[, start, end])
    ```

* 判断指定子字符串是否存在于给定范围的原字符串中，如果存在，那么返回该子字符串在原字符串中第一次出现的位置索引(与`start`无关)，如果不存在，那么返回-1

    ```python
    .find/rfind(子字符串变量名[, start, end])
    .index/rindex(子字符串变量名[, start, end])
    ```

* 判断指定子字符串是否存在于给定范围的原字符串中的给定位置

    ```python
    .startswith/endswith(子字符串变量名[start, end])
    ```

* 字符串的编码和解码

    ```python
    .encode/decode(encoding[, errors="ignore"])
    ```

* 删除字符串中的指定字符

    ```python
    .trim/ltrim/rtrim([char])
    ```

### 列表

##### 概念

列表是由一系列按特定顺序排列的元素(是列表中的每一个值)组成的序列，用`[]`来表示，元素间用`,`号进行分隔。

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
  
    > 注：
    >
    > 新元素可以是任意数据类型的数据。                                                 

* 多个元素

    ```python
    list[[start]:[end][:step]] = 新元素序列
    ```
  
    > 注：
    >
    > 当`step=1`时，那么添加的新元素数量可以和修改数量不同。

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
        .append(新元素)
        .insert(索引, 新元素)
        ```

    * 多个元素
    
        ```python
        .extend(新元素序列)
        ```

* 排序

    ```python
    .sort([reverse=True/False])
    .reverse()
    ```

* 删除

    * 单个元素
    
        ```python
        .pop([索引])
        .remove(元素)
        del list[索引]
        ```

    * 多个元素
    
        ```python
        .clear()
        del list[[start]:[end][:step]]
        del list
        ```

* 计算列表中元素的个数

    ```python
    len(list)
    ```

* 统计指定元素在列表中出现的次数

    ```python
    .count(元素)
    ```

* 判断指定元素是否存在于给定范围的列表中，如果存在，那么该元素在列表中第一次出现的位置索引(与`start`无关)，如果不存在，那么程序将会报错

    ```python
    .index(元素[, start, end])
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

元组和列表类似，用`()`来表示，并且元组是不可变的，而列表是可变的，如果要修改元组中的部分元素，那么只能重新定义该元组。

##### 创建

```python
变量名 = ()/tuple()
```

> 注：
>
> 当元组中只包含一个元素时，那么必须在该元素之后添加英文状态下的`,`。

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

字典是由键值对组成的序列，在字典中查找数据的速度极快，但占用空间大，内存浪费多。

##### 键的数据类型

键的数据类型只能是数字、字符串或元组。

##### 创建

```python
变量名 = {}/dict(key1=value1, ...)
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
```

> 附：
>
> ```python
> dict.get(key[, default])
> ```

##### 修改

```python
dict[key] = newValue
```

##### 删除

* 单个键值对

    ```python
    dict.popitem()
    dict.pop(key)
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

集合类似于字典，是由一系列无序且无重复的元素组成的序列。

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
    set(字符串/列表/元组/字典变量)
    ```
  
    > 注：
    >
    > `set`方法会自动过滤掉重复的元素。

### 可迭代对象和迭代器

##### 可迭代对象

* 概念

    可迭代对象是可以直接被用于`for`循环的对象。

* 分类

    * 容器类型对象
    
        字符串、列表、元组、字典、集合。
    
    * `Generator`
    
        生成器或带有`yield`的`generator function`。

##### 迭代器

* 概念

    迭代器是可以被`next()`方法不断调用，并且返回下一个值的对象。

* 生成

    ```python
    iter(object[, sentinel])
    ```
  
    > 注：
    >
    > 当`sentinel`省略时，那么`object`必须是一个容器类型对象，当`sentinel`存在时，那么`object`必须是一个可调用对象，例如函数名，此时只有当`object`的返回值和`sentinel`值相同时，那么迭代才会结束。

##### 判断数据类型

* 单种数据类型判断

    ```python
    isinstance(object, 数据类型)
    ```

* 多种数据类型判断

    ```python
    isinstance(object, (数据类型1, ...))
    ```

### 函数

##### 本质

函数实际上是对一些功能的封装。

##### 创建

```python
def 函数名(形参1, ...):
    """问当字符串的注释"""
    ...
    return ...
```

##### 缺省参数

缺省参数是一个拥有默认值的参数。

##### 传递实参

* 位置传参

    ```python
    函数名(实参1, ...)
    ```

* 关键字传参

    ```python
    函数名(形参1=实参1, ...)
    ```

### 变量进阶

##### 不可变数据类型和可变数据类型

* 不可变数据类型

    不可变数据类型是内存中的数据不允许被修改，例如字符串、数字、布尔值、`None`或元组。

* 可变数据类型

    可变数据类型是内存中的数据允许被修改，例如列表、字典或集合。

##### 局部变量

局部变量是定义在函数体内的变量，只可以在该函数体内使用。

##### 全局变量

全局变量是定义在函数体外的变量，可以在整个包或包外使用。

##### 形式参数

形式参数是定义函数时使用的变量，只可以在该函数体内使用。

> 注：
>
> 形式参数也属于局部变量。

##### 函数体内调用变量原理

当调用函数时，那么程序首先会在局部变量中查找该变量，如果存在，那么调用该局部变量，如果不存在，那么程序会继续在全局变量中查找该变量，如果存在，那么调用该全局变量，如果不存在，那么程序将会报错。

##### 函数体内修改全局变量

* 全局变量是可变数据类型

    直接在函数体内修改。
    
* 全局变量是不可变数据类型

    通过使用`global 全局变量名`来进行修改。

### 递归函数

##### 概念

递归函数是一个调用自身的函数。

##### 设计

1. 写出临界条件；

2. 找出这一次与上一次的关系。

##### 深度遍历和广度遍历

* 深度遍历

    递归实现

* 广度遍历

    队列实现