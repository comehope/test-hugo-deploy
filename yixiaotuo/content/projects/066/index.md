+++
title = '咖啡机'
date = 2018-07-01T17:10:59+08:00
image = '/fe/img/thumbs/066.png'
summary = '#66'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/rKPLMW](https://codepen.io/comehope/pen/rKPLMW)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/c6NzPfK](https://scrimba.com/p/pEgDAM/c6NzPfK)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含机体、出水口、咖啡杯、按钮和咖啡：
```html
<div class="coffee-machine">
    <span class="body"></span>
    <span class="spout"></span>
    <span class="cup"></span>
    <span class="button"></span>
    <span class="coffee"></span>
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
    background: linear-gradient(to right bottom, sandybrown, darkred);
}
```

定义容器尺寸：
```css
.coffee-machine {
    width: 15em;
    height: 15em;
    background-color: white;
    font-size: 20px;
    border-radius: 50%;
    border: 2em solid white;
}
```

画出机体的外框：
```css
.coffee-machine {
    position: relative;
    display: flex;
    justify-content: center;
}

.body {
    position: absolute;
    width: 8em;
    height: 12em;
    background-color: sandybrown;
    border-radius: 1.2em;
    top: 1.5em;
    border-right: 0.6em solid peru;
}
```

用伪元素画出机体的中间部分：
```css
.body::after {
    content: '';
    position: absolute;
    width: 8em;
    height: 8em;
    background-color: darkslategray;
    top: 2em;
    border-right: 0.6em solid black;
}
```

画出出水口：
```css
.spout {
    position: absolute;
    width: 3em;
    height: 1em;
    background-color: white;
    top: 3.5em;
    border-radius: 0.5em;
    border-right: 0.5em solid silver;
}
```

画出咖啡杯的杯体：
```css
.cup {
    position: absolute;
    width: 3em;
    height: 2em;
    background-color: white;
    bottom: 3.5em;
    border-radius: 0 0 1.4em 1.4em;
    border-right: 0.5em solid silver;
}
```

用伪元素画出咖啡杯的把手：
```css
.cup::after {
    content: '';
    position: absolute;
    width: 0.6em;
    height: 0.6em;
    border: 0.3em solid silver;
    border-radius: 50%;
    right: -1.2em;
    top: 0.2em;
}
```

画出按钮：
```css
.button {
    position: absolute;
    width: 1.2em;
    height: 1.2em;
    background-color: tomato;
    border-radius: 50%;
    bottom: 2em;
    right: 4.5em;
}
```

画出咖啡：
```css
.coffee::before,
.coffee::after {
    content: '';
    position: absolute;
    width: 0.7em;
    height: 5em;
    background-color: chocolate;
    top: 4.5em;
    left: calc((15em - 0.7em) / 2);
}
```

接下来润色一下。

为咖啡机增加光影：
```css
.coffee-machine {
    z-index: 1;
}

.coffee-machine::before,
.coffee-machine::after {
    content: '';
    position: absolute;
    width: 2em;
    height: 2em;
    border: 0.3em solid transparent;
    z-index: 2;
    border-radius: 50%;
    border-left-color: white;
    left: 3.8em;
}

.coffee-machine::before {
    top: 1.8em;
    transform: rotate(40deg);
}

.coffee-machine::after {
    bottom: 1.8em;
    transform: rotate(-40deg);
}
```

定义咖啡流动的前半段动画，即咖啡从出水口流到杯中：
```css
.coffee::before {
    animation: 2s linear infinite;
    animation-name: pouring-before;
    transform-origin: top;
}

@keyframes pouring-before {
    0%, 20% {
        transform: scaleY(0);
    }

    30%, 100% {
        transform: scaleY(1);
    }

    70%, 100% {
        visibility: hidden;
    }
}
```

定义咖啡流动的后半段动画，即出水口停止流出咖啡，剩余咖啡流到杯中：
```css
.coffee::after {
    animation: 2s linear infinite;
    animation-name: pouring-after;
    transform-origin: bottom;
}

@keyframes pouring-after {
    0%, 70% {
        visibility: hidden;
        transform: scaleY(1);
    }

    80%, 100% {
        transform: scaleY(0);
    }
}
```

大功告成！
