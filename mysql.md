### MySQL简介

##### SQL概述

##### MySQL优化范围

##### SQL注入

### `innodb`和`myisam`的区别

### 字符集和校对集

##### 字符集的使用环境

##### 校对集

* 概述

* 查看当前MySQL系统支持的校对集

* 分类

### 字段类型

##### 整型

##### 无符号的

##### 零填充

##### 浮点型

##### 字符串类型

##### 枚举类型

* 优点

* 结构

* 索引的计算方式

##### 集合类型

* 结构

* 索引的计算方式

* 为什么实际开发中一般不使用集合类型

* 多选框的问题该如何解决

##### 日期时间类型

##### 布尔类型

### 完整性约束条件

##### 空或非空

##### 默认值

##### 自增长

##### 备注

### 数据完整性

### 索引

##### 适用范围

##### 优缺点

* 优点

* 缺点

##### 索引类型

##### 创建

* 建表时添加

* 建表后添加

##### 查看指定表的索引

##### 删除

### 事务

##### 概述

##### 特性

##### 事务的开启和结束

* 开启事务

* 结束事务

    * 查看当前MySQL系统的事务提交机制
    
    * 临时修改当前MySQL系统的事务提交机制
    
### 实体间的关系和数据库设计

##### 实体间的关系

##### 数据库三范式

* 第一范式

* 第二范式

* 第三范式

### 视图

##### 概述

##### 创建

##### 查看

* 查看所有视图

* 查看建视图语句

* 查看视图结构

##### 修改

##### 删除

### 触发器

##### 概述

##### 类型

##### 创建

* 为什么必须要更改定界符

* `old`表和`new`表

* `old`表和`new`表的共同特征

##### 查看

* 查看所有触发器

* 查看建触发器语句

##### 删除

### 存储过程

##### 概述

##### 创建

##### 参数的分类

* 输入参数

* 输出参数

* 输入输出参数

##### 调用

* 输入调用

* 输出调用

* 输入输出调用

##### 变量的分类

* 系统变量

* 全局变量

* 局部变量

##### 变量的赋值

##### 查看

* 查看存储过程状态

* 查看建存储过程语句

##### 删除

### 函数

##### 创建

* 查看当前MySQL系统的信任函数创建者机制

* 临时修改当前MySQL系统的信任函数创建者机制

##### 调用

##### 查看

* 查看函数状态

* 查看建函数语句

##### 删除

### MySQL基本操作

##### 连接MySQL服务器

##### 断开连接

### 数据库基本操作

##### 创建

##### 使用

##### 查看

* 查看所有数据库

* 查看建数据库语句

* 查看当前数据库的数据库名

##### 删除

### 数据表基本操作

##### 创建

##### 查看

* 查看所有数据表

* 查看建表语句

* 查看表结构

##### 修改

* 修改表名

* 修改引擎

* 修改字符集

* 修改校对集

* 增加一个新字段

* 修改字段名

* 修改字段类型

##### 复制 

* 复制表结构(不包含主键)和表数据

* 只复制表结构(包含主键)

##### 移动

##### 删除

* 删除数据表

* 删除数据表中指定字段

### 数据基本操作

##### 插入

* 全列插入

* 缺省插入

##### 查询

* 基本查询

* 消除重复行

* 聚合查询

* `where`查询

    * 算术运算符
    
    * 比较运算符
    
    * 逻辑运算符
    
    * 模糊查询
    
    * 范围查询
    
    * 空值或非空值查询

* 分组查询

* 排序

* 分页查询

##### 更新

##### 删除

* 保留`id`(为后期数据恢复做准备)

* 不保留`id`(是先销毁数据表，再按照原来的建表语句重建数据表)

### 外键

##### 概述

##### 特点

##### 添加

* 建表时添加

* 建表后添加

##### 删除

### 联合查询

##### 概述

##### 结构

### 多表查询

##### 概述

##### 常用连接

### 子查询

##### 概述

##### 常用关键字

### 用户管理

##### 创建

##### 授予权限

##### 撤销权限

##### 刷新权限

##### 查看权限

##### 删除

### 常用语句

##### 判断语句

* `if`判断

* `if-else`

##### 循环语句