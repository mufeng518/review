### 字符串

##### 设置

* 设置一个键值对

    * 结构
        ```redis
        set key value [EX seconds/PX milliseconds] [NX/XX]  # 时间复杂度O(1)
        ```

    * Python返回值

        设置成功，返回`True`；
        设置失败，返回`False`。

* 设置多个键值对

    * 结构

        ```redis
        mset key1 value1 ...  # 时间复杂度O(n)，其中n为key的数量
        ```

    * Python返回值

        设置成功，返回`True`；
        设置失败，返回`False`。

* 偏移设置

    * 结构

        ```redis
        setrange key offset value  # 时间复杂度O(n)，其中n为value的长度
        ```

        > 注：
        >
        > 当`key`不存在或`key`所对应的`value`长度不足时，那么将会使用零字节`\x00`来填充。

    * Python返回值

        返回的是`key`所对应的`value`值被修改后的的长度。

##### 获取

* 获取一个值

    * 结构

        ```shell
        get key  # 时间复杂度O(1)
        ```

    * Python返回值

        `key`存在，返回`key`所对应的`value`值；

        `key`不存在，返回`None`。

* 获取多个值

    * 结构

        ```shell
        mget key1 ...  # 时间复杂度O(n)，其中n为key的数量
        ```

    * Python返回值

        返回的是一个包含所有`key`所对应的`value`的列表。

* 获取键指定范围的值

    * 结构

        ```shell
        getrange key start end  # 时间复杂度O(n)，其中n为value的长度
        ```

        > 注：
        >
        > 1. `start`和`end`可正可负，且`start<=end`；
        >
        > 2. 不遵循差一行为。

    * Python返回值

        `key`存在，返回指定范围的值；

        `key`不存在，返回空字符串。

##### 获取旧值并设置新值

* 结构

    ```redis
    getset key value  # 时间复杂度O(1)
    ```

* Python返回值

    `key`存在，返回旧值；

    `key`不存在，返回`None`。

##### 追加或设置

* 结构

    ```redis
    append key value  # 时间复杂度O(1)
    ```

* Python返回值

    `key`存在，返回`key`所对应的`value`被追加后的长度；

    `key`不存在，返回追加的`value`的长度

##### 计算长度

* 结构

    ```redis
    strlen key  # 时间复杂度O(1)
    ```

* Python返回值

    `key`存在，返回`key`所对应的`value`的长度；

    `key`不存在，返回`0`。

##### 递增

* 结构

    ```redis
    incrby key increment
    incrbyfloat key increment
    ```

    > 注：
    >
    > 1. `key`所对应的`value`值必须是数字字符串；
    >
    > 2. 当`key`不存在时，那么将会对`key`先进行初始化为`0`，再对其进行`incrby`或`incrbyfloat`操作。

* Python返回值

    返回的是`key`所对应的`value`值被递增后的值。