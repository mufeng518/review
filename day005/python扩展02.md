### 装饰器

##### 概述

装饰器是通过闭包来实现的，而闭包是通过函数特性来实现的。

> 释：
>
> `@`的作用是把被装饰得函数作为参数传递到装饰函数中，并执行该装饰函数。
>
> 注：
>
> 当装饰函数时，如果想要保留被装饰函数的函数名称和文档字符串，那么可以通过`functools`模块中的`@wraps(func)`来实现。

##### 函数装饰器

* 装饰普通函数

    ```python
    def funcName(形参1, ...):
        ...
        def deco(func):
            ...
            @wraps(func)
            def deco_func(*args, **kwargs):
                ...
            return deco_func
        return deco
    ```

* 装饰类方法

    ```python
    def funcName(形参1, ...):
        ...
        def deco(func):
            ...
            @wraps(func)
            def deco_func(self, *args, **kwargs):
                ...
            return deco_func
        return deco
    ```

##### 类装饰器

```python
class deco:
    def __init__(self, func):
        self._func = func

    def __call__(*args, **kwrags):
        ...
```

##### 类方法装饰器

```python
class 类名:
    def funcName(self, 形参1, ...):
        ...
        def deco(func):
            ...
            return self._deco_func(*args, **kwargs)
        return deco

    def _deco_func(*args, **kwargs):
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
[变量名 = ]lambda 形参1, ...: expression
```

##### 使用

```python
变量名(实参1, ...)
(匿名函数)(实参1, ...)
```

### 异常处理

##### 自定义异常类型

```python
class 自定义异常类型类名(Expression):
    def __init__(self):
        super(自定义异常类型类名, self).__init__(异常信息)
```

##### 主动抛出异常

```python
raise 异常类型类名
```

### 生成器

##### 概念

生成器(`generator`)是一个使用了`yield`的函数。

> 注：
>
> 生成器的返回值是一个迭代器。

##### 创建

```python
def 函数名(形参1, ...):
    ...
    temp_data = yield expression
    ...
```

##### 常用方法

```python
.send(实参1, ...)
.throw(异常类型类名)
.close()
```

### `logging`模块

##### 日志级别说明

```python
NOTSET 0 不设置
DEBUG 10 输出调试信息
INFO 20 输出常规信息
WARNING 30 输出事件信息
ERROR 40 输出程序报错信息
CRITICAL 50 输出系统故障信息
```

##### 日志格式说明

```python
%(asctime)s
%(name)s
%(levelno)s
%(levelname)s
%(pathname)s
%(filename)s
%(funcName)s
%(lineno)s
%(process)d
%(processName)s
%(thread)d
%(threadName)s
%(message)s
```

##### 创建默认`logger`

```python
import logging
logging.basicConfig(level, filename, filemod, format, datefmt)
logger = logging.getLogger(name)
```

##### 创建自定义`logger`

* 定义`Formatter`对象

    ```python
    formatter = logging.Formatter(fmt, datefmt)
    ```

* 定义`Filter`对象

    ```python
    _filter = logging.Filter(name)
    ```

* 定义`StreamHandler`，并设置日志级别、`Formatter`和添加`Filter`

    ```python
    stream_handler = logging.StreamHandler()
    stream_handler.setLevel(logging.DEBUG/INFO/WARNING/ERROR/CRITICAL)
    stream_handler.setFormatter(formatter)
    stream_handler.addFilter(_filter)
    ```

* 定义`FileHandler`，并设置日志级别、`Formatter`和添加`Filter`

    * 文件不拆分定义

        ```python
        file_handler = logging.FileHandler(filename, encoding)
        ```

    * 文件拆分定义

        * 按字节

            ```python
            from logging.handlers import RotatingFileHandler

            file_handler = RotatingFileHandler(filename, encoding, maxBytes, backupCount)
            ```

        * 按时间

            ```python
            from logging.handlers import TimeRotatingFileHandler

            file_handler = TimeRotatingFileHandler(filename, encoding, when="d/h/m/s", interval, backupCount)
            ```
        
        * 设置日志级别、`Formatter`和添加`Filter`

            ```python
            file_handler.setLevel(logging.DEBUG/INFO/WARNING/ERROR/CRITICAL)
            file_handler.setFormatter(formatter)
            file_handler.addFilter(_filter)
            ```

* 获取`Logger`对象，并设置日志级别、添加`Filter`和`Handler`

    ```python
    logger = logging.getLogger(name)
    logger.setLevel(logging.DEBUG/INFO/WARNING/ERROR/CRITICAL)
    logger.addFilter(_filter)
    logger.addHandler(stream_handler/file_handler)
    ```

##### 通过`dict`来创建`logger`

* `dict`结构

    ```python
    {
        "version": 1,
        "disable_exists_loggers": True/False,
        "formatters": {
            "formatter1": {
                "format": ...,
                "datefmt": ...
            },
            ...
        },
        "filters": {
            "filter1": {
                "name": ...
            },
            ...
        },
        "handlers": {
            "stream_handler": {
                "level": logging.DEBUG/INFO/WARNING/CRITICAL,
                "formatter": ...,
                "filters": [...]
            },
            ...
        },
        "loggers": {
            "logger1": {
                "level": logging.DEBUG/INFO/WARNING/CRITICAL,
                "filters": [...],
                "handlers": [...],
                "propagation": True/False
            }
        }
    }
    ```

* 使用

    ```python
    import logging.dict

    logging.dict.dictConfig(config)
    logger = logging.getLogger(name)
    ```

##### 捕获异常信息

```python
logger.error(异常信息, exc_info=True)
```