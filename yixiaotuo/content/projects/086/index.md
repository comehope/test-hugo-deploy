+++
title = '旋转的方块'
date = 2018-07-22T17:16:47+08:00
image = '/fe/img/thumbs/086.png'
summary = '#86'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/gjgyWm](https://codepen.io/comehope/pen/gjgyWm)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/czDMNsw](https://scrimba.com/p/pEgDAM/czDMNsw)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含 4 个元素：
```html
<div class="loader">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
</div>
```

居中显示：
```css
body {
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: black;
}
```

画出容器中心的方块：
```css
.loader{
    width: 10em;
    height: 10em;
    border: 0.25em solid white;
    font-size: 10px;
    border-radius: 1em;
}
```

画出容器四周的方块：
```css
.loader,
.loader span {
    position: absolute;
}

.loader span:nth-child(1) {
    top: 5em;
    left: 5em;
}

.loader span:nth-child(2) {
    top: -5em;
    left: 5em;
}

.loader span:nth-child(3) {
    top: 5em;
    left: -5em;
}

.loader span:nth-child(4) {
    top: -5em;
    left: -5em;
}
```

给方块上色：
```css
.loader,
.loader span {
    mix-blend-mode: screen;
}

.loader {
    background-color: gold;
}

.loader span:nth-child(1) {
    background-color: dodgerblue;
}

.loader span:nth-child(2) {
    background-color: hotpink;  
}

.loader span:nth-child(3) {
    background-color: mediumpurple;
}

.loader span:nth-child(4) {
    background-color: limegreen;
}
```

为容器整体增加旋转动画：
```css
.loader {
    animation: rotating 2s linear infinite;
}

@keyframes rotating {
    to {
        transform: rotate(1turn);
    }
}
```

为容器四周的方块增加反向旋转的动画效果：
```css
.loader span {
    animation: de-rotating 4s linear infinite;
}

@keyframes de-rotating {
    from, to {
        transform: rotate(0deg) scale(0.5);
    }

    50% {
        transform: rotate(-180deg) scale(1.2);
    }
}
```

最后，隐藏可能出现在页面外部的内容：
```css
body {
    overflow: hidden;
}
```

大功告成！
