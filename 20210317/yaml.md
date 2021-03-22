### YAML简介

##### 概念

YAML是一门专门用来写配置文件的语言。

##### 支持的数据结构

* 对象

    对象也被称为哈希、映射或字典。

* 数组

    数组也被称为序列或列表。

* 纯量

    纯量是一个单个的、不可再分的值，包括字符串、整数、浮点数、`bool`、`Null`、日期和日期时间。

##### 安装

```shell script
pip install PyYAML
```

### YAML书写结构

##### 对象

* 行内表示

    ```yaml
    {key: value}
    ```

* 行外表示

    ```yaml
    key: value
    ...
    ```

##### 数组

* 行内表示

    ```yaml
    [元素, ...]
    ```

* 行外表示

    ```yaml
    - 元素
    - ...
    ```

##### 注释

```yaml
# 注释
```

### 纯量的表现形式

##### 字符串

* 单行字符串

    ```yaml
    字符串
    ```
  
    > 注：
    >
    > 1. 当字符串中含有空格或特殊字符时，那么必须使用英文状态下的单引号或双引号来将其括起来；
    >
    > 2. 当字符串中含有转义字符时，那么必须使用单引号来将其括起来。

* 多行字符串

    * 折叠换行
    
        ```yaml
        >
        ```
    
    * 不折叠换行
    
        ```yaml
        |
        ```
    
    * 保留字符串末尾的`\n`
    
        ```yaml
        >+
        |+
        ```
    
    * 不保留字符串末尾的`\n`
    
        ```yaml
        >-
        |-
        ```

##### 布尔值

```yaml
true
false
```

##### `Null`

```yaml
null
~
```

##### 日期

```yaml
四位数的年-两位数的月-两位数的日
```

##### 日期时间

```yaml
四位数的年-两位数的月-两位数的日t两位数的时:两位数的分:两位数的秒
```

### 对象引用

##### 建立锚点

* 对象

    ```yaml
    key:/- &锚点名
      key: value
      ...
    key:/- &锚点名 {key: value, ...}
    ```

* 数组

    ```yaml
    key:/- &锚点名
      - 元素
      - ...
    # 或
    key:/- &锚点名 [元素, ...]
    ```

##### 引用锚点

```yaml
*锚点名
```

### 类型强转

##### 适用范围

类型强转只适用于纯量类型间的数据转换。

##### 转换成字符串

```yaml
key:/- !!str ...
```

##### 转换成整数

```yaml
key:/- !!int ...
```

##### 转换成浮点数

```yaml
key:/- !!float ...
```