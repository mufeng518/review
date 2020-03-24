### 基本配置

##### 配置用户名

```shell
git config --global user.name "github用户名"
```

##### 配置邮箱

```shell
git config --global user.email "github绑定的邮箱账号"
```

##### 查看Git的全剧配置

```shell
cat -n ~/.gitconfig
```

### 版本库简介

##### 概述

版本库也被称为仓库，也可以理解成一个目录，版本库里面所有的文件都可以被Git来管理，即版本库里面每个文件的修改或删除，Git都可以来跟踪。

##### 创建

在一个合适的位置创建一个空目录，并且在该目录下执行

```shell
git init
```

##### 文件添加

* 将文件添加到暂存区

    ```shell
    git add 工作区文件路径
    ```

* 将文件提交到版本库

    ```shell
    git commit -m "备注"
    ```

### 常用命令

##### 查看当前版本库的状态

```shell
git status
```

> 注：
>
> 当版本库里面的未见有被修改或删除时，那么返回被修改或删除的文件。

##### 查看提交的历史记录

```shell
git log --pretty=oneline --abbrev-commit
```

##### 查看被修改的内容

```shell
git diff
```

##### 版本回退

* 回退到前`n`个版本

    ```shell
    git reset --hard HEAD~n
    ```

* 回退到指定版本

    ```shell
    git reset --hard 版本号
    ```

##### 文件撤销或文件恢复

```shell
git checkout -- 工作区文件路径
```

> 注：
>
> 当文件被修改后未被添加到暂存区时，那么撤销后将会回退到最后一次`git commit`时的状态，当文件被添加到暂存区后又被修改时，那么撤销后将会回退到最后一次`git add`时的状态。

### 工作区、暂存区和版本库

##### 工作区

工作区是`.git`目录所在的目录。

##### 版本库

版本库是`.git`目录

##### 版本库结构

* 暂存区

    暂存区是`.git/index`文件。

* `HEAD`

    `HEAD`是指向分支的指针。

* `master`

    `master`是版本库自动创建的分支。

### 本地仓库到远程仓库

##### 信任设置

```shell
ssh-keygen -t rsa
```

##### 测试密钥

```shell
ssh -T git@github.com
```

##### 创建远程仓库

##### 连接远程仓库

```shell
git remote add origin 远程仓库地址
```

##### 拉取

```shell
git pull origin master --allow-unrelated-histories
```

##### 推送

```shell
git push origin master
```

##### 断开连接

```shell
git remote rm origin
```

### 远程仓库到本地仓库

##### 克隆

```shell
git clone [-b 分支名] origin 远程仓库地址
```

> 注：
>
> 当`-b 分支名`省略时，那么默认为拉取的是`master`分支。

##### 推送

```shell
git push origin 分支名/标签名
```

##### 拉取

```shell
git pull origin 分支名/标签名
```

### 分支

##### 优点

当引入了分支以后，可以更好地解决各功能模块开发进度间的影响。

##### 创建

```shell
git branch 分支名
```

##### 查看

```shell
git branch -a
```

##### 切换

```shell
git checkout 分支名
```

##### 创建并切换

```shell
git checkout -b 分支名
```

##### 合并

```shell
git merge 分支名
```

##### 删除

* 本地

    ```shell
    git branch -d 分支名
    ```

* 远程

    ```shell
    git remote origin --delete 分支名
    ```

##### 一次性推送本地所有分支到远程仓库

```shell
git push --all origin
```

### 标签

##### 创建

```shell
git tag 标签名
```

##### 查看

```shell
git tag
```

##### 切换

```shell
git checkout 标签名
```

##### 删除

* 本地

    ```shell
    git tag -d 标签名
    ```

* 远程

    ```shell
    git push origin --delete 标签名
    ```

##### 给指定版本打标签

```shell
git tag 标签名 版本号
```

##### 一次性推送本地所有标签到远程仓库

```shell
git push origin --tags
```

### 贮藏代码

##### 贮藏代码

```shell
git stash
```

##### 查看贮藏列表

```shell
git stash list
```

##### 恢复并删除贮藏列表中最近的贮藏

```shell
git stash pop
```