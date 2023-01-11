# eCharts在一些特殊的布局下重绘方案研究

项目基于Vue3 + Vite搭建。

## 说明

虽然这种场景很少，但是不可避免会在某些情况下发生。eCharts在Vue的mounted之后进行图表绘制，而此时的容器若被设定为flex: 1，则可能会受到其他元素的影响，比如此Demo下的图片加载完成后会影响到eCharts容器，造成页面显示效果的问题。

## 解决方案

当然最简单的办法就是在image加载完成的回调上面重新绘制图表，当然可以销毁的chart的方式让其重新自动适应宽度后再次绘制，达到效果。然而还有没有更好的办法呢。
