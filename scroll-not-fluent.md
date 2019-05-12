# iOS 下滚动不流畅

背景：页面布局顶部有 navigationBar，底部有 foot，在滑动的时候，发现页面滚动显得非常卡顿，不流畅。

了解到的情况：在 iOS 11 以上的版本里，当快速滑动页面的时候，页面滚动期间，fixed 定位的头部会随着页面的滑动滑上去，等到上滑动作执行完毕时，头部才又出现,这个问题在安卓及iOS 11 以下的版本都是没有的。

## 解决方案

```html
<header><header>
<div class="wrapper"></div>
<footer></footer>
```

```css
header {
  width: 100%;
  height: 30px;
  position: fixed;
  top: 0;
  transform: translateZ(0);
  -webkit-transform: translateZ(0);
}
.wrapper {
  position: absolute;
  top: 30px;
  left: 0;
  right: 0;
  bottom: 30px;
  overflow-y: scroll;
  -webkit-overflow-scrolling: touch;
}
footer {
  width: 100%;
  height: 30px;
  position: fixed;
  bottom: 0;
  transform: translateZ(0);
  -webkit-transform: translateZ(0);
}
```