+++
title = '一组办公用品'
date = 2018-07-12T17:14:05+08:00
image = '/test-hugo-deploy/img/thumbs/076.png'
summary = '#76'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/oMgmwB](https://codepen.io/comehope/pen/oMgmwB)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

上部：
[https://scrimba.com/p/pEgDAM/cEb3nhK](https://scrimba.com/p/pEgDAM/cEb3nhK)

下部：
[https://scrimba.com/p/pEgDAM/cqwzqAR](https://scrimba.com/p/pEgDAM/cqwzqAR)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器包含 5 个元素，分别代表纸张、尺子、记事本、日历和铅笔。
```html
<div class="desk">
    <span class="paper"></span>
    <span class="ruler"></span>  
    <span class="notebook"></span>
    <span class="calendar"></span>
    <span class="pencil"></span>
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
}
```

定义容器尺寸：
```css
.desk {
    width: 70em;
    height: 70em;
    font-size: 5px;
    position: relative;
}
```

定义各元素的共有属性：
```css
.desk {
    --b: 1em solid darkslategray;
}

.desk * {
    position: absolute;
    border: var(--b);
    box-sizing: border-box;
}

.desk *::before,
.desk *::after {
    content: '';
    position: absolute;
    box-sizing: border-box;
}
```

画出纸张的轮廓：
```css
.paper {
    width: 24em;
    height: 30em;
    color: skyblue;
    background-color: currentColor;
    border-radius: 0 0 0 3em;
    top: 14em;
    left: 4em;
}
```

画出纸张左侧卷曲的部分：
```css
.paper::before {
    width: 4em;
    height: 32em;
    background-color: currentColor;
    border: var(--b);
    filter: saturate(150%) brightness(0.9);
    bottom: 1.6em;
    left: -1em;
    border-radius: 3em 0 3em 0;
}

.paper::after {
    width: 4em;
    height: 5em;
    background-color: currentColor;
    border: var(--b);
    bottom: -1em;
    left: -1em;
    border-radius: 2.5em 0 0 2.5em;
    border-right: none;
}
```

画出尺子的轮廓：
```css
.ruler {
    width: 6em;
    height: 24em;
    background: linear-gradient(
        to right,
        peru 30%, 
        sandybrown 30%
    );
    top: 8em;
    left: 14em;
    transform: rotate(25deg);
}
```

画出尺子上的长刻度线：
```css
.ruler::before {
    width: 2em;
    height: calc(100% - 3em);
    background-image: linear-gradient(darkslategray 1em, transparent 0);
    background-size: 4em 4em;
    top: 1em;
}
```

画出尺子上的短刻度线：
```css
.ruler::after {
    width: 1em;
    height: calc(100% - 3em);
    background-image: linear-gradient(darkslategray 1em, transparent 0);
    background-size: 4em 4em;
    top: 3em;
}
```

画出日历的轮廓：
```css
.calendar {
    width: 28em;
    height: 28em;
    background: linear-gradient(coral 30%, white 30%);
    border-radius: 2em;
    top: 14em;
    right: 4em;
    transform: rotate(15deg);
}
```

画出日历顶部的转轴：
```css
.calendar::before {
    width: 3em;
    height: 4em;
    color: sandybrown;
    background-color: currentColor;
    top: -2em;
    left: 4em;
    border-radius: 100% 100% 50% 50%;
    box-shadow:
        0 0, 0 0 0 1em darkslategray,
        15em 0, 15em 0 0 1em darkslategray;
}
```

画出日历上的日期：
```css
.calendar::after {
    width: 3em;
    height: 3em;
    color: silver;
    background-color: silver;
    top: 10em;
    left: 4em;
    border-radius: 0.4em;
    box-shadow:
        0 0, 5em 0, 10em 0, 15em 0,
        0 5em, 5em 5em, 10em 5em, 15em 5em,
        0 10em, 5em 10em, 10em 10em, 15em 10em;
}
```

画出记事本的轮廓：
```css
.notebook {
    width: 26em;
    height: 34em;
    background: linear-gradient(
        to right,
        tomato 12%,
        coral 12%, coral 60%,
        darkslategray 60%, darkslategray 64%,
        sandybrown 64%, sandybrown 78%,
        darkslategray 78%, darkslategray 82%,
        coral 82%
    );
    border-radius: 3em;
    bottom: 8em;
    left: 20em;
}
```

画出记事本的底部：
```css
.notebook::before {
    width: inherit;
    height: 5em;
    background-color: white;
    border: var(--b);
    bottom: -1em;
    left: -1em;
    border-radius: 3em 0 3em 3em;
}
```

画出记事本的书签：
```css
.notebook::after {
    width: 4em;
    height: 5em;
    background-color: coral;
    border: var(--b);
    bottom: -3em;
    left: 4em;
    border-top: none;
    border-radius: 0 0 1em 1em;
}
```

画出铅笔的轮廓：
```css
.pencil {
    width: 6em;
    height: 12em;
    background: linear-gradient(
        coral 20%,
        darkslategray 20%, darkslategray 25%,
        sandybrown 25%
    );
    border-radius: 0.8em;
    bottom: 14em;
    right: 13em;
    transform: rotate(-35deg);
}
```

画出铅笔的笔尖：
```css
.pencil::before {
    border: 3em solid transparent;
    border-top-color: darkslategray;
    bottom: -6.5em;
    left: -1em;
}

.pencil::after {
    border: 2em solid transparent;
    border-top-color: sandybrown;
    bottom: -4.5em;
    left: 0;
}
```

增加鼠标悬停效果，把物品都推向桌面的边缘：
```css
.desk * {
    transition: 1s;
}

.desk:hover .paper {
    top: 0;
    left: 0;
}

.desk:hover .ruler {
    top: 0;
    left: 50%;
    transform: rotate(0);
}

.desk:hover .calendar {
    top: 0;
    right: 0;
    transform: rotate(0deg);
}

.desk:hover .notebook {
    bottom: 0;
    left: 0;
}

.desk:hover .pencil {
    bottom: 0;
    right: 0;
    transform: rotate(180deg);
}
```

dom 中增加文字 “Hey, Take it easy”：
```html
<div class="desk">
    <span class="paper"></span>
    <span class="ruler"></span>  
    <span class="calendar"></span>
    <span class="notebook"></span>
    <span class="pencil"></span>
    <p>Hey!<br>Take it easy!</p>
</div>
```

设置文字样式：
```css
.desk p {
    border: none;
    color: darkslategray;
    font-size: 6em;
    font-weight: bold;
    font-family: sans-serif;
    text-align: center;
    bottom: 2em;
    right: 1em;
}
```

最后，为文字增加慢慢浮现的效果：
```css
.desk p {
    transform: rotate(-35deg) scale(0);
}

.desk:hover p {
    transform: rotate(-35deg) scale(1);
}
```

大功告成！
