### 前期准备工作

##### 安装相关文件

```shell script
sudo pip install virtualenv virtualenvwrapper
```

##### 创建存放虚拟环境的目录

```shell script
mkdir -p ~/.virtualenvs/
```

##### 修改系统变量

```shell script
vim ~/.bash_profile +
```

中写入

```shell script
export VIRTUALENVWRAPPER_PYTHON=python路径
export VIRTUALENVWRAPPER_VIRTUALENV=virtualenv路径
export WORKON_HOME=~/.virtualenvs/

source virtualenvwrapper.sh路径
```

##### 激活系统变量

```shell script
source ~/.bash_profile
````

### 虚拟环境操作

##### 创建

```shell script
mkvirtualenv 虚拟环境名
```

##### 查看

```shell script
workon
```

##### 切换

```shell script
workon 虚拟环境名
```

##### 退出

```shell script
deactivate
```

##### 删除

```shell script
rmvirtualenv 虚拟环境名
```

### 其他操作

##### `pip`命令

* 查看当前系统已安装的所有依赖项

    ```shell script
    pip list
    ```

* 查看当前用户已安装的所有依赖项

    ```shell script
    pip freeze
    ```

##### 虚拟环境的迁入与迁出

* 迁出

    ```shell script
    pip freeze > ./requirements.txt
    ```

* 迁入

    ```shell script
    pip install -r ./requirements.txt
    ```

### 使用Python操作虚拟环境

##### 创建

```shell script
python -m venv .虚拟环境名
```

##### 激活

```shell script
source .虚拟环境名的相对路径或绝对路径/bin/activate
```

##### 退出

```shell script
deactivate
```