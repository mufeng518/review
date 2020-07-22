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
    def 函数名(形参: 类型注解, ..., 形参: 类型注解 = 默认值) -> 返回值的类型注解
    ```

##### 具体分类

* 基本类型注解

    ```python
    str int float bool None type Any
    ```

* 复合类型注解

    ```python
    List[类型注解]
    Tuple[类型注解, ...]
    Sequence[类型注解]
    Iterable[类型注解]
    Mapping[类型注解, 类型注解]
    Dict[类型注解, 类型注解]
    Set[类型注解]
    Callable[[类型注解, ...], 类型注解]
    NoReturn
    Optional[类型注解] = None
    Union[类型注解, ...]
    ```

##### 类型注解的别名

```python
别名 = 类型注解
```

### `logging`模块

##### 日志级别说明

```python
NOTSET
DEBUG
INFO
WARNING
ERROR
CRITICAL
```

##### 日志格式说明

```python
%(name)s %(asctime)s %(levelno)s %(levelname)s %(pathname)s %(filename)s %(lineno)s %(process)s %(processName)s %(thread)s %(threadName)s %(message)s
```

##### 创建默认`logger`

```python
import logging

logging.basicConfig(level, format, datefmt, filename, filemode)
logger = logging.getLogger([name])
```

##### 通过`dict`对象来创建`logger`

* `dict`结构：
    ```python
    {
      "version": 1,
      "disable_exists_loggers": True/False,
      "formatters": {
          "console_formatter": {
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
          "streamHandler": {
              "class": "logging.StreamHandler",
              "level": "DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "formatter": "...",
              "filter": [...]
          },
          "fileHandler": {
              "class": "logging.FileHandler",
              "filename": "文件路径",
              "level": "DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "formatter": "...",
              "filter": [...]
          },
          "byteHandler": {
              "class": "logging.handlers.RotatingFileHandler",
              "filename": "文件路径",
              "maxBytes": 文件大小,
              "backupCount": 备份数量,
              "level": "DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "formatter": "...",
              "filter": [...]
          },
          "timeHandler": {
              "class": "logging.FileHandler",
              "filename": "文件路径",
              "when": "D/H/M/S",
              "interval": 数值,
              "backupCount": 备份数量
              "level": "DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "formatter": "...",
              "filter": [...]
          }
      }
      "loggers": {
          "Logger对象名": {
              "level": "DEBUG/INFO/WARNING/ERROR/CRITICAL",
              "handler": [...],
              "propagate": True/False
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