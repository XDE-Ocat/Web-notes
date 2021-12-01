## 消除浮动带来的影响

```css
.clearfix::after{
    content:'';
    visibility:hidden;
    height:0;
    display:block;
    clear:both;
}
```

## 相对定位
相对自己进行移动

## display:
- none
- inline
- block
- inline-block
- flex
- inline-flex

## flex
- dispaly:flex||inline-flex
- 属性
    - 弹性容器属性
        
    - 弹性子元素属性
        1. 弹性子元素在父容器中的位置:flex-direction: row | row-reverse | column | column-reverse
        2. justify-content: flex-start | flex-end | center | space-between | space-around
        3. align-items 设置或检索弹性盒子元素在侧轴（纵轴）方向上的对齐方式
        align-items: flex-start | flex-end | center | baseline | stretch
        4. flex-wrap 属性用于指定弹性盒子的子元素换行方式
        flex-wrap: nowrap|wrap|wrap-reverse|initial|inherit;
        5. align-content
        6. flex-flow
        7. order
        8. align-self

## 响应式
- 媒体查询
- @media 媒体类型 and （条件）

## 移动端开发
- rem
- em
- %
- 移动端网页开发技术方案
    - 通过flexible动态设置html的fontsize值
    - 通过px to rem插件来将px转换为rem
    - 需要注意，我们练习的时候模仿的网页宽度都是375
    - normalize.css
    - iphone 6 7 8

