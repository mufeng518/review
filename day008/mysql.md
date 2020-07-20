### MySQL简介

##### SQL概述

SQL是Structured Query Language的简称，是一门程序设计和数据查询的语言。

##### MySQL优化范围

* 字段类型优化

* 插入优化

* 查询优化

* 表优化

* 数据库优化

* 服务器优化

* 硬盘优化

##### SQL注入

```mysql
or 1=1 --
```

### `innodb`和`myisam`的区别

* 事务

    `innodb`是事务安全的，并且`innodb`环境下的`autocommit`默认是开启的，即每条SQL语句都会被默认封装成一个事务自动提交，这样会严重影响数据库性能，所以通常情况下最好一次性把多条SQL语句单独封装成一个事务后再去提交。
    
    `myisam`是非事务安全的。
    
* CURD

    `innodb`在CUD操作上性能更好。
    
    `myisam`在R操作上性能更好。
    
* 存储结构

    `innodb`是将一张数据表存储成两个文件，分别是`表名.frm`和`表名.ibd`。
    
    `myisam`是将一张数据表存储成三个文件，分别是`表名.frm`、`表名.MYI`和`表名.MYD`。
    
* 外键

    `innodb`支持外键。
    
    `myisam`不知外键。
    
* 全文索引

    `innodb`不支持全文索引。
    
    `myisam`支持全文索引。
    
* 可移植性

    `innodb`环境下的数据文件不支持移动。
    
    `myisam`环境下的数据文件支持移动。

### 字符集和校对集

##### 字符集的使用环境

* 保存数据时使用

    `gbk` `gbk2312` `utf8` `utf8mb4`
    
* 传输数据时使用

    > 附：查看当前MySQL系统的字符集
    >
    > ```mysql
    > show variables like 'character_%';
    > set names 新字符集;
    > ```

##### 校对集

* 概述

    校对集是在某种字符集下让字符和字符间形成某种关系的集合。

* 查看当前MySQL系统支持的校对集

    ```mysql
    show collation;
    ```

* 分类

    * 区分大小写
    
        ```mysql
        字符集_bin
        ```
    
    * 不区分大小写
    
        ```mysql
        字符集_general_ci
        ```

### 字段类型

##### 整型

`tinyint` 1 -128~127

`int` 4 -32768~32768

`bigint` 8 -21亿~21亿

##### 无符号的

`unsigned`

##### 零填充

`zerofill`

##### 浮点型

`float(m,d)` 4

`double(m,d)` 8

`decimal(m,d)`

##### 字符串类型

`varchar(m)` 255

`char(m)` 65535

##### 枚举类型

* 优点

    1. 限制输入范围；
    
    2. 减少存储空间；
    
    3. 提高查询效率。

* 结构

    ```mysql
    enum(可选项1, ...)
    ```

* 索引的计算方式

    `1` ...

##### 集合类型

* 结构

    ```mysql
    set(可选项1, ...)
    ```

* 索引的计算方式

    `2^0` ...

* 为什么实际开发中一般不使用集合类型

    因为实际开发中多选框的可选项至少成百上千个，这样会导致索引所占据的存储空间极大，所以实际开发中一般不使用集合类型。

* 多选框的问题该如何解决

    将多选框的可选项单独存放在一张数据表中。

##### 日期时间类型

`date` 1000.01.01~9999.12.31

`datetime` 1000.01.01 00:00:00~9999.12.31 23:59:59

##### 布尔类型

`bool`

### 完整性约束条件

##### 空或非空

`null`

`not null`

##### 默认值

`default 默认值`

##### 自增长

`auto_increment`

> 注：
>
> 当全列插入时用`null`来填充，但插入成功以后以实际数据为准。

##### 备注

`commit '备注'`

### 数据完整性

##### 从字段类型角度出发

数据完整性 = 正确性 + 准确性

##### 从表结构角度出发

数据完整性 = 域完整性 + 实体完整性 + 引用完整性 + 自定义完整性

### 索引

##### 适用范围

索引适用与数据量大且频繁查找或排序的数据列。

##### 优缺点

* 优点

    提高查询效率。

* 缺点

    增减存储空间。

##### 索引类型

`primary key`

`unique`

`index`

`index(字段名, ...)`

`fulltext index`

##### 创建

* 建表时添加

    ```mysql
    create table `表名`(
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

事务是一个最小的且不可再分的工作单元，通常情况下一个事务对应一个完整的业务，并且事务只针对CRD进行操作。

> 注：
>
> 当事务未执行完毕时，那么DML语句是不会更改系统底层硬盘文件中的数据，只有当事务成功结束时，那么DML语句才会更改系统底层硬盘文件中的数据。

##### 特性

* 原子性

    事务是一个最小的且不可再分的工作单元。

* 一致性

    事务中的语句要么同时成功要么同时失败。

* 隔离性

    事务间不具有任何关系。

* 持久性

    事务一旦执行成功，便不会再被更改。

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

视图是一张虚拟的数据表，不存在任何数据，只有表的结构，数据是从基础表中去获取的。

> 注：
>
> 一张数据表可以创建多个视图，一个视图可以应用多张数据表。

##### 创建

```mysql
create [or repace algorithm=视图算法] view `视图名`
as
sql语句;
```

##### 查看

* 查看所有视图

    ```mysql
    show tables;
    ```

* 查看建视图语句

    ```mysql
    create view `视图名`;
    ```

* 查看视图结构

    ```mysql
    desc `视图名`;
    ```

##### 修改

```mysql
alter view `视图名`
as
sql语句;
```

##### 删除

```mysql
drop view `视图名`;
```

### 触发器

##### 概述

触发器是一个特殊的存储过程，不需要外部来调用，当事件被触发时会自动执行，并且触发器是一个事务，可以回滚。

##### 类型

`insert`触发器

`update`触发器

`delete`触发器

##### 创建

```mysql
delimiter //
create trigger `触发器名`
before/after 触发类型 on `表名` for each row
begin
sql语句;
end //
delimiter ;
```

* 为什么必须要更改定界符

    因为分号不仅要保证SQL语句的结构完整性，而且默认情况下会将代码发送到服务器端直接执行，所以必须要更改定界符。

* `old`表和`new`表

    `old`表是保存修改之前数据表中的数据，`new`表是保存修改之后数据表中的数据。

* `old`表和`new`表的共同特征

    1. 都是临时表，并且数据结构相同；
    
    2. 都是触发器触发时创建，触发器结束时销毁；
    
    3. 都是只能读取，不能写入。

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
DELIMITER //
CREATE PROCEDURE `存储过程名`(参数, ...)
BEGIN 
sql语句;
END//
DELIMITER ;
```

##### 参数的分类

* 输入参数

    `in 形参 数据类型`

* 输出参数

    `out 形参 数据类型`

* 输入输出参数

    `inout 形参 数据类型`

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
    set @实参=值
    call `存储过程名`(@实参)
    ```

##### 变量的分类

* 系统变量

    系统变量是一个以两个`@`开头的变量。

* 全局变量

    全局变量是一个以一个`@`开头的变量。
    
    > 注：
    >
    > 全局变量的数据类型是有全局变量的值决定的，当全局变量的值省略时，那么全局变量的数据类型是`Null`。

* 局部变量

    ```mysql
    declare 变量名 数据类型 [default 默认值];
    ```
    
    > 注：
    >
    > 局部变量名不可以与字段名同名。

##### 变量的赋值

```mysql
set @变量名/变量名=值
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
create function `函数名`(形参 数据类型, ...) returns 数据类型
begin
sql语句;
return ...
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
`函数名`(实参, ...)
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

```shell
mysql -u用户名 -p密码 -hip地址 -P端口号
```

##### 断开连接

```mysql
exit;
```

### 数据库基本操作

##### 创建

```mysql
create database `数据库名`;
```

##### 使用

```mysql
use `数据库名`;
```

##### 查看

* 查看所有数据库

    ```mysql
    show databases;
    ```

* 查看建数据库语句

    ```mysql
    show create database `数据库名`;
    ```

* 查看当前数据库的数据库名

    ```mysql
    select database() from dual;
    ```

##### 删除

```mysql
drop database `数据库名`;
```

### 数据表基本操作

##### 创建

```mysql
create table `表名`(
字段名 字段类型 [完整性约束条件],
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

* 修改字段类型

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

* 删除数据表

    ```mysql
    drop table `表名`;
    ```

* 删除数据表中指定字段

    ```mysql
    alter table `表名` drop 字段名;
    ```

### 数据基本操作

##### 插入

* 全列插入

    ```mysql
    insert into `表名` values(null, 值, ...), ...;
    ```

* 缺省插入

    ```mysql
    insert into `表名`(字段名, ...) values(值, ...), ...;
    ```

##### 查询

* 基本查询

    ```mysql
    select */字段名, ... from `表名` [[as] 别名];
    ```

* 消除重复行

    ```mysql
    select distinct 字段名, ... from `表名` [[as] 别名];
    ```

* 聚合查询

    ```mysql
    select 聚合函数名(*/字段名) [[as] 别名], ... from `表名` [[as] 别名];
    ```

* `where`查询

    ```mysql
    select 聚合函数名(*/字段名) [[as] 别名], .../字段名, .../ * from `表名` [[as 别名] where 条件语句;
    ```

    * 算术运算符
    
        `+` `-` `*` `/` `%`
    
    * 比较运算符
    
        `=` `!=` `>` `>=` `<` `<=`
    
    * 逻辑运算符
    
        `and` `or` `not 布尔表达式`
    
    * 模糊查询
    
        `like` `_` `%`
    
    * 范围查询
    
        `between ... and ...` `not between ... and ...`
    
    * 空值或非空值查询
    
        `is null` `is not null`

* 分组查询

    ```mysql
    select */聚合函数 [[as] 别名], .../字段名 [[as] 别名], ... from `表名` [[as] 别名] group by 字段名, ... having 条件语句/with rollup;
    ```

* 排序

    ```mysql
    select */聚合函数 [[as] 别名], .../字段名 [[as] 别名], ... from `表名` [[as] 别名] order by 字段名 asc/desc;
    ```

* 分页查询

    ```mysql
    select */聚合函数 [[as] 别名], .../字段名 [[as] 别名], ... from `表名` [[as] 别名] limit [起始行,]行数;
    ```

##### 更新

```mysql
update `表名` set 字段名=值, ... [where 条件语句];
```

##### 删除

* 保留`id`(为后期数据恢复做准备)

    ```mysql
    delete from `表名` [where 条件语句];
    ```

* 不保留`id`(是先销毁数据表，再按照原来的建表语句重建数据表)

    ```mysql
    truncate table `表名`;
    ```

### 外键

##### 概述

外键是主从数据表中的公共字段。

##### 特点

1. 主表中不存在的数据从表中不可以添加；

2. 从表中已存在的数据主表中不可以删除；

3. 当需要删除数据表时，那么应该先删除从表，再删除主表。

##### 添加

* 建表时添加

    ```mysql
    create table `表名`(
    ...,
    constraint `外键名` foreign key(公共字段名) references `主表名`(公共字段名) on update 级联操作 on delete 级联操作;
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

联合查询是用于对一张或多张数据结构相同的数据表中的数据进行查询时使用，并且会把多张数据表的查询集进行纵向拼接，字段名依据的是最左侧数据表中的字段。

> 注：
>
> 1. 当进行联合查询时，字段类型可以不相同，但字段数量必须相同；
>
> 2. 当对联合查询的查询集进行排序时，那么必须设置查询数量，即`limit 999999999`;

##### 结构

```mysql
(sql语句) union (sql语句) ...;
```

### 多表查询

##### 概述

多表查询是用于对关联表间的数据进行查询时使用。

##### 常用连接

* 内连接

    `inner join`
    
    内连接是返回关联表间对应的数据。
    
    ```mysql
    select ... from `表名` [[as] 别名] inner join `表名` [[as] 别名] on `主表名`.公共字段名=`从表名`.公共字段名 ...;
    ``` 
    
* 外连接

    `left outer join` `right outer join`
    
    ```mysql
    select ... from `表名` [[as] 别名] left/right outer join `表名` [[as] 别名] on `主表名`.公共字段名=`从表名`.公共字段名 ...;
    ```
    
* 交叉连接

    `cross join`

* 自然连接

    `natural join` `natural left join` `natural right join`
    
    自然连接是不需要指定公共字段的，依据的是同名字段，并且查询集只会包含一个同名字段。
    
* `using(公共字段名)`

    ```mysql
     select ... from `表名` [[as] 别名] inner join `表名` [[as] 别名] using(公共字段名) ...;
    ```

### 子查询

##### 概述

子查询是用于通过多张数据表对其相关联的另一张数据表中的数据进行查询时使用。

##### 常用关键字

* `select ... where 字段名 in/not in(...) ...`

* `select ... where 字段名 逻辑运算符all/some/any(...) ...`

* `select ... where not exists/exists(...) ...`

### 用户管理

##### 创建

```mysql
create user '用户名'@'ip地址/%' identified by '密码';
```

##### 授予权限

```mysql
grant 权限名, .../all privileges on `数据库名`/ *.`表名`/ * to '用户名'@'ip地址/%';
```

##### 撤销权限

```mysql
revoke 权限名, .../all privileges on `数据库名`/ *.`表名`/ * from '用户名'@'ip地址/%';
```

##### 刷新权限

```mysql
flush privileges;
```

##### 查看权限

```mysql
show grants for '用户名'@'ip地址/%';
```

##### 删除

```mysql
drop user 用户名@ip地址/%;
```

### 常用语句

##### 判断语句

* `if`判断

    ```mysql
    if(条件语句, 条件语句成立时返回的结果, 条件语句不成立时返回的结果)
    ```

* `if-else`

    ```mysql
    if 条件语句 then
      ...
    elseif 条件语句 then
      ...
    ...
    else
      ...
    end if
    ```

##### 循环语句

```mysql
别名:while 条件语句 do
      ...
    end while
```

> 附：
>
> `iterable 别名;` `leave 别名;`