##### 容器

容器是一个镜像文件运行时的实体。

##### 登录

```shell
docker login [镜像仓库地址]
```

> 注：
>
> 当`镜像仓库地址`省略时，那么默认为`镜像仓库地址`为`DockerHub`。

##### 创建并运行容器

```shell
docker container run -dit --name "容器名" -p 宿主机端口号:容器端口号 镜像ID
```

##### 查看指定容器的进程信息

```shell
docker container top 容器ID
```

##### 查看指定容器的日志信息

```shell
docker container logs -tf 容器ID
```

##### 主机到容器

```shell
docker container cp 源路径 容器ID:目标路径
```