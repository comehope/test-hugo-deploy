+++
title = '冒着热气的咖啡杯'
date = 2018-05-05T15:21:41+08:00
image = '/test-hugo-deploy/img/thumbs/013.png'
summary = '#13'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/zhang-ou/pen/xjXxoz](https://codepen.io/zhang-ou/pen/xjXxoz)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/c/cBm4eU9](https://scrimba.com/c/cBm4eU9)

## 源代码下载

请从 github 下载。

[https://github.com/comehope/front-end-daily-challenges/tree/master/013-hot-coffee-cup](https://github.com/comehope/front-end-daily-challenges/tree/master/013-hot-coffee-cup)

## 代码解读

定义 dom，一个名为 coffee 的容器，其中包含一个名为 cup 的元素：
```html
<div class="coffee">
	<div class="cup"></div>
</div>
```

居中显示：
```css
html, body {
	height: 100%;
	align-items: center;
	justify-content: center;
	background-color: brown;
}
```

画出杯子主体：
```css
.coffee .cup {
	width: 10em;
	height: 9em;
	background-color: white;
	border-bottom-left-radius: 1.5em;
	border-bottom-right-radius: 1.5em;
}
```

用伪元素画出杯口：
```css
.coffee .cup {
	position: relative;
}

.coffee .cup::before {
	content: '';
	position: absolute;
	width: 100%;
	height: 2em;
	background-color: chocolate;
	border: 0.5em solid white;
	box-sizing: border-box;
	border-radius: 50%;
	top: -1em;
	box-shadow: inset 0 0 1em rgba(0, 0, 0, 0.5);
}
```

用伪元素画出杯子把手：
```css
.coffee .cup::after {
	content: '';
	position: absolute;
	width: 3em;
	height: 3.5em;
	border: 0.8em solid white;
	border-radius: 50%;
	top: 20%;
	left: 80%;
}
```

dom 元素增加托盘：
```html
<div class="coffee">
	<div class="cup"></div>
	<div class="plate"></div>
</div>
```

画出托盘：
```css
.coffee {
	display: flex;
	flex-direction: column;
	align-items: center;
	height: calc(9em + 1em);
	position: relative;
}

.coffee .plate {
	width: 16em;
	height: 1em;
	background-color: white;
	border-bottom-left-radius: 50%;
	border-bottom-right-radius: 50%;
	position: absolute;
	bottom: -1px;
}
```

dom 元素增加杯中冒出的热气：
```html
<div class="coffee">
	<div class="vapor">
		<span></span>
		<span></span>
		<span></span>
		<span></span>
		<span></span>
	</div>
	<div class="cup"></div>
	<div class="plate"></div>
</div>
```

画出杯中冒出的热气：
```css
.coffee {
	height: calc(9em + 1em + 2em);
}

.coffee .vapor {
	width: 7em;
	display: flex;
	justify-content: space-between;
}

.coffee .vapor span {
	width: 0.1em;
	min-width: 1px;
	height: 2em;
	background-color: white;
}
```

定义热气冒出的动画：
```css
.coffee .vapor span {
	animation: evaporation 2s linear infinite;
	filter: opacity(0);
}

@keyframes evaporation {
	from {
		transform: translateY(0);
		filter: opacity(1) blur(0.2em);
	}

	to {
		transform: translateY(-4em);
		filter: opacity(0) blur(0.4em);
	}
}
```

最后，调整每条热气的延迟时间，使动感更强：
```css
.coffee .vapor span:nth-child(1) {
	animation-delay: 0.5s;
}

.coffee .vapor span:nth-child(2) {
	animation-delay: 0.1s;
}

.coffee .vapor span:nth-child(3) {
	animation-delay: 0.3s;
}

.coffee .vapor span:nth-child(4) {
	animation-delay: 0.4s;
}

.coffee .vapor span:nth-child(5) {
	animation-delay: 0.2s;
}
```

大功告成！
