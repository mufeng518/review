### 魔术方法

##### `__new__(cls, *args, **kwargs)`

当实例化对象时，那么该方法会自动被使用。

> 注：
>
> 返回值必须是`super().__new__(cls, *ags, **kwargs)`。

##### `__init__(self, 形参1, ...)`

当初始化对象时，那么该方法会自动被使用。

##### `__del__(self)`

当对象被销毁时，那么该方法会自动被使用。

##### `__len__(self)`

当`len(对象)`时，那么该方法会自动被使用。

> 注：
>
> 返回值必须是`int`类型。

##### `__str__(self)`

当`print(对象)`时，那么该方法会自动被使用。

> 注：
>
> 返回值必须是`str`类型。

##### `__repr__(self)`

当在Python解释器里直接输入对象并回车时，那么该方法会自动被使用。

> 注：
>
> 返回值必须是`str`类型。

##### `__iter__(self)`

当声明对象为可迭代对象时，那么该方法会自动被使用。

##### `__next__(self)`

当对象被用于`for`循环或`next(对象)`时，那么该方法会自动被使用。

##### `__setitem__(self, item, value)`

当以`self/对象[item] = value`的形式设置对象属性时，那么该方法会自动被使用。

> 注：
>
> 该方法体内只能使用`self.__dict__[item] = value`的形式来设置对象属性。

##### `__getitem__(self, item)`

当以`self/对象[item]`的形式访问对象属性时，那么该方法会自动被使用。

> 注：
>
> 此处的`item`可以是`int`类型、`str`类型或`slice`对象。

##### `__delitem__(self, item)`

当以`del self/对象[item]`的形式来删除对象属性时，那么该方法会自动被使用。

> 注：
>
> 该方法体内只能使用`del self.__dict__[attr]`来删除对象属性。

##### `__getattr__(self, attr, value)`

当以`self/对象.attr = value`的形式设置对象属性时，那么该方法会自动被使用。

> 注：
>
> 该方法体内只能使用`self.__dict__[attr] = value`的形式来设置对象属性。

##### `__getattr__(self, attr)`

当以`self/对象.attr`的形式来访问对象不存在的属性时，那么该方法会自动被使用。

##### `__delattr__(self, attr)`

当以`del self/对象.attr`的形式来删除对象属性时，那么该方法会自动被使用。

> 注：
>
> 该方法体内只能使用`del self.__dict__[attr]`来删除对象属性。

##### `__enter__(self)`

当`with`后面紧跟的语句被执行时，那么该方法会自动被使用。

##### `__exit__(self, type, value, trace)`

当`with`代码块被执行完毕或程序报错时，那么该方法会自动被使用。

##### `__eq__/__ne__/__gt__/__gte__/__lt__/__lte__(self, othre)`

当对象被用于比较运算时，那么该方法会自动被使用。

##### `__add__/__sub__/__mul__/__div__/__mod__/__pow__/__floordiv__(self, other)`

当对象被用于算术运算时，那么该方法会自动被使用。

##### `__call__(self, 形参1, ...)`

当`对象(实参1, ...)`时，那么该方法会自动被使用。

### 魔术属性

##### `obj.__dict__`

主要用于查看对象内部所有的属性名和属性值组成的字典。

> 注：
>
> 1. Python内置的数据类型是没有`__dict__`属性的；
>
> 2. 每一个类都拥有自己独有的`__dict__`属性，即使存在继承关系，也互不影响；
>
> 3. 每一个实例化对象也有自己的`__dict__`属性，并且只存储着`self.xxx`属性，但如果存在继承关系，那么父子类共用`__dict__`属性；
>
> 4. 每一个模块也有自己独有的`__dict__`属性。

##### `obj.__class__`

主要用于查看对象所在的类。

##### `[obj.]__name__`

主要用于查看对象的名称。

> 释：
>
> 当`obj`省略时，那么默认为返回的是`__main__`。
>
> 附：
>
> 当一个模块被另一个模块引入时，如果不希望该模块中的某些属性或方法被另一个模块所调用，那么可以通过`__name__`属性来进行控制。

### 辅助工具

##### `__slots__ = [属性1, ...]`

主要用于控制类型的添加。

##### `__file__`

主要用于存储当前正处于运行状态的脚本的路径。

> 注：
>
> 当需要获取当前正处于运行状态的脚本的绝对路径时，那么可以通过`os.path.abspath(__file__)`来获取。

### 内置函数

##### 设置属性值

```python
getattr(对象, 属性名, 属性值)
```

##### 获取属性值

```python
getattr(对象, 属性名[, 默认值])
```

##### 判断对象是否拥有该属性

```python
hasattr(对象, 属性名)
```

##### 判断可迭代对象中的元素是否全部为`True`

```python
all(iterable)
```

##### 判断可迭代对象中的元素是否全部为`False`

```python
any(iterable)
```

### 类型注解的添加

##### 基本结构

* 变量

    ```python
    变量名 类型注解 = 值
    ```

* 函数

    ```python
    def 函数名(形参1 类型注解[=默认值1], ...) -> 返回值的类型注解:
        ...
    ```

##### 具体分类

* 基本类型注解

    ```python
    int
    float
    str
    None
    type
    Any
    ```

* 复合类型注解

    ```python
    List[类型注解]
    Tuple[类型注解1, ..]
    Sequence[类型注解]
    Iterable[类型注解]
    Dict[类型注解, 类型注解]
    Mapping[类型注解, 类型注解]
    Set[类型注解]
    NoReturn
    Callable[[类型注解1, ...], 类型注解]
    Optional[类型注解] = None
    Union[类型注解1, ...]
    别名 = TypeVar("别名", 类型注解1, ...)
    ```

##### 类型别名

```python
别名 = 类型注解
```

### `collections`模块

##### `Counter(字符串/列表/元组)`

* 作用

   主要用于对字符串、列表或元组中的每一个元素进行统计，返回的是一个`Counter`对象，类似于字典。

* 常用方法

    ```python
    .most_common(n)
    .update(newCounter)
    .sub(newCounter)
    .clear()
    ```

##### `defaultdict(数据类型)`

* 作用

    主要用于对字典中不存在的键提供默认值。

    ```python
    int    0
    float  0.0
    str    ""
    bool   False
    list   []
    tuple  ()
    dict   {}
    set    set()
    ```

##### `OrderedDict()`

* 作用

    主要用于保留字典中`key`的添加顺序。

##### `namedtuple("变量名", [元素1, ...])`

* 作用

    主要用于对元组进行重新命名，并且可以通过`.`方法来获取具体的元素。

##### `deque([maxlen])`

* 作用

    主要用于创建一个指定长度的队列。

    > 注：
    >
    > 当`maxlen`省略时，那么默认为队列长度为无穷大。

* 常用方法

    ```python
    .append/appendleft(新元素)
    .insert(索引, 新元素)
    .extend/extendleft(iterable)
    .reverse()
    .pop/popleft()
    .remove(元素)
    .clear()
    .__len__()
    .count(元素)
    .index(元素[, start, end])
    .copy()
    ```

### `importlib`模块

##### 模块的导入

* 相对导入

    ```python
    import_module(name="模块名....", package="包名")
    ```

* 绝对导入

    ```python
    import_module(name="包名.模块名....")
    ```