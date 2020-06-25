### 函数

##### 本质

函数实际上是对一些功能的封装。

##### 创建

```python
def 函数名(形参1, ...):
    """文档字符串的注释"""
    ...
    return ...
```

##### 缺省参数

缺省参数是一个拥有默认值的形参。

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

    不可变数据类型是内存中的数据不允许被修改，例如整数、浮点数、复数、字符串、`bool`、`None`和元组。

* 可变数据类型

    可变的数据类型是内存中的数据允许被修改，例如列表、字典和集合。

##### 局部变量

局部变量是定义在函数体内的变量，只可以在该函数体内使用。

##### 全局变量

全局变量是定义在函数体外的变量，可以在整个包或包外使用。

##### 形式参数

形式参数是定义函数时使用的变量。

##### 函数体内调用变量原理

当调用函数时，那么系统首先会在局部变量中查找该变量，如果存在，那么调用该局部变量，如果不存在，那么程序会继续在全局变量中查找该变量，如果存在，那么调用该全局变量，如果不存在，那么程序将会报错。

##### 函数体内修改全局变量

* 全局变量是可变数据类型

    直接在函数体内修改。
    
* 全局变量是不可变数据类型

    通过`global 变量名`来修改。

### 递归函数

##### 概念

递归函数是一个调用自身的函数。

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

```python
open(file, mode[, encoding, errors])
```

##### `.txt`文件处理

* 读取

    ```python
    with open(file, mode="r"[, encoding, errors]) as file_object:
      contents = file_object.read([字符长度])
      line = file_object.readline([字符长度])
      lines = file_object.readlines()
    ```

* 写入

    ```python
    with open(file, mode="w"[, encoding, errors]) as file_object:
      file_object.write("内容")
    ```
  
    注：
    
    Python只能直接将字符串写入到文本文件中。
    
    附：
    
    ```python
    import pickle
    
    with open(file, mode="rb"[, encoding, errors]) as file_object:
      contents = pickle.load(file_object)
  
    with open(file, mode="wb"[, encoding, errors]) as file_object:
      pickle.dump(内容, file_object)
    ```

##### `.json`文件处理

* 读取
    
    ```python
    import json
    
    with open(file, mode="r"[, encoding, errors]) as file_object:
      contents = json.load(file_object)
    ```

* 写入

    ```python
    import json
    
    with open(file, mode=""w[, encoding, errors]) as file_object:
      json.dump(内容, file_object)
    ```

##### `.csv`文件处理

* 读取

    ```python
    import csv
    
    with open(file, mode="r"[, encoding, errors]) as file_object:
      reader = csv.reader(file_object)
      for row in reader:
          ...
    ```

* 写入

    ```python
    import csv
    
    with open(file, mode="r"[, encoding, errors]) as file_object:
      writer = csv.writer(file_object)
      writer.writerow(data)
    ```

### `os`模块

##### 概述

`os`模块是一个包含操作系统功能的模块。

##### `os`

```python
os.name
os.environ
os.uname()
os.mkdir(path)
os.listdir([path])
os.stat(path)
os.path.getsize(path)
os.rename(path, newPath)
os.rmdir(path)
os.remove(path)
os.curdir
os.getwd()
os.system("...")
```

##### `os.path`

```python
os.path.abspath(相对路径)
os.path.join(path1, ...)
os.path.split(path)
os.path.dirname(path)
os.path.basename(path)
os.path.splitext(path)
os.path.isdir(path)
os.path.isfile(path)
os.path.exists(path)
```

### 模块

##### 概述

模块是一个可执行的程序文件。

##### 优点

* 提高代码的可维护性

* 提高代码的复用度

* 避免程序中的变量名和函数名冲突。

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
    from module import name [as 别名], ...
    ```

* 引入模块中所有的变量名、函数名或类名

    ```python
    from module import *
    ```

### 包

##### 概述

为了解决模块命名的冲突，引入了按目录来组织模块的方法，其中目录(该目录中必须包含一个`__init__.py`文件)被称为包。

##### 特点

引入了包以后，只要顶层的包不发生冲突，那么包中的模块也不会发生冲突。

##### 结构

* 引入包

    ```python
    from .module import name1, ...
    ...
    ```

* 导入包

    ```python
    import 包名
    ```

* 使用

    ```python
    包名.name[(实参1, ...)]
    ```

##### 安装第三方模块

```python
pip install module
```

### 类简介

##### 概述

* 类对象

    类也被称为类对象，它是对一些拥有相同特征或相同行为的事物的一个统称，是一个抽象的事物，并且本身不能被直接使用。

* 实例化对象

    实例化对象是类对象实例化的一个具体存在。

##### 设计

* 类名

* 属性

* 方法

##### 创建

```python
class 类名(object):
    """文档字符串的注释"""
    def 方法名(self, 形参1, ...):
        ...
```

##### 添加属性、方法

* 添加属性

    ```python
    对象.属性名
    ```

* 添加方法

    ```python
    import types
  
    def 方法名(self, 形参1, ...):
      ...
    对象.方法名 = types.MethodType(方法名, 对象)
    ```

##### 访问属性、方法

```python
对象.属性名/方法名(实参1, ...)
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
      self.属性名 = 形参
    ```

##### 删除属性、方法

```python
del 对象.属性名/方法名
```

### 继承

##### 优点

* 简化代码，减少冗余

* 提高代码的健壮性和安全性

##### 缺点

耦合性高，内聚性低

##### 继承

* 单继承

    ```python
    class 子类名(父类名):
      def __init__(self, 形参1, ...):
          super(子类名, self).__init__(形参m, ...)
          ...
      ...
    ```

* 多继承

    ```python
    class 子类名(父类名1, ...):
      def __init__(self, 形参1, ...):
          父类名1.__init__(self, 形参m, ...)
          ...
      ...
    ```

### 类的其他知识点

##### 类属性、类方法、静态方法

```python
class 类名(object):
    属性名1 = 属性值1
    ...
    @classmethod
    def 方法名(cls, 形参1, ...):
        ...
    
    @staticmethod
    def 方法名(形参1, ...):
        ...
```

##### 私有属性的访问、修改、删除和约定私有化

```python
class 类名(object):
    def __init__(self, 形参):
        self.__属性名 = 形参

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

    由上而下，逐渐求精。

* 面向对象(OOP)
    
    * 特点
    
        封装、继承和多态。
    
### 高阶函数

##### `map`

```python
map(函数名, 序列)
```

##### `reduce`

```python
from functools import reduce

reduce(函数名, 序列)
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
zip(序列1, 序列2)
```

##### `enumerate`

```python
enumerate(序列)
```

### 正则表达式

##### 概述

正则表达式是一个用来描述字符排列和匹配模式的语法规则，主要用来对字符串进行切割、查找、匹配或替换等。

##### 常用字符

`/` `\` `\A、^` `\Z、$` `*` `+` `?` `{m,n}` `.` `[...]` `[^...]` `\b` `\B` `(?=...)` `(?!...)` `(?<=...)` `(?<!...)` `\d` `\D` `\w` `\W` `\s` `\S` `\f` `\r` `\n` `\t` `\v` `(...)` `(?P<name>...)` `(?P=name)` `\number` 

##### 常用修饰符

`re.I` `re.M` `re.S`

##### 常用方法

```python
re.compile(pattern[, flags])
match/search("子字符串"[, pos, endpos])
Match对象.group()/group(name/number)/group(name1/number1, ...)/groups()/span()/start()/end()
findall("子字符串"[, pos, endpos])
sub/subn("子字符串", repl[, count])
def 函数名(matched):
    ...
split("子字符串"[, maxsplit])
```

### 闭包、列表生成式、列表生成器和字典生成式

##### 闭包

* 概述

    闭包是一个引用了定义在函数体外的变量，并且可以在其定义环境之外被执行的函数。

* 优点

    1. 避免污染全局环境；
    
    2. 可以在函数体外调用定义在函数体内的变量。

* 缺点
    
    占用内存空间，造成了内存的极大浪费。

##### 列表生成式

* 单层循环列表生成式

    ```python
    [变量名 for 变量名 in 序列 [if 条件语句 ...]]
    ```

* 多层循环列表生成式

    ```python
    [变量名1 运算符 变量名2 ... for 变量名1 in 序列 ... [if 条件语句 ...]]
    ```

##### 列表生成器

* 概述

    列表生成器与列表生成式类似，只需将`[]`换成`()`即可。

* 特点

    可以被`next()`方法不断调用，并且返回下一个值。

##### 字典生成式

```python
{k: v for k, v in zip(序列1, 序列2)}
```

### 内建函数和工厂函数

##### 内建函数

* 概述

    内建函数(BIF)是`built_in_function`的简称，是Python的内置函数。

* 特点

    * 内建函数都是功能性函数。
    
    * 内建函数的类型都是`<class 'builtin_function_or_method'>`。

##### 工厂函数

* 概述

    工厂函数是一些特殊的内建函数。

* 特点

    * 工厂函数都是类型转换型函数。
    
    * 工厂函数的类型都是`<class 'type'>`。