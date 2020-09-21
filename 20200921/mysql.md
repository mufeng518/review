### 用户管理

##### 创建

```mysql
create user '用户名'@'ip地址/%' identified by '密码';
```

##### 授予权限

```mysql
grant 权限名, .../all privileges on `数据库名`/ *.`表名`/ * to '用户名';
```

##### 撤销权限

```mysql
revoke 权限名, .../all privileges on `数据库名`/ *.`表名`/ * from '用户名';
```

##### 刷新权限

```mysql
flush privileges;
```

##### 查看权限

```mysql
show grants for 用户名@ip地址;
```

##### 删除

```mysql
drop user '用户名'@'ip地址/%';
```

### 常用语句

##### 判断语句

* `if`判断

    ```mysql
    if(条件语句, 条件语句返回true时返回的结果, 条件语句返回false时返回的结果)
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
> `iterable 别名;`
>
> `leave 别名;`