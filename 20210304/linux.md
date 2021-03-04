### 关机、重启

##### 关机

```shell script
shutdown -h 时:分 "提示信息"
shutdown -h +分 "提示信息"
shutdown -h now "提示信息"
```

##### 重启

```shell script
shutdown -r 时:分 "提示信息"
shutdown -r +分 "提示信息"
shutdown -r now "提示信息"
```

### 命令行前缀解析

```shell script
用户名@机器的名字:当前操作目录#/$
```

### 目录树状结构设置及查看

##### 目录树状结构设置

```shell script
sudo apt/yum [-y] install tree
```

##### 目录树状结构查看

```shell script
tree 目录路径
```

### `cd`命令

```shell script
pwd
cd /
cd ~  # /root/ /home/用户名/
cd .
cd ..
cd -
cd 目录路径
```

### `ls`命令

```shell script
ls -alh 目录路径
```

> 附：
>
> 文件类型 d l -
>
> 文件属性 [---][---][---]
>
> 子目录或子文件数量 注
>
> 拥有者、组名
>
> 文件大小
>
> 最后修改日期、时间
>
> 目录名或文件名

### `vim`的简单使用

##### 进入命令

```shell script
vim 文件路径+[n]
```

##### 光标命令

`i` `Esc` `o` `⬆️` `⬇️` `⬅️` `➡️`

##### 复制、粘贴、删除和撤销

`yy` `nyy` `p` `np` `dd` `ndd` `u`

##### 文档操作命令

`:` `w` `e` `q` `!`

##### 行号的设置、取消、`tab`缩进空格数和语法高亮的设置

```shell script
vim /etc/vimrc +
```

中写入

```shell script
set number
set nonumber
set tabstop=4
syntax on
```

##### 底行模式查找命令

```shell script
/关键字
:ns/被替换的关键字/替换的关键字[/g]
:%s/被替换的关键字/替换的关键字[/g]
```

### 目录或文件操作

##### 创建

* 文件

    ```shell script
    touch 文件路径 ...
    ```

* 目录

    ```shell script
    mkdir -p 目录名/...
    ```

##### 查找

* 目录或文件查找

    ```shell script
    find 目录路径 -name 目录名/文件名
    ```

* 程序查找

    ```shell script
    whereis 程序名
    ```

* 命令查找

    ```shell script
    which 命令
    ```

##### 拷贝、重命名

```shell script
cp -rfv 源路径 拷贝路径
```

##### 移动

```shell script
mv -fv 源路径 移动路径
```

##### 删除

```shell script
rm -rfv 源路径
```

### 外部查看文件内容

##### 查看文件内容

```shell script
cat -n 文件路径
head -n 文件路径
tail -n[f] 文件路径
```

##### 通过关键字查看文件指定内容

```shell script
grep --color -ncrE 关键字 文件路径
```

### 创建链接文件

##### 硬链接

* 概述

    硬链接是只能链接普通文件，并且源文件删除不会使硬链接失效。

* 创建

    ```shell script
    ln 源路径 链接路径
    ```

##### 软链接

* 概述

    软链接是既可以链接普通文件，也可以链接目录，但源文件删除会使软链接变成死链接。

* 创建

    ```shell script
    ln -s 源路径 链接路径
    ```

### 重定向

##### 概述

重定向是把原本要输出的内容转存到文件中。

##### 语句

* 转存

    ```shell script
    命令 > 文件路径
    ```

* 追加

    ```shell script
    命令 >> 文件路径
    ```

### 远程连接、主机信任设置和文件的上传、下载

##### 远程连接

* 概述

    `ssh`是一个远程登录协议，配置文件默认存放在`/etc/ssh/ssh_config`。

* 连接

    ```shell script
    ssh 用户名@ip地址
    ```

* 断开

    ```shell script
    exit
    ```

##### 主机信任设置

1. 家目录下执行

    ```shell script
    ssh-keygen -t rsa
    ```

2. 将公钥上传到对方主机的`～/.ssh/`目录中

    ```shell script
    scp 公钥路径 用户名@ip地址:~/.ssh/
    ```

3. 将上传的公钥重定向到`~/.ssh/authorized_keys`文件中。

##### 文件的上传、下载

* 上传

    ```shell script
    scp 源路径 用户名@ip地址:目标路径
    ```

* 下载

    ```shell script
    scp 用户名@ip地址:源路径 目标路径
    ```

### 压缩和解压

##### 压缩

```shell script
tar -czjvf 压缩包路径 源路径
```

##### 解压

```shell script
tar -xzjvf 压缩包路径 -C 解压路径
```

### 网卡操作

##### 查看网卡信息

```shell script
ifconfig
```

##### 测试`ip`地址是否畅通

```shell script
ping ip地址
```

### `yum/apt`命令

##### 源更新

```shell script
sudo apt/yum [-y] update
```

##### 安装

```shell script
sudo apt/yum [-y] install unit
```

##### 移除

```shell script
sudo apt/yum [-y] remove unit
```

### `ssh`协议的安装和服务相关命令

##### `ssh`协议的安装

```shell script
sudo apt/yum [-y] install openssh-server
```

##### 服务相关命令

```shell script
systemctl start/stop/restart/status unit
service unit start/stop/restart/status
```

### 常用端口号、清屏和开启或关闭防火墙

##### 常用端口号

```shell script
ssh 22
mongodb 27017
redis 6379
mysql 3306
http 80
https 443
```

##### 清屏

```shell script
clear
```

##### 开启或关闭防火墙

```shell script
systemctl start/stop iptables
service iptables start/stop
```

### 管道命令

##### 概述

管道命令是把前面命令的输出作为后面命令的输入。

##### 语句

```shell script
命令 | ...
```

### 查看内存状况、进程的管理和网络的管理

##### 查看内存状况

```shell script
free -h
```

##### 查看进程状况

```shell script
ps -eaf
```

##### 杀死进程

```shell script
kill -9 进程ID
```

##### 查看网络状况

```shell script
netstat -nt[u]lp
```

##### 查看哪些进程占用着某个端口号

```shell script
lsof -i:端口号
```

### 动态监控Linux系统整体状况

```shell script
top -csi
```

> 附：
>
> 当前系统已运行时长、当前登录系统的用户数量和当前系统平均负载情况
>
> 任务情况
>
> CPU情况
>
> 物理内存和交换分区情况
>
> 各进程情况

### 用户、用户组和文件所属者分配管理

##### 用户管理

* 增加

    ```shell script
    useradd -u 新用户id -g 已存在组id 登录用户名
    passwd 登录用户名
    ```

* 查看

    ```shell script
    cat -n /etc/passwd
    ```

* 切换

    ```shell script
    sudo -s
    su 登录用户名
    ```

* 退出

    ```shell script
    exit
    ```

* 修改

    ```shell script
    usermod -ugld 新数据 登录用户名
    ```

* 删除

    ```shell script
    userdel -r 登录用户名
    ```

##### 用户组管理

* 增加

    ```shell script
    groupadd -g 新组id 组名
    ```

* 查看

    ```shell script
    cat -n /etc/group
    ```

* 修改

    ```shell script
    groupmod -gn 新数据 组名
    ```

* 删除

    ```shell script
    groupdel 组名
    ```

##### 文件所属者分配管理

* 移交拥有者权限

    ```shell script
    chown 用户名 文件路径
    ```

* 移交组权限

    ```shell script
    chgrp 组名 文件路径
    ```

* 修改文件属性

    ```shell script
    chmod 属性值 文件路径
    ```

### 常用命令

##### `export`命令

* 概述

    `export`命令通常用于设置或查看系统变量。

* 设置

    ```shell script
    export 变量名=值
    ```

* 查看

    ```shell script
    export
    ```

###### `source`命令

* 概述

    `source`命令通常用于重新激活被修改的初始化文件。

* 结构

    ```shell script
    source 文件路径
    ```

##### `diff`命令

* 概述

    `diff`命令通常用于两个文件的差异比较。

* 结构

    ```shell script
    diff 文件路径 文件路径
    ```

### 日期、时间管理

##### 查看

```shell script
date ["+日期、时间格式"]
```

##### 设置

```shell script
date -s "四位数的年两位数的月两位数的日 两位数的时:两位数的分:两位数的秒"
```

### `history`命令

##### 查看历史命令

```shell script
history
```

##### 执行历史命令

```shell script
!命令编号
```

##### 清空历史命令

```shell script
history -c
```

### 元字符

##### `*`

表示任意一个字符。

##### `?`

表示任意多个字符。

### 文件合并和查看登录系统的用户

##### 文件合并

* 按行合并

    ```shell script
    cat 文件路径 文件路径
    ```

* 按列合并

    ```shell script
    paste 文件路径 文件路径
    ```

##### 查看登录系统的用户

```shell script
w
```