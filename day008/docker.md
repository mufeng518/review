### 基本概念

##### 镜像

镜像是一个特殊的文件系统。

##### 容器

容器是一个镜像文件运行时的实体。

##### 仓库

仓库是一个存放镜像文件的地方。

### 仓库操作

##### 登录

```shell
docker login -u 用户名 -p 密码 [镜像仓库地址/]用户名/仓库名:标签名
```

##### 注销

```shell
docker logout [镜像仓库地址/]用户名/仓库名:标签名
```

### 镜像操作

##### 查找

```shell
docker search 仓库名:标签名
```

##### 拉取

```shell
docker iamge pull [镜像仓库地址/]用户名/仓库名:标签名
```

##### 推送

```shell
docker image push [镜像仓库地址/]用户名/仓库名:标签名
```

##### 查看本地镜像列表

```shell
docker image ls -a
```

##### 删除本地镜像

```shell
docker image rm -f 镜像id
```

##### 查看指定镜像创建容器的历史记录

```shell
docker image history 镜像id
```

##### 标记本地镜像(将其归入某一仓库)

```shell
docker image tag 仓库名:标签名 [镜像仓库地址/]用户名/仓库名:标签名
```

### 容器基本操作

##### 创建并运行

```shell
docker container run -dit -p 宿主机端口号:容器端口号 --name 容器名 镜像id
```

##### 查看

```shell
docker container ls -a
```

##### 启动、停止、终止或重启

```shell
docker container start/stop/kill/restart 容器id
```

##### 删除

```shell
docker container rm -f 容器id
```

### 容器其他操作

##### 查看指定容器的进程信息

```shell
docker container top 容器id
```

##### 查看指定容器的日志信

```shell
docker container logs -tf --tail n 容器id
```

##### 查看指定容器的端口映射

```shell
docker container port 容器id
```

##### 在运行的容器中执行命令

```shell
docker container exec -it 容器id [命令]
```

### 容器与主机间的数据拷贝

##### 主机到容器

```shell
docker container cp 源路径 容器id:目标路径
```

##### 容器到主机

```shell
docker container cp 容器id:源路径 目标路径
```

### 容器的导出和导入来定制镜像

##### 导出

```shell
docker export 容器id > ./文件名.tar
```

##### 导入

```shell
docker import ./文件名.tar 仓库名:标签名
```

### `docker commit`来定制镜像

```shell
docker commit --author "作者" --message "备注" 容器id 仓库名:标签名
```

### `Dockerfile`文件来定制镜像

##### 常用指令

* `FROM`

    拉取基础镜像。

    ```dockerfile
    FROM [镜像仓库地址/]用户名/仓库名:标签名
    ```

* `COPY`

    将工作区文件拷贝到容器镜像中。

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

    `docker run`时执行的命令

    ```dockerfile 
    CMD 命令1 \
        && 命令2 \
        ...
    ```

##### 构建

```shell
docker build [-f Dockerfile文件路径] -t [镜像仓库地址/]用户名/仓库名:标签名 .
```