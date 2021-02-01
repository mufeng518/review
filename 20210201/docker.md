### 简介

##### 概念

Docker是一个开源的应用容器引擎，通过Docker可以快速地构建一个轻量的、可移植的、自给自足的容器。

##### 优点

1. 持续集成和持续交付；

2. 响应式部署和扩展。

##### Docker信息和版本查看

* 信息查看

    ```shell script
    docker info
    ```

* 版本查看

    ```shell script
    docker -v
    ```

### 基本概念

##### 仓库

仓库是一个存放镜像文件的地方。

##### 镜像

镜像是一个特殊的文件系统。

##### 容器

容器是一个镜像文件运行时的实体。

### 仓库操作

##### 登录

```shell script
docker login -u 用户名 -p 密码 [镜像仓库地址]
```

> 注：
>
> 当`镜像仓库地址`省略时，那么默认为`镜像仓库地址`为`DockerHub`。

##### 注销

```shell script
docker logout [镜像仓库地址]
```

### 镜像操作

##### 查找

```shell script
docker search [用户名/]仓库名[:标签名]
```

##### 拉取

```shell script
docker image pull [镜像仓库地址/][用户名/]仓库名[:标签名]
```

##### 推送

```shell script
docker image push [镜像仓库地址/][用户名/]仓库名:标签名
```

##### 查看本地镜像列表

```shell script
docker images
# 或
docker image ls -a
```

##### 删除本地镜像

* 单个

    ```shell script
    docker image rm -f 镜像ID
    ```
    
* 所有

    ```shell script
    docker image rm -f $(docker images -q)
    ```

##### 查看指定镜像创建容器的历史记录

```shell script
docker image history 镜像ID
```

##### 标记本地镜像(将其归入某一仓库)

```shell script
docker image tag 仓库名:标签名 [镜像仓库地址/][用户名/]仓库名:标签名
```

### 容器基本操作

##### 创建并运行

```shell script
docker container run --name 容器名 -p 宿主机端口号:容器端口号 -v 宿主机目录:容器目录 -dit 镜像ID [命令]
```

##### 查看

```shell script
docker container ls -a
```

##### 启动、停止、终止或重启

* 单个

    ```shell script
    docker container start/stop/kill/restart 容器ID
    ```

* 所有

    ```shell script
    docker container start/stop/kill/restart $(docker container ps -aq)
    ```

##### 删除

* 单个

    ```shell script
    docker container rm -f 容器ID
    ```

* 所有

    ```shell script
    docker container rm -f $(docker container ps -aq)
    ```

### 容器其他操作

##### 查看指定容器的进程信息

```shell script
docker container ps
```

##### 查看指定容器的日志信息

```shell script
docker contaienr logs -tf 容器ID
```

##### 查看指定容器的端口映射

```shell script
docker container port 容器ID
```

##### 在运行的容器中执行命令

```shell script
docker container exec -dit 容器ID 命令
```

### 容器与主机间的数据拷贝

##### 主机到容器

```shell script
docker container cp 源路径 容器ID:目标路径
```

##### 容器到主机

```shell script
docker container cp 容器ID:源路径 目标路径
```

### 容器的导出和导入来定制镜像

##### 导出

```shell script
docker export 容器ID > ./文件名.tar
```

##### 导入

```shell script
docker import ./文件名.tar 仓库名:标签名
```

### `docker commit`来定制镜像

```shell script
docker commit --author "作者" --message "信息" 容器ID 仓库名:标签名
```

### 镜像的导出和导入来定制镜像

##### 导出

```shell script
docker save 仓库名:标签名 > ./文件名.tar
```

##### 导入

```shell script
docker load -i ./文件名.tar
```

### `Dockerfile`文件来定制镜像

##### 常用指令

* `FROM`
    
    拉取基础镜像文件。
    
    ```dockerfile
    FROM [镜像仓库地址/][用户名/]仓库名[:标签名]
    ```
  
* `MAINTAINER`

    指定维护者。
    
    ```dockerfile
    MAINTAINER 维护着信息
    ```
  
* `COPY`

    将工作区的目录或文件拷贝到容器镜像中。
    
    ```dockerfile
    COPY 工作区源路径 ... 目标路径
    ```
  
* `WORKDIR`

    指定工作目录。
    
    ```dockerfile
    WORKDIR 目录路径
    ```
  
* `RUN`
    
    `docker build`时执行的操作。
    
    ```dockerfile
    RUN 命令\
      && 命令\
      && ...
    ```
  
* `EXPOSE`

    暴露容器映射到宿主机的端口号。
    
    ```dockerfile
    EXPOSE 端口号
    ```
  
* `CMD`

    `docker run`时执行的操作。
    
    ```dockerfile
    CMD 命令\
      && 命令\
      && ...
    ```
  
* `ENV`

    设置环境变量。
    
    ```dockerfile
    ENV 变量名=值 ...
    ```

##### 构建

```shell script
docker build [-f Dockerfile文件路径] -t 仓库名:标签名 .
```

### `docker-compose`文件编写规则

##### `version`编写

```yaml
version: 3
```

##### `services`编写

* 容器名

    指定容器名。
    
    ```yaml
    services:
      容器名:
    ```
  
    > 注：
    > 
    > 此处的容器名是`docker-compose`文件定义的容器名，只适用于该`docker-compose`文件，与`docker container ls -a`看到的容器名不一定一致。

* `build`

    * 单个Dockerfile文件
    
        ```yaml
        services:
          容器名:
            build: Dockerfile文件所在的相对目录或绝对目录
        ```
    
    * 多个Dockerfile文件
    
        ```yaml
        services:
          容器名:
            build:
              context: Dockerfile文件所在的相对目录或绝对目录
              dockerfile: Dockerfile文件名
              args:
                变量名: 值
                - 变量名=值
                - 变量名
        ```

* `image`

    指定镜像名。
    
    ```yaml
    services:
      容器名:
        image: 仓库名:标签名
    ```

* `container_name`

    指定容器名。
    
    ```yaml
    services:
      容器名:
        container_name: 容器名
    ```

* `volumes`

    挂载本地目录下的指定目录或文件到容器目标地址中。
    
    ```yaml
    services:
      容器名:
        volumes:
          - 宿主机目录或文件路径:容器目标路径
    ```

* `environment`

    设置环境变量。
    
    ```yaml
    services:
      容器名:
        environment:
          变量名: 值
          - 变量名=值
    ```

* `ports`

    指定端口映射。
    
    ```yaml
    services:
      容器名:
        ports:
          - "宿主机端口号:容器端口号"
    ```

* `expose`

    指定容器端口号，但不会映射到宿主机，只能被连接的容器使用。
    
    ```yaml
    services:
      容器名:
        expose:
          - 端口号
    ```

* `depends_on`

    指定依赖。
    
    ```yaml
    services:
      容器名:
        depends_on:
          - 容器名
    ```

* `links`

    指定连接的容器，并标记连接容器的ip地址到该容器中。
    
    ```yaml
    services:
      容器名:
        links:
          - 容器名
    ```

* `command`

    覆盖启动时默认执行的命令。
    
    ```yaml
    services:
      容器名:
        command: 命令
    ```

* `restart`

    指定重启模式。
    
    ```yaml
    services:
      容器名:
        restart: no/always
    ```

* `networks`

    指定要加入的网络。
    
    ```yaml
    services:
      容器名:
        networks:
          - 网络名
  
    networks:
      网络名:
        driver: bridge
    ```