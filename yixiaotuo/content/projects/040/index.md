+++
title = '记事本动画'
date = 2018-06-02T15:48:01+08:00
image = '/fe/img/thumbs/040.png'
summary = '#40'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/qKOPGw](https://codepen.io/comehope/pen/qKOPGw)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/c6GV2Ay](https://scrimba.com/p/pEgDAM/c6GV2Ay)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，一个 book 容器中包含一个 page 容器，page 中再包含 5 个 <span>，page 用于绘制书页，<span> 用于绘制笔划：
```html
	<div class="book">
		<div class="page">
			<span></span>
			<span></span>
			<span></span>
			<span></span>
			<span></span>
		</div>
	</div>
```

重定义盒模型：
```css
* {
	box-sizing: border-box;
}
```

定义书的尺寸：
```css
.book {
	--sw: 0.3em; /* stroke width */
	width: 15em;
	height: 10em;
	background-color: white;
	border: var(--sw) solid cadetblue;
	border-radius: var(--sw);
	font-size: 20px;
}
```

定义书页的尺寸：
```css
.book {
	position: relative;
}

.book .page {
	height: inherit;
	width: calc(50% + var(--sw) + var(--sw) / 2);
	background-color: inherit;
	border: inherit;
	border-radius: inherit;
	position: absolute;
	top: calc(-1 * var(--sw));
	right: calc(-1 * var(--sw));
}
```

绘制书页上的笔划：
```css
.book .page {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	padding: 8% 5%;
}

.book .page span {
	display: block;
	width: 100%;
	border-top: var(--sw) solid cadetblue;
	border-radius: inherit;
}
```

定义笔划动画效果，依次画出 5 个笔划：
```css
.book .page span {
	animation: 4s linear infinite;
	transform-origin: left;
	transform: scaleX(0);
}

.book .page span:nth-child(1) {
	animation-name: stroke-1;
}

.book .page span:nth-child(2) {
	animation-name: stroke-2;
}

.book .page span:nth-child(3) {
	animation-name: stroke-3;
}

.book .page span:nth-child(4) {
	animation-name: stroke-4;
}

.book .page span:nth-child(5) {
	animation-name: stroke-5;
}

@keyframes stroke-1 {
	0% {
		transform: scaleX(0);
	}

	10%, 100% {
		transform: scaleX(1);
	}
}

@keyframes stroke-2 {
	10% {
		transform: scaleX(0);
	}

	20%, 100% {
		transform: scaleX(1);
	}
}

@keyframes stroke-3 {
	20% {
		transform: scaleX(0);
	}

	30%, 100% {
		transform: scaleX(1);
	}
}

@keyframes stroke-4 {
	30% {
		transform: scaleX(0);
	}

	40%, 100% {
		transform: scaleX(1);
	}
}

@keyframes stroke-5 {
	40% {
		transform: scaleX(0);
	}

	50%, 100% {
		transform: scaleX(1);
	}
}
```

最后，定义书页翻动的效果：
```css
.book .page {
	animation: flip 4s linear infinite;
	transform-origin: left;
	transform-style: preserve-3d;
}

@keyframes flip {
	55% {
		transform: rotateY(0) translateX(0) skewY(0);
	}

	70% {
		transform: rotateY(-90deg) translateX(calc(-1 * var(--sw) / 2)) skewY(-20deg);
	}

	80%, 100% {
		transform: rotateY(-180deg) translateX(calc(-1 * var(--sw))) skewY(0);
	}
}

.book .page span {
	backface-visibility: hidden;
}
```

大功告成！
