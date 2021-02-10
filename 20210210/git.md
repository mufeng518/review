### 基本配置

##### 配置用户名

```shell script
git config --global user.name "github用户名"
```

##### 配置邮箱

```shell script
git config --global user.email "github绑定的邮箱账号"
```

##### 查看当前Git的配置列表

```shell script
git config --list
```

##### 编辑Git的配置信息

* 全局

    ```shell script
    git config --global -e
    ```

* 当前

    ```shell script
    git config -e
    ```

### 版本库简介

##### 概述

版本库也被称为仓库，也可以理解成一个目录，版本库里面所有的目录或文件都可以被Git来管理，即版本库里面每个目录或文件的修改或删除，Git都可以来跟踪。

##### 创建

在一个合适的位置处案件一个空目录，并且在该目录下执行

```shell script
git init
```

##### 文件添加

```shell script
git add 工作区目录或文件路径 ...
```

##### 文件提交

```shell script
git commit -m "备注"
```

> 附：修改上一次提交的`备注`信息
>
> ```shell script
> git commit --amend -m "新备注"
> ```
>
> 注：
>
> 文件未被推送到远程仓库。

### 常用命令

##### 查看当前版本库的状态

```shell script
git status
```

> 注：
>
> 当版本库里面有目录或文件被修改或删除时，那么返回被修改或删除的目录或文件。

##### 查看提交的日志记录

```shell script
git log --pretty=oneline --abbrev-commit
```

##### 查看被修改的内容

```shell script
git diff
```

##### 版本回退

* 回退到前`n`个版本

    ```shell script
    git reset --hard HEAD~n
    ```

* 回退到指定版本

    ```shell script
    git reset --hard 版本号
    ```

##### 文件撤销或文件恢复

```shell script
git checkout -- 工作区目录或文件路径 ...
```

### 工作区、暂存区和版本库

##### 工作区

工作区是`.git`目录所在的目录。

##### 版本库

版本库是`.git`目录。

##### 版本库结构

* 暂存区

    暂存区是`.git/index`文件。

* `HEAD`

    `HEAD`是指向分支的指针。

* `master`

    `master`是版本库自动创建的一个分支。

### 本地仓库到远程仓库

##### 信任设置

```shell script
ssh-keygen -r rsa
```

##### 测试密钥

```shell script
ssh -T git@github.com
```

##### 创建远程仓库

##### 连接远程仓库

```shell script
git remote add origin 代码仓库地址
```

##### 垃取

```shell script
git pull origin master --allow-unrelated-histories
```

##### 推送

```shell script
git push origin master
```

##### 断开连接

```shell script
git remote rm origin
```

### 远程仓库到本地仓库

##### 克隆

```shell script
git clone [-b 分支名] 代码仓库地址
```

> 注：
>
> 当`-b 分支名`省略时，那么默认为拉取的是`master`分支。

##### 推送

```shell script
git push origin 分支名/标签名
```

##### 拉取

```shell script
git pull origin 分支名/标签名
```

### 分支

##### 优点

引入了分支以后，可以更好地解决各分支功能模块开发进度间的影响。

##### 创建

```shell script
git branch 分支名
```

##### 查看

```shell script
git branch -a
```

##### 切换

```shell script
git checkout 分支名
```

##### 创建并切换

```shell script
git checkout -b 分支名
```

##### 合并

```shell script
git merge 分支名
```

##### 删除

* 本地

    ```shell script
    git branch -d 分支名
    ```

* 远程

    ```shell script
    git push origin --delete 分支名
    ```

##### 一次性推送本地所有分支到远程仓库

```shell script
git push --all origin
```

### 标签

##### 创建

```shell script
git tag 标签名
```

##### 查看

```shell script
git tag
```

##### 切换

```shell script
git checkout 标签名
```

##### 删除

* 本地

    ```shell script
    git tag -d 标签名
    ```

* 远程

    ```shell script
    git push origin --delete 标签名
    ```

##### 给指定版本打标签

```shell script
git tag 标签名 版本号
```

##### 一次性推送本地所有标签到远程仓库

```shell script
git push origin --tags
```

### 贮藏代码

##### 贮藏代码

```shell script
git stash save "备注"
```

##### 查看贮藏列表

```shell script
git stash list
```

##### 恢复并删除贮藏列表中最近的贮藏

```shell script
git stash pop
```

##### 移除贮藏

* 单个

    ```shell script
    git stash drop 贮藏名
    ```

* 所有

    ```shell script
    git stash clear
    ```