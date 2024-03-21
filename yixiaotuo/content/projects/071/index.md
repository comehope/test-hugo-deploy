+++
title = '跳8字型舞的 loader'
date = 2018-07-06T17:12:38+08:00
image = '/test-hugo-deploy/img/thumbs/071.png'
summary = '#71'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/gKNMMm](https://codepen.io/comehope/pen/gKNMMm)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cd339Ur](https://scrimba.com/p/pEgDAM/cd339Ur)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含 5 个元素：
```html
<div class="loader">
    <span></span>
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
    background-color: goldenrod;
}
```

定义容器尺寸：
```css
.loader {
    width: 8em;
    height: 8em;
    font-size: 30px;
}
```

画出圆点：
```css
.loader span {
    position: absolute;
    top: 4em;
    width: 1em;
    height: 1em;
    background-color: #222;
    border-radius: 50%;
}
```

定义动画效果：
```css
.loader span {
    transform-origin: 4em top;
    animation: dance 1s linear infinite;
}

@keyframes dance {
    to {
        transform: rotateX(360deg) rotateZ(360deg);
    }
}
```

最后，为各圆点增加动画延时：
```css
.loader span {
    animation-delay: calc((var(--n) - 5) * 0.1s);
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
```

大功告成！
