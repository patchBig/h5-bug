# :active 不生效

背景：在 H5 中做按钮加点击事件的时候，动态改变按下的样式，发现不生效

```css
a:active { color: lime } /* 激活链接 */
```

## 原因

 Safari Mobile 默认不使用:active 状态，除非元素上或`<body>` 上有一个 touchstart 事件处理器。

## 办法

```js
document.body.addEventListener('touchstart', function (){}); //...空函数即可
```

将上述事件监听代码加上后，Safari Mobile上就可以看到按钮按下后的切换效果了。