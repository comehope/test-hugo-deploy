+++
title = '宇宙飞船'
date = 2018-08-02T17:37:44+08:00
image = '/test-hugo-deploy/img/thumbs/096.png'
summary = '#96'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/oMqNmv](https://codepen.io/comehope/pen/oMqNmv)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cm48rta](https://scrimba.com/p/pEgDAM/cm48rta)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，`spacecraft` 表示飞船，容器中包含 1 个表示尾冀的元素 `fins`：
```html
<div class="spacecraft">
    <div class="fins"></div>
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
    background: linear-gradient(black, midnightblue);
}
```

画出飞船的船舱：
```css
.spacecraft {
    width: 7em;
    height: 11em;
    font-size: 16px;
    background: 
        linear-gradient(whitesmoke, darkgray);
    border-radius: 50% / 70% 70% 5% 5%;
}
```

用伪元素画出飞船尾部的火焰：
```css
.spacecraft::before {
    content: '';
    position: absolute;
    width: 6em;
    height: 2em;
    background-color: #444;
    border-radius: 20%;
    top: 10em;
    left: 0.5em;
    z-index: -1;
}

.spacecraft::after {
    content: '';
    position: absolute;
    box-sizing: border-box;
    width: 4em;
    height: 4em;
    background: gold;
    top: 10em;
    left: 1.5em;
    border-radius: 80% 0 50% 45% / 50% 0 80% 45%;
    transform: rotate(135deg);
    border: 0.5em solid orange;
    z-index: -2;
}
```

画出飞船两侧的尾冀：
```css
.fins::before,
.fins::after {
    content: '';
    position: absolute;
    width: 2em;
    height: 6em;
    background: linear-gradient(tomato, darkred);
    top: 7em;
}

.fins::before {
    left: -2em;
    border-radius: 3em 0 50% 100%;
}

.fins::after {
    right: -2em;
    border-radius: 0 3em 100% 50%;
}
```

用径向渐变画出飞船的舷窗：
```css
.spacecraft {
    background: 
        radial-gradient(
            circle at 3.5em 5em,
            transparent 1.5em,
            lightslategray 1.5em, lightslategray 2em,
            transparent 2em
        ),
        radial-gradient(
            circle at 3.3em 5.2em,
            deepskyblue 1.4em,
            transparent 1.6em
        ),
        radial-gradient(
            circle at 3.5em 5em,
            white 1.5em,
            transparent 1.5em
        ),
        linear-gradient(whitesmoke, darkgray);
}
```

增加飞船火焰喷射的动画效果：
```css
.spacecraft::after {
    animation: flame-spout 0.3s infinite;
}

@keyframes flame-spout {
    0%, 100% {
        filter: opacity(0.1);
    }

    50% {
        filter: opacity(1);
    }
}
```

接下来画星空。
在 dom 中增加 `stars` 容器，其中包含表示星星的 4 个子元素：
```html
<div class="stars">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
</div>
<div class="rocket">
    <div class="fins"></div>
</div>
```

定义星星的样式：
```css
.stars span {
    position: absolute;
    width: 2px;
    height: 8px;
    border-radius: 50%;
    background-color: white;
    top: calc(50% - 7em);
}
```

用变量使星星分布在水平方向的不同位置：
```css
.stars span {
    left: calc(var(--left) * 1vw);
}

.stars span:nth-child(1) {
    --left: 20;
}

.stars span:nth-child(2) {
    --left: 40;
}

.stars span:nth-child(3) {
    --left: 60;
}

.stars span:nth-child(4) {
    --left: 80;
}

```

用变量设置星星的尺寸和不透明度，使每颗星星看起来稍有差异：
```css
.stars span {
    width: calc(var(--size) * 1px);
    height: calc(var(--size) * 4px);
    filter: opacity(var(--opacity));
}

.stars span:nth-child(1) {
    --size: 0.8;
    --opacity: 0.5;
}

.stars span:nth-child(2) {
    --size: 1.25;
    --opacity: 0.6;
}

.stars span:nth-child(3) {
    --size: 1.5;
    --opacity: 0.7;
}

.stars span:nth-child(4) {
    --size: 2;
    --opacity: 0.8;
}
```

定义星星从太空中飘过的动画效果：
```css
.stars span {
    top: -5vh;
    animation: star-move linear infinite;
}

@keyframes star-move {
    to {
        top: 100vh;
    }
}
```

用变量设置动画的时长和延时时间：
```css
.stars span {
    animation-duration: calc(var(--duration) * 1s);
    animation-delay: calc(var(--delay) * 1s);
}

.stars span:nth-child(1) {
    --duration: 1;
    --delay: -0.05;
}

.stars span:nth-child(2) {
    --duration: 1.5;
    --delay: -0.1;
}

.stars span:nth-child(3) {
    --duration: 2;
    --delay: -0.15;
}

.stars span:nth-child(4) {
    --duration: 2.5;
    --delay: -0.2;
}
```

隐藏屏幕外的内容：
```css
body {
    overflow: hidden;
}
```

接下来用 d3 批量处理表示星星的 dom 元素和 css 变量。
引入 d3 库：
```html
<script src="https://d3js.org/d3.v5.min.js"></script>
```

用 d3 创建表示星星的 dom 元素：
```javascript
const COUNT_OF_STARS = 4;

d3.select('.stars')
    .selectAll('span')
    .data(d3.range(COUNT_OF_STARS))
    .enter()
    .append('span');
```

用 d3 为 css 变量 `--left`, `--size`, `--opacity` 赋值，`--left` 的取值范围是 1 到 100，`--size` 的取值范围是 1 到 2.5，'--opacity' 的取值范围是 0.5 到 0.8：
```javascript
d3.select('.stars')
    .selectAll('span')
    .data(d3.range(COUNT_OF_STARS))
    .enter()
    .append('span')
    .style('--left', () => Math.ceil(Math.random() * 100))
    .style('--size', () => Math.random() * 1.5 + 1)
    .style('--opacity', () => Math.random() * 0.3 + 0.5);
```

用 d3 为 css 变量 `--duration` 和 `--delay` 赋值，`--duration` 的取值范围是 1 到 3，`--delay` 的取值是依次减少 0.05：
```javascript
d3.select('.stars')
    .selectAll('span')
    .data(d3.range(COUNT_OF_STARS))
    .enter()
    .append('span')
    .style('--left', () => Math.ceil(Math.random() * 100))
    .style('--size', () => Math.random() * 1.5 + 1)
    .style('--opacity', () => Math.random() * 0.3 + 0.5)
    .style('--duration', () => Math.random() * 2 + 1)
    .style('--delay', (d) => d * -0.05);
```

刪除掉 html 文件中相关的 dom 声明和 css 文件中的变量声明。

最后，把星星的数量增加到 30 颗：
```javascript
const COUNT_OF_STARS = 30;
```

大功告成！
