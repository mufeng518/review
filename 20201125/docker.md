##### Docker概念

Docker是一个开源的应用容器引擎，通过Docker可以快速地构建一个轻量的、可移植的、自给自足的容器。

##### Docker优点

* 持续集成和持续交付

* 响应式部署和扩展

##### version编写

```yaml
version: 3
```

##### services编写

* 容器名

    指定容器名。
    
    ```yaml
    services:
      容器名:
    ```
    
    > 注：
    >
    > 此处的容器名是`docker-compose`定义的容器名，只适用于该`docker-compose`文件，与`docker container ls -a`看到的容器名不一定一致。

* `build`

    用于构建镜像文件。
    
    * 单个`Dockerfile`文件
    
        ```yaml
        services:
          容器名:
            build: Dockerfile文件的相对目录或绝对目录
        ```
    
    * 多个`Dockerfile`文件
    
        ```yaml
        services:
          容器名:
            build:
              context: Dockerfile文件的相对目录或绝对目录
              dockerfile: Dockerfile文件名
              args:
                变量名: 值
                - 变量名=值
                - 变量名
        ```

* `container_name`

    指定容器名。
    
    ```yaml
    services:
      容器名:
        container_name: 容器名
    ```

* `image`

    指定镜像名。
    
    ```yaml
    services:
      容器名:
        image: 仓库名:标签名
    ```

* `volumes`

    挂载本地目录下的指定目录或文件到容器目标地址中。
    
    ```yaml
    services:
      容器名:
        volumes: 宿主机目录或文件路径:容器目标路径
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

    暴露容器端口，但不会映射到宿主机，只能被连接的容器使用。
    
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

    指定连接的容器。
    
    ```yaml
    services:
      容器名:
        - 容器名
    ```

* `command`

    覆盖容器启动是默认执行的命令。
    
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