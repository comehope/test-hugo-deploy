+++
title = '文本淡入动画效果'
date = 2018-09-21T17:50:01+08:00
image = '/test-hugo-deploy/img/thumbs/140.png'
summary = '#140'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/ZMwgqK](https://codepen.io/comehope/pen/ZMwgqK)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cJB3rAN](https://scrimba.com/p/pEgDAM/cJB3rAN)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含若干子元素，每个子元素是 1 个字母：
```html
<div class="container">
    <span>h</span>
    <span>a</span>
    <span>p</span>
    <span>p</span>
    <span>y</span>
    <span>&nbsp;</span>
    <span>h</span>
    <span>o</span>
    <span>l</span>
    <span>i</span>
    <span>d</span>
    <span>a</span>
    <span>y</span>
    <span>s</span>
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
	background: linear-gradient(pink, white, pink);
}
```

设置字体样式：
```css
.container span {
	display: inline-block;
	color: purple;
	font-weight: bold;
	text-transform: uppercase;
	font-size: 40px;
}
```

定义文字从左到右的移动效果：
```css
.container span {
    animation: sideSlide 4s forwards infinite;
    transform: translateX(-100vw);
}

@keyframes sideSlide {
	15%, 20% {
		transform: translateX(0.5em);
	}

	24% {
		transform: translateX(0);
	}

	25%, 75% {
		transform: translateX(0);
	}

	90%, 100% {
		transform: translateX(100vw);
	}
}
```

增加文字缩放的动画效果：
```css
.container span {
	transform: translateX(-100vw) scale(0);
}

@keyframes sideSlide {
	15%, 20% {
		transform: translateX(0.5em) scale(1);
	}

	24% {
		transform: translateX(0) scale(1.2);
	}

	25%, 75% {
		transform: translateX(0) scale(1);
	}

	90%, 100% {
		transform: translateX(100vw) scale(0);
	}
}
```

增加文字入场和出场时的淡入淡出效果：
```css
.container span {
	filter: opacity(0);
}

@keyframes sideSlide {
	15%, 20% {
		transform: translateX(0.5em) scale(1);
	}

	24% {
		transform: translateX(0) scale(1.2);
	}

	25%, 75% {
		transform: translateX(0) scale(1);
		filter: opacity(1);
	}

	90%, 100% {
		transform: translateX(100vw) scale(0);
		filter: opacity(0);
	}
}
```

增加文字变色的效果：
```css
@keyframes sideSlide {
	15%, 20% {
		transform: translateX(0.5em) scale(1);
		color: purple;
	}

	24% {
		transform: translateX(0) scale(1.2);
		color: cyan;
	}

	25%, 75% {
		transform: translateX(0) scale(1);
		filter: opacity(1);
		color: purple;
	}

	90%, 100% {
		transform: translateX(100vw) scale(0);
		filter: opacity(0);
	}
}
```

设置子元素的下标变量：
```css
.container span:nth-child(1) { --n: 1; }
.container span:nth-child(2) { --n: 2; }
.container span:nth-child(3) { --n: 3; }
.container span:nth-child(4) { --n: 4; }
.container span:nth-child(5) { --n: 5; }
.container span:nth-child(6) { --n: 6; }
.container span:nth-child(7) { --n: 7; }
.container span:nth-child(8) { --n: 8; }
.container span:nth-child(9) { --n: 9; }
.container span:nth-child(10) { --n: 10; }
.container span:nth-child(11) { --n: 11; }
.container span:nth-child(12) { --n: 12; }
.container span:nth-child(13) { --n: 13; }
.container span:nth-child(14) { --n: 14; }
```

设置子元素的动画延时：
```css
.container span {
	animation-delay: calc((var(--n) - 1) * 0.05s);
}
```

大功告成！
