# 滚动穿透

背景：页面滑出了一个弹窗，我们用手指触摸屏幕滑动时，会发现弹窗下面的内容还是在滚动。

## 方案1

在滚动位置丢失之前先保存下来，等到退出弹窗的前在將这个保存下来的滚动位置在设置回去。

```css
.modal-open {
  position: fixed;
  height: 100%;
}
```

```js
var ModalHelper = (function(bodyClass) {
    var scrollTop;
    return {
        afterOpen: function() {
            scrollTop = document.scrollingElement.scrollTop
                || document.documentElement.scrollTop
                || document.body.scrollTop;
            // 使 body 脱离文档流
            document.body.classList.add(bodyClass);
            document.body.style.top = -scrollTop + 'px';
        },
        beforeClose: function() {
            document.body.classList.remove(bodyClass);
            document.scrollingElement.scrollTop = document.documentElement.scrollTop = document.body.scrollTop = scrollTop;
        }
    };
})('modal-open');
```

参考：<https://uedsky.com/2016-06/mobile-modal-scroll/>