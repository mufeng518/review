### 虚拟化技术

##### 概念

虚拟化技术是一种计算机硬件资源管理技术。

##### 作用

虚拟化技术的作用是将计算机中的各种硬件资源(比如服务器、CPU、内存等)予以抽象和转换后呈现出一套新的硬件资源环境，在这一套新的硬件资源环境中我们可以安装操作系统或部署应用等。

##### 分类

* 硬件虚拟化

    硬件虚拟化是运行在硬件之上的虚拟化技术，它的核心技术是Hypervisor(Hypervisor是运行在基础物理服务器硬件之上的软件层，可以将计算机中的各种硬件资源进行虚拟化)。

* 操作系统虚拟化

    操作系统虚拟化是运行在操作系统之上的虚拟化技术，也被称为容器化技术，它的核心技术是将运行在同一个操作系统中的多个不同进程打包到一个密闭的容器里。

##### 硬件虚拟化技术的优缺点

* 优点

    一台物理服务器可以虚拟化出多台虚拟服务器。

* 缺点

    1. 每虚拟化出一台虚拟服务器，都会创建一套操作系统，这样会导致计算机硬件资源极大消耗。
    
    2. 环境兼容性差。

### Docker简介

##### 概念

1. Docker是基于LXC来实现操作系统虚拟化和容器进程间的隔离。

    > 附：
    >
    > LXC：是Linux Container的简称，是一种内核虚拟化技术。
    >
    > LXC：
    >
    > 1. 提供了轻量级的虚拟化，以便进程和资源的隔离；
    >  
    > 2. 与宿主机共享一个内核。

2. Docker是一个开源的应用容器引擎，通过Docker可以快速地构建一个轻量的、可移植的、自给自足的容器。

3. Docker可以让技术开发者更快速地将自己的应用及其依赖打包到一个可移植的容器里，并且打包好的容器可以发布到任何流行的服务器上运行。

##### Docker和虚拟机的区别

启动 秒级 分钟级

性能 接近原生 弱于原生

操作系统 与宿主机共享OS 在宿主机OS上运行虚拟机OS

硬盘使用量 一般为Mb 一般为Gb

系统支持量 单机支持上千个 一般为几十个

##### 优点

1. 持续集成和持续交付；

2. 响应式部署和扩展。

##### Docker架构模式

Docker的架构模式是CS架构模式，是通过调用远程API来创建和管理容器。

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

##### 仓库的分类

本地仓库和远程仓库。

##### 镜像

镜像是由多层文件系统叠加构成的(最低层是引导文件系统bootfs，第二层是root文件系统rootfs，在其之上又有多层其他文件系统)。

##### 镜像的特点

只读的。

##### 容器

容器是一个镜像文件运行时的实体。

##### 容器的特点

支持读写。

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

##### 查看本地所有镜像

```shell script
docker image ls -a
# 或
docker images
```

##### 查看本地指定镜像的所有版本号

```shell script
docker images 仓库名
```

##### 查看本地指定镜像的所有ID

```shell script
docker images 仓库名 -q
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
docker container run --name 容器名 --rm --networks 网桥名 -dit -e 变量名=值 -p [宿主机ip地址:]端口号:容器端口号 镜像ID [命令]
```

> 注：
>
> 当创建容器时，如果制定了网桥，那么与该网桥相关联的所有容器间都可以使用容器名进行通信。

##### 数据卷使用

* 自定义数据卷目录

    ```shell script
    docker container run -v 数据卷名/宿主机目录:容器目录 镜像ID
    ```

* 自动数据卷目录

    ```shell script
    docker container run -v 数据卷名:容器目录 镜像ID
    ```

##### 自定义数据卷目录和自动数据卷目录的区别

* 自定义数据卷目录

    进行挂载时，会清空挂载点目录中的所有目录或文件。

* 自动数据卷目录

    进行挂载时，Docker引擎会自动创建该数据，同时会将该数据卷映射到宿主机中的某个目录，并将该数据卷所对应容器目录中所有的目录或文件都拷贝到该数据卷所映射的宿主机目录中。

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

##### 查看指定宿主机容器的进程信息

* 查看处于运行状态的容器的进程信息

    ```shell script
    docker container ps
    ```

* 查看所有容器(包括停止的容器)的进程信息

    ```shell script
    docker container ps -aq
    ```

##### 查看指定容器内部的进程信息

```shell script
docker container top 容器ID
```

##### 查看指定容器的日志信息

```shell script
docker container logs -tf 容器ID
```

##### 查看指定容器的端口映射

```shell script
docker container port 容器ID
```

##### 进入容器

```shell script
docker container exec -it 容器ID bash
```

##### 退出容器

```shell script
exit
```

##### 查看指定容器内部细节

```shell script
docker container inspect 容器ID
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

### 容器通信机制

##### 容器与宿主机间的通信机制

Docker引擎启动的同时会自动在宿主机上创建一个网桥(默认为`bridge`)，当在该网桥创建容器时，会自动创建一对`veth pair`接口(当数据包发送到其中一个接口时，另一个接口也会收到相同的数据包)，这对接口一个被挂载在容器内部，即`eth0`，一个被挂载在网桥上。

##### 容器与容器间的通信机制

Docker引擎启动的同时会被随机分配一个宿主机中未占用的私有网段中的ip地址给网桥接口使用，此后在该网桥创建的所有容器都会被随机分配一个同一网段中的ip地址。

##### 网桥使用

当使用网桥来实现容器间的通信时，那么一般都是站在应用的角度上出发，即创建各自应用的网桥。

### 网桥操作

##### 创建

```shell script
docker network create [-d bridge] 网桥名
```

##### 查看

```shell script
docker network ls
```

##### 删除

```shell script
docker network rm 网桥名
```

##### 查看指定网桥细节

```shell script
docker network inspect 网桥名
```

### 数据卷操作

##### 作用

数据卷的作用是用来实现宿主机与容器间的数据共享。

##### 创建

```shell script
docker volume create --name 数据卷名
```

##### 查看

```shell script
docker volume ls
```

##### 删除

```shell script
docker volume rm 数据卷名
```

##### 查看指定数据卷的细节

```shell script
docker volume inspect 数据卷名
```

### `Dockerfile`文件来定制镜像

##### 常用指令

* `FROM`

    拉取基础镜像文件。
    
    ```dockerfile
    FROM [镜像仓库地址/][用户名/]仓库名[:标签名]
    ```
  
* `ENV`

    设置容器中的环境变量。
    
    ```dockerfile
    ENV 变量名=值 ...
    ```
  
* `ADD`

    将Context目录中指定的`tar`包(自动解压)、url连接(自动下载，但不解压)添加到容器镜像中。
    
    ```dockerfile
    ADD 宿主机tar包路径/url连接 ... 容器目标路径
    ```
  
* `COPY`

    将Context目录中指定的目录或文件拷贝到容器镜像中。
    
    ```dockerfile
    COPY 目录或文件路径 ... 容器目标路径
    ```

* `WORKDIR`

    指定进入容器时默认的目录。
    
    ```dockerfile
    WORKDIR 容器目录路径
    ```
  
* `RUN`

    `docker build`时容器内执行的操作。
    
    ```dockerfile
    RUN ["命令", "参数", ...]
    ```
  
* `EXPOSE`

    暴露容器内启动的应用映射到宿主机的端口号。
    
    ```dockerfile
    EXPOSE 端口号 ...
    ```
  
* `ENTRYPOINT`

    `docker run`时容器内执行的操作，一般为不可变的操作，也可以接受`CMD`传进来的参数，并将其放置到数组的末端。
    
    ```dockerfile
    ENTRYPOINT ["命令", "参数", ...]
    ```
  
* `CMD`

    `docker run`时容器内执行的操作，一般为可变的操作。
    
    ```dockerfile
    CMD [["命令", ]"参数", ...]
    ```
  
    > 注：
    >
    > 一个Dockerfile文件只允许有一条`CMD`指令生效，当一个Dockerfile文件存在多条`CMD`指令时，只会生效最后一条`CMD`指令。

##### 构建

```dockerfile
docker build [-f Dockerfile文件路径] -t 仓库名:标签名 .
```

### `docker-compose`文件编写规则

##### 作用

`docker-compose`的作用是用来实现对容器集群进行编排。

##### `version`编写

```yaml
version: "3.0"
```

##### `services`编写

* 服务名

    指定服务名。
    
    ```yaml
    services:
      服务名:
    ```

* `build`

    用于构建镜像文件。
    
    ```yaml
    services:
      服务名:
        build:
          context: Context目录路径
          dockerfile: Dockerfile文件名
    ```

* `image`

    指定镜像名。
    
    ```yaml
    services:
      服务名:
        image: 仓库名:标签名
    ```

* `container_name`

    指定容器名。
    
    ```yaml
    services:
      服务名:
        container_name: 容器名
    ```

* `networks`

    指定网桥。

    ```yaml
    services:
      服务名:
        networks:
          - 网桥名
          - ...
  
    networks:
      网桥名:
        driver: bridge
        external: true/false
    ```

* `env_file`

    通过`.env`文件来设置容器内的环境变量。
    
    ```yaml
    services:
      服务名:
        env_file:
          - .env文件路径
          - ...
    ```

* `enviroment`

    设置容器内的环境变量。
    
    ```yaml
    services:
      服务名:
        environment:
          变量名: 值
          - 变量名=值
          - ...
    ```

* `ports`

    指定端口映射。
    
    ```yaml
    services:
      服务名:
        ports:
          - "宿主机端口号:容器端口号"
          - ...
    ```

* `expose`

    暴露容器内启动的应用的端口号，但不会映射到宿主机，只能被连接的容器使用。
    
    ```yaml
    services:
      服务名:
        expose:
          - 端口号
          - ...
    ```

* `volumes`

    指定数据卷。
    
    ```yaml
    services:
      服务名:
        volumes:
          - 数据卷名/宿主机目录:容器目录
          - ...
  
    volumes:
      数据卷名:
        external: true/false
    ```

* `restart`

    指定重启模式。
    
    ```yaml
    services:
      服务名:
        restart: no/always
    ```

* `command`

    指定容器启动时默认执行的命令(会覆盖掉Dockerfile中的`CMD`命令)。
    
    ```yaml
    services:
      服务名:
        command: 命令
    ```

* `depends_on`

    指定依赖。
    
    ```yaml
    services:
      服务名:
        depends_on:
          - 容器名
          - ...
    ```

* `links`

    指定连接的容器。
    
    ```yaml
    services:
      服务名:
        links:
          - 容器名
          - ...
    ```

* `healthcheck`

    检测容器与Docker引擎的连接是否正常。
    
    ```yaml
    services:
      服务名:
        healthcheck:
          test: ["cmd", "curl" , "-f", "宿主机ip地址"]
          interval: 间隔时间
          timeout: 超时时间
          retries: 重试次数
    ```

* `ulimits`

    设置容器内的最大进程数和文件句柄数。
    
    ```yaml
    services:
      服务名:
        ulimits:
          nproc: 最大进程数
          nofile:
            soft: 文件句柄数(软限制，不可以超过硬限制)
            hard: 文件句柄数(硬限制)
    ```

### `docker-compose`操作

##### 前提

执行`docker-compose`操作指令的目录必须是`docker-compose.yml`文件所在的目录。

##### 启动

```shell script
docker-compose up [-d]
```

##### 停止和删除创建的网桥

```shell script
docker-compose down
```

##### 列出当前`docker-compose`文件所运行的所有容器的进程信息

```shell script
docker-compose ps
```

##### 列出当前`docker-compose`文件所运行的各个容器内的进程信息

```shell script
docker-compose top
```