### Go

##### 分类

* 解释性字符串

    解释性字符串是用英文状态下的双引号括起来的标识符。

* 非解释性字符串

    非解释性字符串是用英文状态下的反引号括起来的标识符。

##### 指针概念

指针是指向某一个值的内存地址。

> 注：
>
> 指针不可以指向字面量或常量的内存地址。

##### 指针赋值

```go
指针变量名 = &变量名/指针变量名
```

### Docker

##### 登录

```shell
docker login -u 用户名 -p 密码 [镜像仓库地址/]用户名/仓库名:标签名
```

> 注：
>
> 当`镜像仓库地址`省略时，那么默认为`镜像仓库地址`为Docker Hub的地址。

##### 注销

```shell
docker logout [镜像仓库地址/]用户名/仓库名:标签名
```

##### 查找

```shell
docker search 用户名/仓库名:标签名
```

##### 主机到容器

```shell
docker container cp 源路径 容器id:目标路径
```

##### 导出

```shell
docker export 容器id > ./文件名.tar
```

##### 导入

```shell
docker import ./文件名.tar 仓库名:标签名
```

##### 常用指令

* `FROM`

    拉取基础镜像

    ```dockerfile
    FROM [镜像仓库地址/]用户名/仓库名:标签名
    ```

* `COPY`

    将工作区的文件拷贝到容器镜像中。

    ```dockerfile
    COPY 工作区文件路径1 ... 目标路径
    ```

* `WORKDIR`

    指定工作目录。

    ```dockerfile
    WORKDIR 目录路径
    ```

* `RUN`

    `docker build`时执行的操作。

    ```dockerfile
    RUN 命令1 \
        && 命令2 \
        ...
    ```

* `EXPOSE`

    暴露容器映射到宿主机的端口号。

    ```dockerfile
    EXPOSE 端口号
    ```

* `CMD`

    `docker run`时执行的操作。

    ```dockerfile
    CMD 命令1 \
        && 命令2 \
        ...
    ```

##### 构建

```shell
docker build [-f Dockerfile文件路径] -t [镜像仓库地址/]用户名/仓库名:标签名 .
```

### Git

##### 版本库简介

版本库也被称为仓库，也可以理解成一个目录，版本库里面所有的文件都可以被Git来管理，即每个文件的修改或删除，Git都可以来跟踪。

##### 查看提交的历史记录

```shell
git log --pretty=oneline --abbrev-commit
```

##### 连接远程仓库

```shell
git remote add origin 远程仓库地址
```

##### 断开连接

```shell
git remote rm origin
```

##### 删除分支

* 本地

    ```shell
    git branch -d 分支名
    ```

* 远程

    ```shell
    git push origin --delete 分支名
    ```

##### 一次性将本地所有分支推送到远程仓库

```shell
git push --all origin
```

##### 一次性将本地所有标签推送到远程仓库

```shell
git push origin --tags
```

### Linux

##### 在指定时间关机

```shell
shutdown -h 时:分 "提示"
```

##### 命令行前缀解析

```shell
用户名@机器的名字:当前操作目录#/$
```

##### 行号的设置、取消和`tab`缩进空格数的设置

```shell
vim /etc/vimrc +
```

中写入

```shell
set number
set nonumber
set tabstop=4
```

##### 底行模式查找命令

```shell
/关键字
:ns/被替换的关键字/替换的关键字[/g]
:%s/被替换的关键字/替换的关键字[/g]
```

##### 查找

* 文件查找

    ```shell
    find 目录路径 -name 文件名/目录名
    ```

* 程序查找

    ```shell
    whereis 程序名
    ```

* 命令查找

    ```shell
    which 命令
    ```

##### 通过关键字查看文件指定内容

```shell
grep --color -ncrE 关键字 文件路径
```

##### 硬链接

* 概述

    硬链接是只能链接普通文件，并且源文件删除不会使硬链接失效。

* 创建

    ```shell
    ln 源路径 链接路径
    ```

##### 软链接

* 概述

    软链接是既可以链接普通文件也可以链接目录，但源文件删除会使软链接变成死链接。

* 创建

    ```shell
    ln -s 源路径 链接路径
    ```

##### `ssh`的安装

```shell
yum/sudo apt [-y] install openssh-server
```

##### 常用端口号

```shell
ssh 22
mysql 3306
redis 6379
mongodb 27017
http 80
https 443
```

##### 开启或关闭防火墙

```shell
systemctl start/stop iptables
```

##### 查看内存状况

```shell
free -h
```

##### 查看进程情况

```shell
ps -eaf
```

##### 结束进程

```shell
kill -9 进程id
```

##### 查看网络状况

```shell
netstat -nt[u]lp
```

##### 查看哪些进程占用着某个端口号

```shell
lsof -i:端口号
```

##### 动态监控Linux系统整体状况

```shell
top -csi
```

> 当前系统已运行时长、当前正登录该系统的用户数量、当前系统平均负载情况
>
> CPU情况
>
> 任务情况
>
> 物理内存、交换分区情况
>
> 各进程情况