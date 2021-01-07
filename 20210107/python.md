### 魔术方法

##### 对象

* `__new__(cls, *args, **kwargs)`

    当实例化对象时，那么该方法会自动被调用。
    
    > 注：
    >
    > 返回值必须是`super().__new__(cls, *args, **kwargs)`
    
* `__init__(self, 形参, ...)`
    
    当初始化对象时，那么该方法会自动被调用。
    
* `__del__(self)`

    当对象被销毁时，那么该方法会自动被调用。

##### 功能

* `__len__(self)`
    
    当`len(对象)`时，那么该方法会自动被调用。
    
    > 注：
    >
    > 返回值必须是`int`类型。
    
* `__call__(self, 形参, ...)`

    当`对象(实参, ...)`时，那么该方法会自动被调用。
    
* `__str__(self)`

    当`print(对象)`时，那么该方法会自动被调用。
    
    > 注：
    >
    > 返回值必须是`str`类型。
    
* `__repr__(self)`

    当在Python解释器里直接输入对象并回车时，那么该方法会自动被调用。
    
    > 注：
    >
    > 返回值必须是`str`类型。

##### 迭代

* `__iter__(self)`

    当声明对象为可迭代对象时，那么该方法会自动被调用。
    
    > 注：
    >
    > 返回值必须是`self`。
    
* `__next__(self)`

    当对象被用于`for`循环或`next(对象)`时，那么该方法会自动被调用。

##### 属性

* `__setitem__(self, item, value)`

    当以`对象/self[item] = vlaue`的形式来设置对象属性时，那么该方法会自动被调用。
    
* `__getitem__(self, item)`

    当以`对象/self[item]`的形式来访问对象属性时，那么该方法会自动被调用。
    
    > 注：
    >
    > 此处的`item`可以是`int`、`str`或`slice`对象。
    
* `__delitem__[self, item]`

    当以`del 对象/self[item]`的形式来删除对象属性时，那么该方法会自动被调用。
    
    
* `__setattr__(self, attr, value)`

    当以`对象/self.attr = value`的形式来设置对象属性时，那么该方法会自动被调用。
    
* `__getattr__(self, attr)`

    当以`对象/self.attr`的形式来访问对象不存在的属性时，那么该方法会自动被调用。
    
* `__delattr__(self, attr)`

    当以`del 对象/self.attr`的形式来删除对象属性时，那么该方法会自动被调用。

##### 上下文

* `__enter__(self)`

    当`with`后面紧跟的语句被执行时，那么该方法会自动被调用。
    
    > 注：
    >
    > 返回值必须是`self`。
    
* `__exit__(self, type, value, trace)`

    当`with`代码块执行完毕或程序报错时注，那么该方法会自动被调用。

##### 算术运算

* `__add__/__sub__/__mul__/__div__/__pow__/__floordiv__/__mod__(self, other)`

    当对对象进行算术运算时，那么该方法会自动被调用。

##### 比较运算

* `__eq__/__ne__/__gt__/__ge__/__lt__/__le__(self, other)`

    当对对象进行比较运算时，那么该方法会自动被调用。

### 魔术属性

##### `obj.__dict__`

主要用于查看对象内部所有的属性名和属性值组成的字典。

> 注：
>
> 1. Python内置的数据类型是没有`__dict__`属性的；
>
> 2. 每一个类对象都有自己独有的`__dict__`属性，即使存在继承关系，也互不影响；
>
> 3. 每一个实例化对象也有`__dict__`属性，但如果存在继承关系，那么父子类共用`__dict__`属性；
>
> 4. 每一个模块也有自己的独有的`__dict__`属性。

##### `obj.__class__`

主要用于查看对象所在的类。

##### `[obj.]__name__`

主要用于查看对象的名称。

> 注：
>
> 当`obj`省略时，那么默认为返回的是`'__main__''。
>
> 延伸：
>
> 当一个模块被另一个模块引入时，如果不希望该模块中的部分代码被另一个模块所执行，那可以通过使用`__name__ == '__main__'`来进行限制。

### 辅助工具

##### `__slots__ = ("属性", ...)`

主要用于控制类属性的添加。

##### `__file__`

主要用于存储当前正处于运行状态的脚本的路径。

> 注：
>
> 当需要获取当前正处于运行状态的脚本的绝对路径时，那么最好通过`os.path.abspat(__file__)`来进行获取。

### 内置函数

##### 设置属性值

```python
setattr(object, 属性名, 属性值)
```

##### 获取属性值

```python
getattr(object, 属性名[, 默认值])
```

##### 判断对象是否拥有该属性

```python
hasattr(object, 属性名)
```

##### 判断可迭代对象中的元素是否全部为`True`

```python
all(iterable)
```

### 类型注解

##### 基本结构

* 变量

    ```python
    变量名: 类型注解 = 值
    ```

* 函数

    ```python
    def 函数名(形参: 类型注解, ..., 形参: 类型注解 = 默认值) -> 返回值的类型注解:
      ...
    ```

##### 具体分类

* 基本类型注解

    `str` `int` `float` `bool` `None` `type` `Any`

* 复合类型注解

    `List[类型注解]` `Tuple[类型注解, ...]` `Sequence[类型注解]` `Iterable[类型注解]` `Dict[类型注解, 类型注解]` `Mapping[类型注解, 类型注解]`
    
    `Set[类型注解]` `Callable[[类型注解, ...], 类型注解]` `NoReturn` `Optional[类型注解] = None` `Union[类型注解, ...]` 

##### 类型注解的别名

```python
别名 = 类型注解
```

### `logging`模块

##### 日志级别说明

`NOTSET` 0 不设置

`DEBUG` 10 输出调试信息

`INFO` 20 输出常规信息

`WARNING` 30 输出事件信息

`ERROR` 40 输出程序异常信息

`CRITICAL` 50 输出系统故障信息

##### 日志格式说明

`%(name)s` `%(asctime)s` `%(levelname)s` `%(levelno)s` `%(pathname)s` `%(filename)s` `%(lineno)s` `%(process)s` `%(processName)s`

`%(thread)s` `%(threadName)s` `%(message)s`

##### 创建默认`logger`

```python
import logging

logging.basicConfig(level, format, datefmt, filename, filemode)
logger = logging.getLogger([name])
```

> 注：
>
> 当`name`省略时，那么默认为`name`为`root`。

##### 通过`dict`对象来创建`logger`

* `dict`结构

    ```python
    config = {
      "version": 1,
      "disable_exists_loggers": True/False,
      "formatters": {
          "formatter": {
              "class": "logging.Formatter",
              "format": "日志格式",
              "datefmt": "日志中的日期格式"
          },
          ...
      },
      "filters": {
          "filter": {
              "class": "logging.Filter",
              "name": "logger对象名"
          },
          ...
      },
      "handlers": {
          "stream_handler": {
              "class": "logging.StreamHandler",
              "formatter": "formatter",
              "filters": ["filter", ...],
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL"
          },
          "file_handler": {
              "class": "logging.FileHandler",
              "filename": "文件路径",
              "formatter": "formatter",
              "filters": ["filter", ...],
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL"
          },
          "byte_handler": {
              "class": "logging.handlers.RotatingFileHandler",
              "filename": "文件路径",
              "maxBytes": 最大字节数,
              "backupCount": 备份数量,
              "formatter": "formatter",
              "filters": ["filter", ...],
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL"
          },
          "time_handler": {
              "class": "logging.handlers.TimeRotatingFileHandler",
              "filename": "文件路径",
              "when": "D/H/M/S",
              "interval": 间隔,
              "backupCount": 备份数量,
              "formatter": "formatter",
              "filters": ["filter", ...],
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL"
          }
      },
      "loggers": {
          "logger": {
              "propagate": True/False,
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "handlers": ["handler", ...]
          },
          ...
      }
    }
    ```

* 使用

    ```python
    import logging.config
  
    logging.config.dictConfig(config)
    logger = logging.getLogger(name)
    ```

##### 捕获异常信息

```python
logger.error(异常信息, exc_info=True/False)
```

### 装饰器

##### 概述

装饰器是通过闭包来实现的，而闭包是通过函数特性来实现的。

##### `@`的作用

`@`的作用是把被装饰得函数作为参数传递到该装饰器中，并执行该装饰器函数。

> 注：
>
> 当需要保留原函数的函数名和文档字符串时，那么可以通过使用`functool`模块中的`@wraps(func)`来实现。

##### 函数装饰器

* 装饰普通函数

    ```python
    def funcName(形参, ...):
        ...
        def deco_func(func):
            ...
            def deco(*args, **kwargs):
                ...
            return deco
        return deco_func
    ```

* 装饰类方法

    ````python
    def funcName(形参, ...):
        ...
        def deco_func(func):
            ...
            def deco(self, *args, **kwargs):
                ...
            return deco
        return deco_func
    ```

##### 类装饰器

```python
class 类名:
    def __init__(self, func):
        self._func = func
    
    def __call__(self, *args, **kwargs):
        ...
```

##### 类方法装饰器

```python
class 类名:
    def funcName(self, 形参, ...):
        ...
        return self._deco_func
    
    def _deco_func(self, func):
        ...
        return self._deco
    
    def _deco(self, *args, **kwargs):
        ...
```

### 匿名函数

##### 概念

匿名函数是通过使用`lambda`来创建的函数。

##### 特点

1. 匿名函数只是一个简单的表达式，函数体比`def`简单；

2. 匿名函数只能封装一些简单的功能。

##### 创建

```python
变量名 = lambda 形参, ...:expression
```

##### 使用

```python
变量名(实参, ...)
```

### 异常处理

##### 自定义异常类型

```python
class 自定义异常类型类名(Exception):
    
    def __init__(self):
       super(自定义异常类型类名, self).__init__("异常信息")
```

##### 主动抛出异常

```python
raise 自定义异常类型类名
```

### `time`模块

##### 常用概念说明

* `UTC`

    `UTC`是`Universal Time Code`的简称，被称为格林威治时间，也被称为世界协调时或世界标准时间，对于中国来说是`UTC+8`。

* `DST`

    `DST`是`Daylight Saving Time`的简称，被称为夏令时，是一种为了节约能源而人为规定的时间制度，并且在夏季时调快一个小时。

##### 时间的表现形式

* 时间戳

    时间戳是以整数或浮点数的形式来表示的时间间隔。

* 时间元组

    时间元组是一个包含九个元素的数组，即`(year, month, day, hour, minute, second, weekday, julia day, flag)`
    
    > 释：
    >
    > `flag`: `-1` `0` `1`

* 格式化时间字符串

    `%Y` `%y` `%m` `%d` `%H` `%I` `%M` `%S` `%A` `%a` `%j`

##### 常用方法

```python
time.time()
time.gmtime([时间戳])
time.localtime([时间戳])
time.ctime([时间戳])
time.mktime(时间元组)
time.asctime(时间元组)
time.strftime("日期、时间格式"[, 时间元组])
time.strptime("格式化时间字符串"[, "日期、时间格式"])
time.sleep(秒数)
```