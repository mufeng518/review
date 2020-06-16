### MySQL简介

##### SQL概述

SQL是`Structured Query Language`的简称，是一门程序设计和数据查询的语言。

##### MySQL优化范围

* 字段类型优化

* 插入优化

    > 附：MySQL语句的执行步骤
    >
    > 连接MySQL服务器 -> 选择数据库 -> 语法分析 -> 验证表 -> 插入数据 -> 断开连接

* 查询优化

* 表优化

* 数据库优化

* 引擎优化

* 硬盘优化

##### SQL注入

```mysql
or 1=1 --
```

### `innodb`和`myisam`的区别

##### 事务支持

`innodb`是事务安全的，但由于`innodb`环境下的`autocommit`默认是开启的，即每一条SQL语句都会默认被封装成一个事物自动提交，这样会严重影响数据库性能，所以通常情况下最好一次性把多条SQL语句单独封装成一个事物后再去提交。

`myisam`是非事务安全的。

##### `CURD`

`innodb`在`CUD`操作上性能更好。

`myisam`在`R`操作上性能更好。

##### 存储结构

`innodb`会将一张数据表存储成两个文件，分别是`表名.frm`和`表名.ibd`。

`myisam`会将一张数据表存储成三个文件，分别是`表明.frm`、`表名.MYI`和`表名.MYD`。

##### 外键

`innodb`支持外键。

`myisam`不支持外键。

##### 全文索引

`innodb`不支持全文索引。

`myisam`支持全文索引。

##### 可移植性

`innodb`环境下的数据文件不支持移动。

`myisam`环境下的数据文件支持移动。

### 字符集和校对集

##### 字符集的使用环境

* 保存数据时使用

    > 附：常用的字符集
    >
    > `gbk`：是简体中文字符，一个汉子最多占用两个字节的存储空间；
    >
    > `gb2312`：是所有中文字符，一个汉子最多占用两个字节的存储空间；
    >
    > `utf8`：是国际通用编码，一个汉子最多占用三个字节的存储空间；
    >
    > `utf8mb4`：是国际通用编码，一个汉子最多占用四个字节的存储空间。

* 传输数据时使用

    * 查看当前MySQL系统支持的字符集
    
        ```mysql
        show variables like "character_%";
        ```
    
    * 临时修改当前MySQL系统支持的字符集
    
        ```mysql
        set names 新字符集;
        ```

##### 校对集

* 概述

    校对集是在某种字符集下让字符和字符间形成某种关系的集合。

* 查看当前MySQL系统支持的校对集

    ```mysql
    show collation;
    ```

* 分类

    * 不区分大小写
    
        ```mysql
        字符集_general_ci
        ```

    * 区分大小写
    
        ```mysql
        字符集_bin
        ```

### 字段类型

##### 整型

`tinyint` 1 -128~127

`int` 4 -21亿~21亿

`bigint` 8 -2^63~2^63

##### 无符号的

`unsigned`

##### 零填充

`zerofill`

##### 浮点型

`float(m,d)` 4

`double(m,d)` 8

`decimal(m,d)`

##### 字符串类型

`char(m)` 255

`varchar(m)` 65535

##### 枚举类型

* 优点

    * 限制输入范围
    
    * 减少存储空间
    
    * 提高执行效率

* 结构

    ```mysql
    enum(可选项1, ...)
    ```

* 索引的计算方式

    `1` ...

##### 集合类型

* 结构

    ```mysql
    set(可选项1, ..)
    ```

* 索引的计算方式

    `2^0` ...

* 为什么实际开发中一般不使用集合类型

    因为在实际开发中，多选框的可选项至少有成千上万个，这样会导致索引所占据的存储空间极大，所以实际开发中一般不使用集合类型。

* 多选框的问题该如何解决

    将多选框的可选项单独存放在一张数据表中。

##### 日期时间类型

`date` 1000.1.1~9999.12.31

`datetime` 1000.1.1 00:00:00~9999.12.31 23:59:59

##### 布尔类型

`boolean`

### 完整性约束条件

##### 空或非空

`null` `not null`

##### 默认值

`default 默认值`

##### 自增长

`auto_increment`

> 注：
>
> 当全列插入时，那么用`null`来占位，但插入成功以后以实际数据为准。

##### 备注

`commit "备注"`

### 数据完整性

##### 从字段类型角度出发

`数据完整性 = 正确性 + 准确性`

> 释：
>
> 正确性：是字段类型是否使用得当；
>
> 准确性：是字段类型的范围是否使用得当。

##### 从表结构角度出发

`数据完整性 = 域完整性 + 实体完整性 + 引用完整性 + 自定义完整性`

> 释：
>
> 域完整性：是确保各列数据间可以明显区分；
>
> 实体完整性：是确保各个实体间可以明显区分；
>
> 引用完整性：是确保关联表间的数据对应完整；
>
> 自定义完整性：是自定义的一套规则。

### 索引

##### 适用范围

索引适用于数据量大且频繁查找或替换的数据列。

##### 优缺点

* 优点

    提高执行效率。

* 缺点

    增加存储空间。

##### 索引类型

`primary key`

`unique`

`index`

`index(字段名1, ...)`

`fulltext index`

##### 创建

* 建表时添加

    ```mysql
    create table [if not exists] `表名`(
    ...,
    索引类型 `索引名`(字段名)
    )...;
    ```

* 建表后添加

    ```mysql
    alter table `表名` add 索引类型 `索引名`(字段名);
    ```

##### 查看指定表的索引

```mysql
show index from `表名`;
```

##### 删除

```mysql
alter table drop 索引类型 `索引名`;
```

### 事务

##### 概述

事务是一个最小的且不可再分的工作单元(通常情况下，一个事物对应一个完整的业务)，并且事务只针对`CUD`进行操作。

> 注：
>
> 当事务未执行完毕时，那么DML语句是不会更改底层硬盘文件中的数据，只有当事务成功结束时，那么DML语句才会更改底层硬盘文件中的数据。

##### 特性

* 原子性

    事务是一个最小的且不可再分的工作单元。
    
* 一致性

    事务中的语句要么同时成功，要么同时失败。
    
* 隔离性

    事务间不存在任何关系。
    
* 持久性

    事务一旦执行成功，不可再被更改。

##### 事务的开启和结束

* 开启事务

    ```mysql
    start transaction;
    ```

* 结束事务

    ```mysql
    commit;
    rollback;
    ```

    * 查看当前MySQL系统的事务提交机制
    
        ```mysql
        show variables like "autocommit";
        ```
    
    * 临时修改当前MySQL系统的事务提交机制
    
        ```mysql
        set autocommit=0/1;
        ```
    
### 实体间的关系和数据库设计

##### 实体间的关系

* 一对一

* 一对多

* 多对多

##### 数据库三范式

* 第一范式

    是确保每列数据原子化。
    
* 第二范式

    是基于第一范式，是确保每张数据表只描述一件事情。

* 第三范式

    是基于第二范式，是确保消除传递依赖。
    
### 视图

##### 概述

视图是一张虚拟的数据表，视图中没有任何实际数据，只有表的结构，数据是从基础表中去获取的。

> 注：
>
> 一张数据表可以创建多个视图，一个视图可以引用多张数据表。

##### 创建

```mysql
create [or replace algorithm=算法类型] view `视图名`
as
sql语句;
```

> 释：算法类型
>
> `merge` `temptable` `undefined`

##### 查看

* 查看所有视图

    ```mysql
    show tables;
    ```

* 查看建视图语句

    ```mysql
    show create table `表名`;
    ```

* 查看视图结构

    ```mysql
    desc `表名`;
    ```

##### 修改

```mysql
alter view `视图名`
as
新sql语句;
```

##### 删除

```mysql
drop view `视图名`;
```

### 触发器

##### 概述

触发器是一个特殊的存储过程，不需要外部来调用，当事件被触发时会自动执行，并且触发器是一个事务，可以回滚。

##### 类型

* `insert`触发器

* `update`触发器

* `delete`触发器

##### 创建

```mysql
delimiter //
create trigger `触发器名`
before/after 触发类型 on `表名` for each row
start
sql语句;
end //
delimiter ;
```

* 为什么必须要更改定界符

    因为`;`不仅要保证sql语句的结构完整性，而且默认情况下会将代码发送到服务器端直接执行，所以必须要更改定界符。

* `old`表和`new`表

    `old`表：是保存更改前数据表中的数据；
    
    `new`表：是保存更改后数据表中的数据。

* `old`表和`new`表的共同特征

    * 都是临时表，并且数据结构相同；
    
    * 都是触发器触发时创建，触发器结束时销毁；
    
    * 都是只能读取，不能写入。

##### 查看

* 查看所有触发器

    ```mysql
    show triggers;
    ```

* 查看建触发器语句

    ```mysql
    show create trigger `触发器名`;
    ```

##### 删除

```mysql
drop trigger `触发器名`;
```

### 存储过程

##### 概述

存储过程是一个特殊的函数。

##### 创建

```mysql
delimiter //
create procedure `存储过程名`(参数1, ...)
begin
sql语句;
end//
delimiter ;
```

##### 参数的分类

* 输入参数

    ```mysql
    in 形参 数据类型
    ```

* 输出参数

    ```mysql
    out 形参 数据类型
    ```

* 输入输出参数

    ```mysql
    inout 形参 数据类型
    ```

##### 调用

* 输入调用

    ```mysql
    call `存储过程名`(实参)
    ```

* 输出调用

    ```mysql
    call `存储过程名`(@实参)
    ```

* 输入输出调用

    ```mysql
    set @实参=值;
    call `存储过程名`(@实参)
    ```

##### 变量的分类

* 系统变量

    是一个以`@@`开头的变量。

* 全局变量

    是一个以`@`开头的变量，即`@变量名`。
    
    > 注：
    >
    > 全局变量的数据类型取决于全局变量的值，当全局变量的值省略时，那么默认为全局变量的数据类型为`null`。

* 局部变量

    ```mysql
    declare 变量名 数据类型 [default 默认值];
    ```
  
    > 注：
    >
    > 局部变量名不能与字段名同名。

##### 变量的赋值

```mysql
set @变量名/变量名=值;
```

##### 查看

* 查看存储过程状态

    ```mysql
    show procedure status;
    ```

* 查看建存储过程语句

    ```mysql
    show create procedure `存储过程名`;
    ```

##### 删除

```mysql
drop procedure `存储过程名`;
```

### 函数

##### 创建

```mysql
delimiter //
create function `函数名`(形参1 数据类型, ...) returns 数据类型
begin
sql语句;
return ...;
end//
delimiter ;
```

* 查看当前MySQL系统的信任函数创建者机制

    ```mysql
    show variables like "log_bin_trust_function_creators";
    ```

* 临时修改当前MySQL系统的信任函数创建者机制

    ```mysql
    set global log_bin_trust_function_creators=0/1;
    ```

##### 调用

```mysql
`函数名`(实参1, ...);
```

##### 查看

* 查看函数状态

    ```mysql
    show function status;
    ```

* 查看建函数语句

    ```mysql
    show create function `函数名`;
    ```

##### 删除

```mysql
drop function `函数名`;
```

### MySQL基本操作

##### 连接MySQL服务器

```shell script
mysql -u用户名 -p密码 -hip地址 -P端口号
```

##### 断开连接

```mysql
exit;
```

### 数据库基本操作

##### 创建

```shell script
create database `数据库名`;
```

##### 使用

```mysql
use `数据库名`;
```

##### 查看

* 查看所有数据库

    ```shell script
    show databases;
    ```

* 查看建数据库语句

    ```mysql
    show create database `数据库名`;
    ```

* 查看当前数据库的数据库名

    ```mysql
    select database() [from dual];
    ```
  
    > 释：
    >
    > `dual`：是一张为了保证sql语句的结构完整性而设计的虚拟表。

##### 删除

```mysql
drop database `数据库名`;
```

### 数据表基本操作

##### 创建

```mysql
create table `表名`(
字段名1 数据类型 [完整性约束条件],
...
)engine=引擎 charset=字符集 collate=校对集;
```

##### 查看

* 查看所有数据表

    ```mysql
    show tables;
    ```

* 查看建表语句

    ```mysql
    show create table `表名`;
    ```

* 查看表结构

    ```mysql
    desc `表名`;
    ```

##### 修改

* 修改表名

    ```mysql
    alter table `表名` rename `新表名`;
    ```

* 修改引擎

    ```mysql
    alter table `表名` engine=新引擎;
    ```

* 修改字符集

    ```mysql
    alter table `表名` charset=新字符集;
    ```

* 修改校对集

    ```mysql
    alter table `表名` collate=新校对集;
    ```

* 增加一个新字段

    ```mysql
    alter table `表名` add 新字段名 字段类型 [完整性约束条件] first/after 已存在的字段名;
    ```

* 修改字段名

    ```mysql
    alter table `表名` change 字段名 新字段名 字段类型;
    ```

修改字段类型

    ```mysql
    alter table `表名` modify 字段名 新字段类型 [first/after 已存在的字段名];
    ```

##### 复制 

* 复制表结构(不包含主键)和表数据

    ```mysql
    create table `新表名` select * from `表名`;
    ```

* 只复制表结构(包含主键)

    ```mysql
    create table `新表名` like `表名`;
    ```

##### 移动

```mysql
alter table `表名` rename to `数据库名`.`新表名`;
```

##### 删除

* 数据表

    ```mysql
    drop table `表名`;
    ```
  
* 指定字段

    ```mysql
    alter table `表名` drop 字段名;
    ```

### 数据基本操作

##### 插入

* 全列插入

    ```mysql
    insert into `表名` values(null, 值1, ...), ...;
    ```

* 缺省插入

    ```mysql
    insert into `表名`(字段名1, ...) values(值1, ...), ...;
    ```

##### 查询

* 基本查询

    ```mysql
    select */字段名1 [as [别名]], ... from `表名`;
    ```

* 消除重复行

    ```mysql
    select distinct 字段名1 [as [别名]], ... from `表名`;
    ```

* 聚合查询

    ```mysql
    select 聚合函数1 [as [别名]], ... from `表名`;
    ```

* `where`查询

```mysql
select 聚合函数1 [as [别名]], .../ */字段名1 [as [别名]], ... from `表名` where 条件;
```

    * 算术运算符
    
       ```mysql
       + - * / %
       ```
    
    * 比较运算符
    
        ```mysql
        = != > >= < <=
        ```
    
    * 逻辑运算符
    
        ```mysql
        and or not 布尔表达式
        ```
    
    * 模糊查询
    
        ```mysql
        like "..."
        ```
    
    * 范围查询
    
        ```mysql
        between ... and ...
        not between ... and ...
        ```
    
    * 空值或非空值查询
    
        ```mysql
        is null
        is not null
        ```

* 分组查询

    ```mysql
    select 聚合函数1 [as [别名]], .../ */字段名1 [as [别名]], ... from `表名` group by 字段名1, ... [having 条件/with rollup];
    ```

* 分页查询

    ```mysql
    select 聚合函数1 [as [别名]], .../ */字段名1 [as [别名]], ... from `表名` limit [起始行,]行数;
    ```

##### 更新

```mysql
update `表名` set 字段名1=值1, ... [where 条件];
```

##### 删除

* 保留`id`(为后期数据恢复做准备)

    ```mysql
    delete from `表名` [where 条件];
    ```

* 不保留`id`(是先销毁数据表，再按照原来的建表语句重建数据表)

    ```mysql
    truncate table `表名`;
    ```

### 外键

##### 概述

外键是主从数据表中的公共字段。

##### 特点

* 主表中不存在的数据，从表中不可以插入；

* 从表中已存在的数据，主表中不可以删除；

* 当需要删除数据表时，那么应该先删除从数据表，再删除主数据表。

##### 添加

* 建表时添加

    ```mysql
    create table `表名`(
    ...,
    constraint `外键名` foreign key(公共字段名) references `主表名`(公共字段名) on update 级联操作 on delete 级联操作
    )...;
    ```

* 建表后添加

    ```mysql
    alter table `表名` add constraint `外键名` foreign key(公共字段名) references `主表名`(公共字段名) on update 级联操作 on delete 级联操作;
    ```

##### 删除

```mysql
alter table `表名` drop foreign key `外键名`;
```

### 联合查询

##### 概述

联合查询是用于对一张或多张数据结构相同的数据表中的数据进行查询时使用，并且会把多个查询集进行纵向拼接，字段名依据的是最左侧数据表的字段名。

> 注：
>
> 1. 当进行联合查询时，那么字段类型可以不相同，但字段数量必须相同；
>
> 2. 当对联合查询的查询集进行排序时，那么必须设置限制数量，即`limit 999999999`。

##### 结构

```mysql
(sql语句1) union (sql语句2) ...;
```

### 多表查询

##### 概述

多表查询是用于对关联表间的数据进行查询时使用。

##### 常用连接

* `inner join`

    ```mysql
    from `主表名` inner join `从表名` on `主表名`.公共字段名=`从表名`.公共字段名
    ```
  
* `left/right outer join`

    ```mysql
    from `主表名` left/right outer join `从表名` on `主表名`.公共字段名=`从表名`.公共字段名
    ```
  
* `cross join`

* `natural join`

* `using(公共字段名)`

### 子查询

##### 概述

子查询是用于通过一张或多张数据表对其相关联的数据表中的数据进行查询时使用。

##### 常用关键字

* `where 字段名 in/not in(...)`

* `where 字段名 逻辑运算符some/any/all(...)`

* `where exists/not exists(...)`

### 用户管理

##### 创建

```mysql
create user `用户名`@ip地址 identified by `密码`；
```

##### 授予权限

```mysql
grant insert/select/update/delete/all privileges on `数据库名`/ *.`表名`/* to `用户名`@ip地址;
```

##### 撤销权限

```mysql
revoke insert/select/update/delete/all privileges on `数据库名`/ *.`表名`/* from `用户名`@ip地址;
```

##### 刷新权限

```mysql
flush privileges
```

##### 删除

```mysql
drop user `用户名`@ip地址;
```

### 常用语句

##### 判断语句

```mysql
if(条件语句, 条件语句为true时返回的结果, 条件语句为false时返回的结果)

if 条件语句 then
    ...
elseif 条件语句 then
    ...
...
else
    ...
end if;
```

##### 循环语句

```mysql
别名:while 条件语句 do
    ...
end while;
```

> 附：
>
> `iterate 别名;` `leave 别名;`

### Python操作MySQL

```python
import pymysql

db = pymysql.connect(user="用户名", passwd="密码", host="ip地址", port=端口号, database="数据库名", charset="编码方式")
cursor = db.cursor(pymysql.cursors.DictCursor)

try:
    cursor.execute("insert into `表名` values(%s, ...)", (值1, ...))
    cursor.executemany("insert into `表名` values(%s, ...)", [(值1, ...), ...])

    curosr.execute("...")
    data = cursor.fetchone/fetchmany()

    db.commit()
except:
    db.rollback()
finally:
    cursor.close()
    db.close()
```