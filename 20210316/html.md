### 简介

##### 网站简介

网站是由域名、空间和Web应用组成，对网站的建设与开发实际上是对Web应用进行开发，包括Web前端和Web后端。

##### HTML简介

HTML是Hyper Text Markup Language的简称。

### 基本结构

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8"/>
        <title>标题</title>
    </head>
    <body></body>
</html>
```

### 基本语法

##### 标签的分类

* 常规标签

    ```html
    <标签名 属性名="属性值" ...></标签名>
    ```

* 空标签

    ```html
    <标签名 属性名="属性值" .../>
    ```
  
> 注：
>
> 1. 属性间是不分先后顺序的；
>
> 2. 属性值必须添加英文状态下的双引号。

##### 常用标签

* 注释

    ```html
    <!--注释-->
    ```

* 文章标题

    ```html
    <h1>~<h5>文章标题</h5>~</h1>
    ```

* 段落

    ```html
    <p>段落内容</p>
    ```

* 换行

    ```html
    <br/>
    ```

* 水平线

    ```html
    <hr/>
    ```

* 范围

    ```html
    <span>范围内容</span>
    ```

* 按钮

    ```html
    <button>按钮内容</button>
    ```

* 强调

    * 斜体强调
    
        ```html
        <em>强调内容</em>
        ```
    
    * 加粗强调
    
        ```html
        <strong>强调内容</strong>
        ```

* 加粗

    ```html
    <b>加粗内容</b>
    ```

* 缩写

    ```html
    <abbr title="全称">缩写内容</abbr>
    ```

##### 特殊符号

```html
&nbsp;
&quot;
&gt;
&lt;
&copy;
```

### 图像和链接

##### 图像

```html
<img src="图像文件路径" alt="图像不显示时替代的文字" title="鼠标悬停到当前位置时显示的文字"/>
```

##### 链接

* 页面间的链接

    ```html
    <a href="链接" title="鼠标悬停到当前位置时显示的文字" target="_blank/_self">链接描述</a>
    ```

* 锚链接

    目标位置处设置锚点，即

    ```html
    <a name="锚点名"></a>
    ```
  
    链接位置处
    
    ```html
    <a href="[链接]#[锚点名]">链接描述</a>
    ```

* 功能性链接

    链接到电子邮箱、QQ或MSN等。

### 列表

##### 无序列表

```html
<ul>
    <li>列表项目</li>
</ul>
```

##### 有序列表

```html
<ol>
    <li>列表项目</li>
</ol>
```

##### 自定义列表

```html
<dl>
    <dt>列表项目</dt>
    <dd>列表项目下的内容</dd>
</dl>
```

### 表格

##### 为什么使用表格

简单通用，结构稳定。

##### 结构

```html
<table>
    <caption>表格标题</caption>
    <thead>
        <tr>
            <th>表格表头内容</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>表格单元格内容</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            ...
        </tr>
    </tfoot>
</table>
```

### 常用HTML属性

##### 跨行和跨列

`rowspan="行数"` `colspan="列数"`

##### 文本节点的水平对其方式

`align="left/center/right"`

### 全局HTML属性

##### 元素是否支持拖动

`traggable="true/false"`

### 下拉列表选项框

```html
<select name="名称" [multiple]>
    <option value="下拉列表选项框内容" [selected]>下拉列表选项框内容</option>
</select>
```

### 表单

##### 作用

主要用于收集用户信息。

##### 组成

表单是由表单域、表单控件和提示信息组成。

##### 表单域

```html
<form name="名称" action="链接" method="get/post" target="_blank/_self"></form>
```

##### 表单控件

* 文本框
    
    ```html
    <input type="text" name="名称" value="值" [placeholder="占位符"]/>
    ```

* 密码框

    ```html
    <input type="password" name="名称" value="值" [placeholder="占位符"/>
    ```

* 单选框

    ```html
    <input type="radio" name="名称" value="单选内容" [checked]/>
    ```
  
    > 注：
    >
    > 一组单选框的`name`属性值必须相同。

* 复选框

    ```html
    <input type="checkbox" name="名称" value="多选内容" [checked]/>
    ```

* 普通按钮

    ```html
    <input type="button" vlaue="按钮内容"/>
    ```

* 提交按钮

    ```html
    <input type="submit" value="那妞内容"/>
    ```

* 重置按钮

    ```html
    <input type="reset" value="单选内容"/>
    ```

* 图像按钮

    ```html
    <input type="image" src="图像文件路径" alt="图像不显示替代的文字"/>
    ```

* 文件域

    ```html
    <input type="file" name="名称" value="文件路径"/>
    ```

* 文本域

    ```html
    <textarea rows="行数" cols="字符宽度"></textarea>
    ```

* 隐藏域

    ```html
    <input type="hidden" name="名称" value="值"/>
    ```

##### 表单控件通用属性

##### 表单高级

* 设置表单控件提示信息

    ```html
    <label for="控件id属性值">提示信息</label>
    ```