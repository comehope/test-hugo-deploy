+++
title = '昂首阔步的圆点'
date = 2018-08-03T17:37:57+08:00
image = '/test-hugo-deploy/img/thumbs/097.png'
summary = '#97'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/ejrMKe](https://codepen.io/comehope/pen/ejrMKe)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/caw7yTv](https://scrimba.com/p/pEgDAM/caw7yTv)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含 5 个元素，每个元素代表 1 个小球：
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
    background: radial-gradient(circle at center, sienna, maroon);
}
```

定义容器尺寸：
```css
.loader {
    width: 6em;
    height: 1em;
    font-size: 40px;
}
```

画出圆点：
```css
.loader {
    position: relative;
}

.loader span {
    position: absolute;
    width: 1em;
    height: 1em;
    background-color: white;
    border-radius: 50%;
    left: 5em;
}
```

定义小球从右到左移动以及从左侧返回到右侧的动画效果：
```css
.loader {
    --duration: 5s;
}

.loader span {
    animation: 
        walk linear infinite;
    animation-duration: var(--duration);
}

@keyframes walk {
    0%, 95%, 100% {
        left: 5em;
    }

    80%, 85% {
        left: 0;
    }
}
```

再增加小球在最左端向上跳起和在最右端向下落下的动画效果：
```css
.loader span {
    animation: 
        walk linear infinite,
        jump linear infinite;
}

@keyframes jump {
    80%, 100% {
        top: 0;
    }

    85%, 95% {
        top: -1em;
    }
}
```

再增加小球在从左侧返回到右侧时，因运动得快而稍被压扁的效果：
```css
.loader span {
    animation: 
        walk linear infinite,
        jump linear infinite,
        squash linear infinite;
}

@keyframes squash {
    80%, 100% {
        width: 1em;
        height: 1em;
    }

    90% {
        width: 2em;
        height: 0.8em;
    }
}
```

为 5 个小球分别定义变量：
```css
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

声明小球的数量：
```
.loader {
    --dots: 5;
}
```

设置动画延时：
```css
.loader span {
    animation-delay: calc(var(--n) * var(--duration) / var(--dots) * -1);
}
```

最后，把点的尺寸改小一些：
```css
.loader {
    font-size: 20px;
}
```

大功告成！
