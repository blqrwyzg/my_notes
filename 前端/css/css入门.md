# css入门



### 为html文档添加css规则的三种方式



#### 一：同级目录创建css文件，并在html中的头部链接到css

```
<link rel="stylesheet" href="styles.css">
```

--link 用属性rel，让浏览器知道css文档存在，并利用属性href 指定，寻找css文件的位置。



#### 二、内部样式表

```
 <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }

      p {
        color: red;
      }
    </style>
```

--在html头部中设置style元素

#### 

#### 三、内联样式

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
  </head>
  <body>
    <h1 style="color: blue;background-color: yellow;border: 1px solid black;">Hello World!</h1>
    <p style="color:red;">This is my first CSS example</p>
  </body>
</html>
```

--直接在html元素中 设置 style属性，多个属性用 分号 ；隔开









# 样式化html元素



--可以一次性选择多个html元素

```
p, li {
    color: green;
}
```

--这样就选中两个元素公用一个选择器





# 改变元素的默认样式

--在没有css的情况下，html的样式是使用默认的。

--css可以更改html默认的元素样式

```
li {
  list-style-type: none;
}
```

--这个css就可以让html中的列表 舍去前面的标点







# 使用类名

--可以给html元素设置类名 ，然后在css中选择类名就可以选择html中所有相同类名的元素

```
<ul>
  <li>Item one</li>
  <li class="special">Item two</li>
  <li>Item <em>three</em></li>
</ul>
```

```
.special {
  color: orange;
  font-weight: bold;
}
```

--**ps**：需要在css中加个（.）类名字，就能选择

### 

### 类名选择器 与 元素选择器 同时使用

```
li.special {
  color: orange;
  font-weight: bold;
}
```

--选中每个special类中的li元素。



```
li.special,
span.special {
  color: orange;
  font-weight: bold;
}
```

--选中每个special类





### 根据元素在文档中的位置确定样式

```
li em {
  color: rebeccapurple;
}
```

--**后代选择器**：会选择li元素中的em元素<li>的后代。