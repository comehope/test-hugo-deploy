+++
title = '条纹彩虹心'
date = 2018-06-01T15:47:45+08:00
image = '/test-hugo-deploy/img/thumbs/039.png'
summary = '#39'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/QxbmxJ](https://codepen.io/comehope/pen/QxbmxJ)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cepNzTW](https://scrimba.com/p/pEgDAM/cepNzTW)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含 9 个 <span>：
```html
<div class="heart">
	<span></span>
	<span></span>
	<span></span>
	<span></span>
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
	background: radial-gradient(circle at center, navy, black);
}
```

定义容器尺寸：
```css
.heart {
	width: 14em;
	height: 11em;
}
```

布局容器中的竖条纹：
```css
.heart {
	display: flex;
	justify-content: space-between;
}

.heart span {
	width: 1em;
	background-color: lightblue;
	border-radius: 0.5em;
}
```

为竖条纹配色，条纹的样式是左右对称的：
```css
.heart span {
	background-color: var(--c);
}

.heart span:nth-child(1),
.heart span:nth-child(9) {
	--c: orangered;
}

.heart span:nth-child(2),
.heart span:nth-child(8) {
	--c: gold;
}

.heart span:nth-child(3),
.heart span:nth-child(7) {
	--c: limegreen;
}

.heart span:nth-child(4),
.heart span:nth-child(6) {
	--c: dodgerblue;
}

.heart span:nth-child(5) {
	--c: mediumpurple;
}
```

为竖条纹设置高度，组成心形图案：
```css
.heart span {
	height: var(--h);
	position: relative;
	top: var(--t);
}

.heart span:nth-child(1),
.heart span:nth-child(9) {
	--h: 3em;
	--t: 2.2em;
}

.heart span:nth-child(2),
.heart span:nth-child(8) {
	--h: 6em;
	--t: 0.6em;
}

.heart span:nth-child(3),
.heart span:nth-child(7) {
	--h: 8em;
	--t: 0;
}

.heart span:nth-child(4),
.heart span:nth-child(6) {
	--h: 9em;
	--t: 0.8em;
}

.heart span:nth-child(5) {
	--h: 9.4em;
	--t: 1.6em;
}
```

设置位移动画效果：
```css
.heart span {
	animation: beating 5s infinite;
}

@keyframes beating{
	0%, 30% {
		top: var(--t);
		height: var(--h);
	}

	60%, 70% {
		top: 25%;
		height: 50%;
	}
}
```

最后，为动画过程中的条纹设置去色、模糊和变窄效果，加强与彩色条纹的差异对比：
```css
@keyframes beating{
	0%, 30% {
		background-color: var(--c);
		filter: blur(0);
		width: 1em;
	}

	60%, 70% {
		background-color: lightblue;
		filter: blur(5px);
		width: 0.1em;
	}
}
```

大功告成！

