+++
title = '锡纸撕纸效果'
date = 2018-08-28T17:44:19+08:00
image = '/fe/img/thumbs/120.png'
summary = '#120'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/WgxbaZ](https://codepen.io/comehope/pen/WgxbaZ)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/c86pbcE](https://scrimba.com/p/pEgDAM/c86pbcE)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含若干子元素，每个子元素中包含一个字母：
```html
<div class="text">
    <span>A</span>
    <span>W</span>
    <span>E</span>
    <span>S</span>
    <span>O</span>
    <span>M</span>
    <span>E</span>
</div> 
```

定义容器尺寸：
```css
body {
  margin: 0;
  height: 100vh;
}

.text {
  width: 100%;
  height: 100%;
}
```

设置子元素的布局方式：
```css
.text {
  display: flex;
  justify-content: space-between;
}

.text span {
    width: 100%;
}
```

定义文本样式：
```css
.text span {
    color: darkslategray;
    background-color: rgb(127, 140, 141);
    font-family: serif;
    font-size: 12vmin;
    text-shadow: 1px 1px 1px white;
    display: flex;
    align-items: center;
    justify-content: center;
}
```

设置文本的背景的渐变色，奇数位的文字和偶数位的文字的渐变方向是相反的：
```css
.text span:nth-child(odd) {
    background: linear-gradient(
        to bottom,
        rgba(127, 140, 141, 0.2) 0%, 
        rgba(127, 140, 141, 0) 33%, 
        rgba(127, 140, 141, 0.7) 66%, 
        rgba(127, 140, 141, 0.2) 100%
    );
}

.text span:nth-child(even) {
    background: linear-gradient(
        to top,
        rgba(127, 140, 141, 0.2) 0%, 
        rgba(127, 140, 141, 0) 33%, 
        rgba(127, 140, 141, 0.7) 66%, 
        rgba(127, 140, 141, 0.2) 100%
    );
}
```

增加文字之间的分隔线，第1个文字之前不用加分隔线：
```css
.text span {
    position: relative;
}

.text span:not(:first-child)::before {
    content: '';
    position: absolute;
    width: 10px;
    height: 90%;
    background-color: black;
    left: -5px;
    border-left: 1px solid white;
    border-radius: 50%;
}
```

让分隔线上下错位：
```css
.text span:not(:first-child):nth-child(odd)::before {
    top: 2%;
}

.text span:not(:first-child):nth-child(even)::before {
    bottom: 2%;
}
```

大功告成！
