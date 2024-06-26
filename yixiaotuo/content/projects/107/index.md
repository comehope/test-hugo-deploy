+++
title = '单眼怪兽'
date = 2018-08-16T17:40:57+08:00
image = '/test-hugo-deploy/img/thumbs/107.png'
summary = '#107'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/pZXzaY](https://codepen.io/comehope/pen/pZXzaY)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/c3qbkh8](https://scrimba.com/p/pEgDAM/c3qbkh8)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含的子元素分别表示耳朵、眼睛和嘴，嘴里还有牙齿：
```html
<div class="monster">
    <span class="ear left"></span>
    <span class="ear right"></span>  
    <span class="eye"></span>
    <span class="mouth">
        <span class="tooth"></span>
    </span>
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
    background: linear-gradient(lightcyan, lightblue);
}
```

画出怪兽的轮廓：
```css
.monster {
    width: 10em;
    height: 13em;
    font-size: 16px;
    color: blueviolet;
    background-color: currentColor;
    border-radius: 5em 5em 0 0 / 6em 6em 0 0;
}
```

画出眼睛的轮廓：
```css
.monster {
    position: relative;
}

.eye {
    position: absolute;
    width: 6.5em;
    height: 6.5em;
    background: white;
    border-radius: 77% 77% 77% 77% / 92% 92% 60% 60%;
    top: 2em;
    left: calc((10em - 6.5em) / 2);
    box-shadow: 0.2em 0.9em 0 rgba(0, 0, 0, 0.1);
}
```

用径向渐变画出眼珠和瞳孔：
```css
.eye {
    background: 
        radial-gradient(
            circle at 50% 25%,
            white 0.4em,
            transparent 0.4em
        ),
        radial-gradient(
            circle at 50% 40%,
            black 1.7em,
            transparent 1.7em
        ),
        white;
}
```

画出嘴的轮廓：
```css
.mouth {
    position: absolute;
    width: 3em;
    height: 2.1em;
    background-color: black;
    border-radius: 70% 70% 3.5em 3.5em;
    bottom: 0.9em;
    left: calc((10em - 3em) / 2);
}
```

用伪元素画出舌头：
```css
.mouth {
    overflow: hidden;
}

.mouth::before {
    content: '';
    position: absolute;
    width: inherit;
    height: 0.6em;
    background-color: tomato;
    border-radius: 50% 50% 0 0;
    bottom: 0;
}
```

画出三颗牙齿的中间那颗：
```css
.tooth {
    position: absolute;
    border-top: 0.8em solid white;
    border-left: 0.4em solid transparent;
    border-right: 0.4em solid transparent;
    left: 1.1em;
}
```

用伪元素画出三颗牙齿的左右两颗：
```css
.tooth::before,
.tooth::after {
    position: absolute;
    border-top: 0.8em solid white;
    border-left: 0.4em solid transparent;
    border-right: 0.4em solid transparent;
    left: 1.1em;
}

.tooth::before {
    content: '';
    left: -1.1em;
    top: -0.8em;
}

.tooth::after {
    content: '';
    left: 0.3em;
    top: -0.8em;
}
```

画出耳朵的形状：
```css
.ear {
    position: absolute;
    width: 2.4em;
    height: 4.5em;
    top: -3em;
}

.ear::before {
    content: '';
    position: absolute;
    width: 0.9em;
    height: inherit;
    background-color: currentColor;
    left: calc((2.4em - 0.9em) / 2);
}

.ear::after {
    content: '';
    position: absolute;
    width: 2.4em;
    height: 2.4em;
    top: -0.5em;
    background-color: currentColor;
    border-radius: 50%;
    box-shadow: inset -0.3em -0.2em 0 rgba(0, 0, 0, 0.1);
}
```

分别定位左耳和右耳：
```css
.ear {
    transform-origin: bottom center;
    transform: rotate(calc(10deg * var(--direction)));
}

.ear.left {
    left: 2em;
    --direction: -1;
}

.ear.right {
    right: 2em;
    --direction: 1;
}
```

接下来增加动画效果：
增加身体轻微弹动的效果：
```css
.monster {
    transform-origin: bottom center;
    animation: body-bounce 1s infinite;
}

@keyframes body-bounce {
    50% {
        transform: scaleX(1.03) scaleY(0.97);
    }
}
```

增加耳朵轻微颤动的效果：
```css
.ear {
    animation: ears-shake 5s infinite;
}

@keyframes ears-shake {
    50% {
        transform: rotate(calc(20deg * var(--direction)));
    }
}
```

增加眨眼效果：
```css
.eye {
    animation: eye-blink 5s infinite;
}

@keyframes eye-blink {
    0%, 6% {
        transform: scaleX(1) scaleY(1);
    }

    3% {
        transform: scaleX(1.03) scaleY(0.1);
    }
}
```

大功告成！
