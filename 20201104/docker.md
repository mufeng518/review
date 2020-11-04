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
    > 此处的`容器名`是`docker-compose`文件定义的服务(容器)名，只适用于该`docker-compose`文件，与`docker container ls -a`看到的容器名不一定一致。

* `build`

    用于构建镜像。
    
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
    
* `ports`

    指定端口映射。
    
    ```yaml
    services:
      容器名:
        ports:
          - "宿主机端口号:容器端口号"
    ```
    
* `expose`

    暴露容器端口，但不会映射到宿主机，只能被连接的服务使用。
    
    ```yaml
    services:
      容器名:
        expose:
          - 端口号
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
          - 变量名=值
          变量名:值
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

    指定连接的容器，并标记连接容器的ip第知道该容器中。
    
    ```yaml
    services:
      容器名:
        links:
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