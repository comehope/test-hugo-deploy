+++
title = '弹跳的字母 i'
date = 2018-07-18T17:15:45+08:00
image = '/test-hugo-deploy/img/thumbs/082.png'
summary = '#82'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/pZbrpJ](https://codepen.io/comehope/pen/pZbrpJ)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cq9pZhN](https://scrimba.com/p/pEgDAM/cq9pZhN)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)


## 代码解读

定义 dom，只有一个元素：
```html
<div class="loader"></div>
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

定义容器尺寸：
```css
.loader {
    width: 8em;
    height: 10em;
    font-size: 10px;
}
```

画出字母 i 的形状：
```css
.loader {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.loader::before {
    content: '';
    width: 5em;
    height: 5em;
    background-color: orangered;
    border-radius: 50%;
}

.loader::after {
    content: '';
    width: 5em;
    height: 8em;
    background-color: orange;
    border-radius: 0.5em;
}
```

增加下部矩形的旋转效果：
```css
.loader::after {
    animation: rect-rotating 1s ease-in-out infinite;
}

@keyframes rect-rotating {
    50% {
        transform: rotate(90deg);
    }

    100% {
        transform: rotate(180deg);
    }
}
```

增加上部小球的跳动效果：
```css
.loader::before {
    animation: ball-jumping 1s ease-in-out infinite;
}

@keyframes ball-jumping {
    20%, 80% {
        transform: translateY(-2em);
    }

    50% {
        transform: translateY(calc((8em - 5em) / 2));
    }
}
```

大功告成！
