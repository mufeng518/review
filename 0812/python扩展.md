### `logging`模块

##### 日志级别说明

`NOTSET` 不设置

`DEBUG` 输出调试信息

`INFO` 输出常规信息

`WARNING` 输出事件信息

`ERROR` 输出代码异常信息

`CRITICAL` 输出系统故障信息

##### 日志格式说明

`%(name)s` `%(asctime)s` `%(levelname)s` `%(levelno)s` `%(pathname)s` `%(filename)s`

`%(lineno)s` `%(process)s` `%(processname)s` `%(thread)s` `%(threadname)s` `%(message)s`

##### 创建默认`logger`

```python
import logging

logging.basicConfig(level, formatt, datefmt, filename, filemode)
logging.getLogger(name)
```

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
              "datefmt": "日期格式"
          },
          ...
      },
      "filters": {
          "filter": {
              "class": "logging.Filter",
              "name": "Logger对象名"
          },
          ...
      },
      "handlers": {
          "console_handler": {
              "class": "logging.StreamHandler",
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "formatter": "formatter",
              "filters": ["filter", ...]
          },
          "file_handler": {
              "class": "logging.FileHandler",
              "filename": "文件路径",
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "formatter": "formatter",
              "filters": ["filter", ...]
          },
          "byte_handler": {
              "class": "logging.handlers.RotatingFileHandler",
              "filename": "文件路径",
              "maxBytes": 最大字节数,
              "backupCount": 备份数量,
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "formatter": "formatter",
              "filters": ["filter", ...]
          },
          "time_handler": {
              "class": "logging.handlers.TimeRotatingFileHandler",
              "filename": "文件路径",
              "interval": 间隔数,
              "when": "D/H/M/S",
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "formatter": "formatter",
              "filters": ["filter", ...]
          }
      },
      "loggers": {
          "logger": {
              "propagate": True/False,
              "level": "NOTSET/DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "filters": ["filter", ...],
              "handlers": ["handler", ...]
          },
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
logger.error(信息, exc_info=True/False)
```

##### 装饰器

##### 概述

装饰器是通过闭包来实现的，而闭包是通过函数特性来实现的。

##### `@`的作用

`@`的作用是把被装饰得函数作为参数传递到装饰器函数中，并执行该装饰器函数。

> 注：
>
> 当装饰函数时，如果想要保留被装饰函数的函数名和文档字符串时，那么可以通过使用`functools`模块中的`@wraps(func)`来实现。

##### 函数装饰器

* 装饰普通函数

    ```python
    def funcName(形参, ...):
      ...
      def deco(func):
          ...
          def deco_func(*args, **kwargs):
              ...
          return deco_func
      return deco
    ```

* 装饰类方法

    ```python
    def funcName(形参, ...):
      ...
      def deco(func):
          ...
          def deco_func(self, *args, **kwargs):
              ...
          return deco_func
      return
    ```

##### 类装饰器

```python
def deco:
    def __init__(self, func):
        ...
        sefl.__func = func
    
    def __call__(*args, **kwargs):
        ...
        self.__func(*args, **kwargs)
```

##### 类方法装饰器

```python
class 类名:
    def funcName(self, 形参, ...):
        ...
        def deco(func):
            ...
            return self._deco_func(*args, **kwargs)
            
    def _deco_func(self, *args, **kwargs):
        ...
```

### 匿名函数

##### 概念

匿名函数是使用`lambda`来创建的函数。

##### 特点

1. 匿名函数只是一个表达式，函数体比`def`简单；

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
        super(自定义异常类型类名, self).__init__(异常信息)
```

##### 主动抛出异常

```python
raise 自定义异常类型类名
```