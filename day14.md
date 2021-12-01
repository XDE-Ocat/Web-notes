# day14

## 网站开发的类型

主要分成三种：

* 移动端
* PC
* 响应式



移动端网页和PC端网页分别开发是主流。

响应式网页主要是针对企业站。



## 媒体查询

识别设备的工具。

```css
@media 媒体类型 and (条件) {}
```

常用的媒体类型：

* all 
* print 打印机
* screen 屏幕
* speech 

条件:

* max-width min-width 
* max-height min-height
* orientation：portrait | landscape

示例代码:

```css
@media screen and (max-width: 768px) {}
```

## 根据屏幕宽度的变化来改变页面布局结构

所谓的响应式，主要包括两个开发逻辑：

* 随着屏幕宽度的变化，改变页面结构
* 随着屏幕宽度的变化，改变内容大小

例如:

```css
div {
    width: 1200px;
    font-size: 30px;
}

@media screen and (min-width: 768px) and (max-width: 1200px) {
    div {
        width: 960px;
        font-size: 28px;
    }
}

@media scrren and (max-width: 768px) {
    div {
        font-size: 24px;
        width: 100%;
        margin: 30px auto;
        padding-left: 10px;
        padding-right: 10px;
    }
}
```

## dpr的问题

目前主流的移动设备iphone6、7、8 的dpr是2，意味着实际的物理像素和逻辑像素之间的比例是1：2的关系。

如果UI提供的设计图是750px宽度，那么实际测量值在使用的时候应该/2。

如果UI提供的设计图是375px宽度，则量出多少写多少。



## 图片的问题

同样是因为dpr，所以在移动端使用图片的时候，一般采用2倍图。



## 视口

在pc端视口问题其实是不存在的。但是在移动端，存在三个视口，可视视口、布局视口、理想视口。

那么在移动端的时候，建议把视口设置为理想视口。

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

视口的完整的设置方式：

```html
<meta name="viewport" content="width=device-width,user-scalable=no,initial-scale=1,maximum-scale=1,minimum-scale=1">
```



## 新的单位

在css中，单位其实分成两种：

* 相对单位
* 绝对单位

例如，`px` 就是一个绝对单位。

```css
div {
    width: 100px;
}
```

相对单位主要是通过参照值来获得自己的值。

例如最熟悉的%。

除了%以外，还有两个比较常用的相对单位：

* em
* rem
* vh
* vw



em 和 rem都是相对单位。

em 参考值是父元素的font-size。如果过多的使用em为单位，可能导致在开发网页过程中，一旦出现嵌套层级过多的情况，就可能导致计算出现问题。



rem 相对来说，更加的简单和直观，主要是以html的font-size值为参考。

vw 相当于是视口宽度的简写，使用的逻辑是将网页宽度分成100分，那么1vw就表示其中的1/100。

例如：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .box {
      /* 1vw = 视口宽度的1/100  1vh = 视口高度的1/100 */
      width: 30vw;
      height: 20vw;
      background-color: pink;
    }
  </style>
</head>
<body>
  <div class="box"></div>
</body>
</html>
```





## 移动端网页解决方案之一 flexible 

首先将**flexible**的js文件通过`script`标签引入到网页中。

例如：

```html
<script src="js文件地址"></script>
```

然后设置理想视口：

```html
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no">
```



设置完成之后，可以将浏览器的模拟器调整到iphone6、7、8这个型号。可以在html代码中观察到此时html的font-size值是`37.5`。

![image-20211125132017787](images/image-20211125132017787.png)

此时如果设计图的宽度是375像素，那么在设计图当中测量出来的任何值都可以通过除以37.5得到一个rem值。



## vscode 安装px转rem的插件

在`vscode` 中，可以在扩展的选项里搜索下面的插件：

![image-20211125132213477](images/image-20211125132213477.png)

点击进去之后，选择安装。安装完成后需要配置html的font-size 。可以按照如下图操作。

![image-20211125132259984](images/image-20211125132259984.png)

![image-20211125132311168](images/image-20211125132311168.png)

然后将编辑器重启即可。



> 使用`px to rem`这个插件，有一个需要注意的地方：
>
> 一定要用编辑器打开项目的目录。



## 为什么要使用flexible这种类似的动态改变rem值的工具包

使用第三方工具包的目的，是为了减少开发的流程和难度。

只要将设计图和使用flexible开发的网页中的模拟器处于一个型号，就可以通过一套代码适配所有的移动端。



