### 魔术方法

##### 对象

* `__new__(cls, *args, **kwargs)`

    当类对象实例化对象时，那么该方法会自动被调用。
    
    > 注：
    >
    > 返回值必须是`return super().__new__(cls, *args, **kwargs)`。
    
* `__init__(self, 形参, ...)`

    当初始化实例化对象时，那么该方法会自动被调用。
    
* `__del__(self)`

    当对象被销毁时，那么该方法会自动被调用。

##### 功能

* `__len__(self)`

    当`len(对象)`时，那么该方法会自动被调用。
    
    > 注：
    >
    > 返回值必须是`int`类型。
    
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
    
* `__call__(self, 形参, ...)`

    当`对象(实参, ...)`时，那么该方法会自动被调用。

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

    当以`对象/self[item] = value`的形式来设置对象属性时，那么该方法会自动被调用。

* `__getitem__(self, item)`

    当以`对象/self[item]`的形式来访问对象属性时，那么该方法会自动被调用。
    
* `__delitem__(self, item)`

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
    
* `__exit__(self, type, value, trace)`

    当`with`代码块被执行完毕或程序抛出异常时，那么该方法会自动被调用。

##### 算术运算

* `__add__/__sub__/__mul__/__div__/__mod__/__pow__/__floordiv__(self, other)`

    当对对象进行算术运算时，那么该方法会自动被调用。

##### 比较运算

* `__eq__/__ne__/__gt__/__ge__/__lt__/__le__(self, other)`

    当对对象进行比较运算时，那么该方法会自动被调用。

### 魔术属性

##### `obj.__dict__`

查看对象内部所有的属性和属性值组成的字典。

> 注：
>
> 1. Python内置的数据类型是没有该属性的；
>
> 2. 每一个类对象都拥有自己独有的`__dict__`属性，即使存在继承关系，也互不影响；
>
> 3. 每一个实例化对象也有自己的`__dict__`属性，但如果存在继承关系，那么父子类共用`__dict__`属性；
>
> 4. 每一个模块也有自己独有的`__dict__`属性。

##### `obj.__class__`

查看对象所在的类。

##### `[obj.]__name__`

查看对象的名称。

> 注：
>
> 当`obj`省略时，那么默认为返回的是`'__main__'`。
>
> 附：
>
> 当一个模块被另一个模块引入时，如果不希望该模块中的某些代码被另一个模块所执行，那么可以通过`__name__`来进行限制。

### 辅助工具

##### `__slots__ = ("属性", ...)`

用于控制类属性的添加。

##### `__file__`

用于获取当前处于运行状态的脚本的路径。

> 注：
>
> 当需要获取当前处于运行状态的脚本的绝对路径时，那么最好通过`os.path.abspath(__file__)`来进行获取。

### 内置函数

##### 设置属性值

```python
setattr(object, 属性名, 属性值)
```

##### 获取属性值

```python
getattr(object, 属性名[, default])
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
    def 函数名(形参: 类型注解, ..., 形参n: 类型注解 = 默认值) -> 返回值的类型注解:
      ...
    ```

##### 具体分类

* 基本类型注解

    `str` `int` `float` `None` `bool` `Any` `type`

* 复合类型注解

    `List[类型注解]` `Tuple[类型注解, ...]` `Sequence[类型注解]` `Iterable[类型注解]` `Dict[类型注解, 类型注解]` `Set[类型注解]` `Map[类型注解, 类型注解]` `Callable[[类型注解, ...], 类型注解]` `NoReturn` `Union[类型注解, ...]` `Optional[类型注解] = None`

##### 类型注解的别名

```python
别名 = 类型注解
```

### `logging`模块

##### 日志级别说明

`NOTSET` 不设置

`DEBUG` 输出调试信息

`INFO` 输出常规信息

`WARNING` 输出事件信息

`ERROR` 输出代码错误信息

`CRITICAL` 输出系统故障信息

##### 日志格式说明

`%(name)s` `%(asctime)s` `%(levelno)s` `%(levelname)s` `%(pathname)s` `%(filename)s` `%(lineno)s` `%(process)s` `%(processName)s` `%(thread)s` `%(threadName)s` `%(message)s`

##### 创建默认`logger`

```python
import logging

logging.basicConfig(level, format, datefmt, filename, filemode)
logger = logging.getLogger(name)
```

##### 通过`dict`对象来创建`logger`

* `dict`结构

    ```python
    config = {
      "version": 1,
      "disable_exists_loggers": True,
      "formatters": {
          "formatter": {
              "class": "logger.Formatter",
              "format": "日志格式",
              "datefmt": "日志中的日期格式"
          },
          ...
      },
      "filters": {
          "filter": {
              "class": "logger.Filter",
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
          }
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
logger.error(信息, exc_info=True)
```