+++
title = '蝴蝶标本'
date = 2018-06-09T17:05:52+08:00
image = '/fe/img/thumbs/047.png'
summary = '#47'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/xzgZzQ](https://codepen.io/comehope/pen/xzgZzQ)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cN7EncL](https://scrimba.com/p/pEgDAM/cN7EncL)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器表示整只蝴蝶，因为蝴蝶是对称的，所以分为左右两边，每边有 3 个子元素：
```html
<div class="butterfly">
	<div class="left">
		<span></span>
	    <span></span>
	    <span></span>
	</div>
	<div class="right">
		<span></span>
	    <span></span>
	    <span></span>
	</div>
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
	background: linear-gradient(gray, lightyellow, gray);
}
```

定义蝴蝶的尺寸：
```css
.butterfly {
	position: relative;
	width: 10em;
	height: 10em;
}
```

先画左半边：
```css
.butterfly .left {
	position: absolute;
	width: inherit;
	height: inherit;
}
```

用第 1 个子元素画出翅膀的上半部分：
```css
.butterfly span {
	position: absolute;
	border-radius: 50%;
}

.butterfly span:nth-child(1) {
	width: 5em;
	height: 7em;
	background-color: gold;
}
```

用第 2 个子元素画出翅膀的下半部分：
```css
.butterfly span:nth-child(2) {
	width: 5.5em;
	height: 3.5em;
	background-color: orangered;
	top: 5em;
	left: -2.5em;
	filter: opacity(0.6);
}
```

用第 3 个子元素画出触角：
```css
.butterfly span:nth-child(3) {
	width: 6em;
	height: 6em;
	border-right: 0.3em solid orangered;
	top: -0.5em;
}
```

把左半边复制一份到右半边：
```css
.butterfly .right {
	position: absolute;
	width: inherit;
	height: inherit;
}

.butterfly .right {
	transform: rotateY(180deg) rotate(-90deg);
	top: 0.4em;
	left: 0.4em;
}
```

把标本装到展示框里：
```css
.butterfly::before {
	content: '';
	position: absolute;
	box-sizing: border-box;
	top: -2.5em;
	left: -8em;
	width: 24em;
	height: 18em;
	background-color: black;
  	border: 0.2em inset silver;
}

.butterfly::after {
    content: '';
    position: absolute;
    box-sizing: border-box;
    width: 40em;
    height: 30em;
    background-color: lightyellow;
    top: -9em;
    left: -16em;
    border: 2em solid burlywood;
    border-radius: 3em;
    box-shadow: 
    	0 0.3em 2em 0.4em rgba(0, 0, 0, 0.3),
    	inset 0.4em 0.4em 0.1em 0.5em rgba(0, 0, 0, .4);
    z-index: -1;
}
```

最后，调整一下因图案倾斜引起的位移：
```css
.butterfly {
	transform: translateX(1em);
}
```

大功告成！
