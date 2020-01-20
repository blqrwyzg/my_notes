# head标签

--head里的内容是给html添加额外的功能，称为元数据 。



### HTML头部

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```

-- head元素中的内容就是头部，为文档添加额外的功能。



#### 元数据：<meta>元素

```
<meta charset="utf-8">
```

--文档中被允许使用utf-8字符集utf-8是个通用的字符集，包含了人类语言的大部分字符。意味着web可以显示任何语言。英语 中文 日语 等 都可以背解析。

#### 

#### 添加作者和描述

```
<meta name="author" content="Chris Mills">
<meta name="description" content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications.">
```

--name指定了mets原色的类型，说明元素包含了什么类型的信息

--content制定了切实的元数据内容



#### description的使用

```
<meta name="description" content="The Mozilla Developer Network (MDN) provides
information about Open Web technologies including HTML, CSS, and APIs for both
Web sites and HTML5 Apps. It also documents Mozilla products, like Firefox OS.">
```

--会被搜索引擎抓取到并显示在搜索中。



### 增加自定义图标

--可以在元数据中添加自定义图标，这些图标可以在特定的场合显示

```
1、将图标保存在同级目录中
2、<link rel="shortcut icon" href="favicon.ico" type="image/x-icon"> 将代码写入元数据
```





### 在html中应用css和javascript

​	--css为当前页面添加样式

​	--经常位于文档头部， 有两个2属性，stylesheet表示这是文档的样式，href表示样式表的路径

```
<link rel="stylesheet" href="my-css-file.css">
```



​	--js为当前页面添加动态效果

​	--js通常放在文档末尾，确保加载脚本前浏览器已经解析了html中的内容

```
<script src="my-js-file.js"></script>
```





#### 为文档设置主语言

--	可以为文档设置语言，通过添加lang属性实现

```
<html lang="en-US">

```

