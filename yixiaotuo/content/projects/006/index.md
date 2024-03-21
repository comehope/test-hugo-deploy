+++
title = '蓝色璀璨钻石'
date = 2018-04-28T12:40:38+08:00
image = '/fe/img/thumbs/006.png'
summary = '#6'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/zhang-ou/pen/qYqwQp](https://codepen.io/zhang-ou/pen/qYqwQp)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/c/cp24VfV](https://scrimba.com/c/cp24VfV)

## 源代码下载

请从 github 下载。

[https://github.com/comehope/front-end-daily-challenges/tree/master/006-blue-dazzling-diamond](https://github.com/comehope/front-end-daily-challenges/tree/master/006-blue-dazzling-diamond)

## 代码解读

定义 dom，容器中包含一个元素：
```html
<div class="diamond">
	<span></span>
</div>
```

居中显示：
```css
html,
body {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}
```

画出第一组刻面的形状：
```css
.diamond {
    display: grid;
}

.diamond span {
    border-width: 50px;
    border-style: solid;
}
```

为第一组刻面上色，因为后面还要用到这些色值，所以定义了变量：
```css
:root {
    --color1: deepskyblue;
    --color2: steelblue;
    --color3: royalblue;
    --color4: dodgerblue;
}

.diamond span {
    border-color: var(--color1) var(--color2) var(--color3) var(--color4);
}
```

dom容器 中再增加3组刻面：
```html
<div class="diamond">
	<span></span>
	<span></span>
	<span></span>
	<span></span>
</div>
```

把4组刻面先组成田字格，再转换成钻石形状：
```css
.diamond {
    grid-template-columns: 1fr 1fr;
    transform: rotate(45deg);
}

.diamond span:first-child {
    border-color: transparent var(--color2) var(--color3) transparent;
}
```

定义动画效果：
```css
@keyframes animate {
    0% {
        border-color: var(--color1) var(--color2) var(--color3) var(--color4);
    }
    
    25% {
        border-color: var(--color4) var(--color1) var(--color2) var(--color3);
    }
    
    50% {
        border-color: var(--color3) var(--color4) var(--color1) var(--color2);
    }
    
    75% {
        border-color: var(--color2) var(--color3) var(--color4) var(--color1);
    }
    
    100% {
        border-color: var(--color1) var(--color2) var(--color3) var(--color4);
    }
}
```

最后，把动画效果应用到除第1组以外的刻面上：
```css
.diamond span:not(:first-child) {
    animation: animate 2s linear infinite;
}
```

大功告成！
