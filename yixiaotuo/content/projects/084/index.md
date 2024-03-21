+++
title = '极品飞车 loader'
date = 2018-07-20T17:16:17+08:00
image = '/fe/img/thumbs/084.png'
summary = '#84'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/MBbEMo](https://codepen.io/comehope/pen/MBbEMo)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cWLg8hV](https://scrimba.com/p/pEgDAM/cWLg8hV)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含 7 个元素：
```css
<div class="loader">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
</div>
```

居中显示：
```css
body{
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(midnightblue, black);
}
```

画出 7 个方块：
```css
.loader {
    width: calc(1em * 7 + 0.15em * 6);
    height: 1.5em;
    font-size: 20px;
    display: flex;
    justify-content: space-between;
}

.loader span {
    width: 1em;
    background-color: deepskyblue;
    border-radius: 0.1em;
}
```

让方块倾斜：
```css
.loader span {
    transform: skewX(-25deg);
}
```

定义闪烁的动画效果：
```css
.loader span {
    animation: animate 0.8s infinite alternate;
    filter: opacity(0);
}

@keyframes animate {
    to {
        filter: opacity(1);
    }
}
```

定义变量，设置动画延时，使效果看起来像是有一个暗色块从左到右移动：
```css
.loader span {
    animation-delay: calc((var(--n) - 1) * 0.2s);
}

.loader span:nth-child(1) {
    --n: 1;
}

.loader span:nth-child(2) {
    --n: 2;
}

.loader span:nth-child(3) {
    --n: 3;
}

.loader span:nth-child(4) {
	--n: 4;
}

.loader span:nth-child(5) {
	--n: 5;
}

.loader span:nth-child(6) {
	--n: 6;
}

.loader span:nth-child(7) {
	--n: 7;
}
```

最后，增加色块的缩放效果：
```css
.loader span {
    transform: skewX(-25deg) scale(0.1);
}

@keyframes animate {
    to {
        filter: opacity(1);
        transform: skewX(-25deg) scale(1);
    }
}
```

大功告成！
