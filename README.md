TouchBox
========

> 移动端单页视图库，适用于制作移动专题

## DEMO

[http://jsbin.com/vatuma/latest](http://jsbin.com/vatuma/latest)

手机扫描下面二维码查看例子：

![demo qrcode](http://maxzhang.github.io/examples/images/touchbox-qrcode.png)

## 使用方法

首先，页面必须是下面的结构

```html
<html>
    // ...
</html>
<body>
    <div id="touchBoxCt">
        <div>
            // ...
        </div>
        <div>
            // ...
        </div>
        <div>
            // ...
        </div>
    </div>
</body>
```

初始CSS，除以下两个样式之外，TouchBox不需要其他任何样式

```css
/* 如果不将body的margin设为0，可能会导致视图高宽计算不准确 */
body, div {
    margin: 0;
    padding: 0;
}

/* 默认将子视图隐藏，防止首屏显示页面闪动，Touchbox会自动切到第一个视图 */
#touchBoxCt>div{
    display: none;
}
```

```javascript
new TouchBox('#touchBoxCt', {
    loop: true,
    animation: 'flow'
});
```

## 配置参数

### itemSelector : String

子视图选择器，默认''，如果设置，则使用选择器选中的子元素进行视图切换

### active : Number

首视图索引，默认0，默认为第一个子元素

### loop : Boolean

子视图切换是否可以循环切换，默认false

### animation : String

视图切换的动画效果，默认'flow'，取值范围：'slide'、'flow'

### duration : Number

视图切换动画时间，默认350，单位ms

### lockScreen : String

锁屏状态，默认'off'，取值：
 * 'off'        不锁屏
 * 'landscape'  锁定为横屏
 * 'portrait'   锁定为竖屏

### rotateBody : String/Function

锁屏提示，当lockScreen不为'off'时有效。

当值为String时，HTML字符串会被插入到页面并显示。

当值为Function时，函数的返回值会被被插入到页面并显示。

### beforeSlide : Function

子视图开始切换时回调函数，如果返回值为false，则终止当次切换操作。

回调函数参数：
 - toIndex     切换到视图索引
 - active      当前视图索引

### onSlide : Function

子视图切换结束时回调函数

回调函数参数：
 - active      当前视图索引
 
### onResize : Function

当TouchBox高宽被重置时调用。

回调函数参数：
 - width       高度
 - height      宽度
