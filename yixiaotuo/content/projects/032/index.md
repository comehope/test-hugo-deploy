+++
title = '六边形按钮'
date = 2018-05-25T15:45:30+08:00
image = '/test-hugo-deploy/img/thumbs/032.png'
summary = '#32'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/xjoOeM](https://codepen.io/comehope/pen/xjoOeM)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/c/cQ74NAJ](https://scrimba.com/c/cQ74NAJ)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义dom，容器中只包含 1 个按钮：
```html
<nav>
	<ul>
		<li>Home</li>
	</ul>
</nav>
```

定义按钮样式：
```css
nav {
	--h: 3em;
}

nav ul {
	padding: 0;
}

nav ul li {
	list-style-type: none;
	width: calc(var(--h) * 1.732);
	height: var(--h);
	background-color: #333;
	color: white;
	font-family: sans-serif;
	text-align: center;
	line-height: var(--h);
}
```

用伪元素增加2个倾斜的矩形：
```css
nav ul li {
	position: relative;
}

nav ul li::before,
nav ul li::after {
	content: '';
	position: absolute;
	top: 0;
	left: 0;
	width: inherit;
	height: inherit;
	background-color: #333;
}

nav ul li::before{
	transform: rotate(60deg) translateX(calc(var(--h) * -2));
}

nav ul li::after{
	transform: rotate(-60deg) translateX(calc(var(--h) * 2));
}
```

增加鼠标划过效果：
```css
nav ul li::before,
nav ul li::after {
	z-index: -1;
	filter: opacity(0);
	transition: 0.3s;
}

nav ul li:hover::before {
	filter: opacity(1);
	transform: rotate(60deg) translateX(0);
}

nav ul li:hover::after {
	filter: opacity(1);
	transform: rotate(-60deg) translateX(0);
}
```

dom 中增加几个按钮，形成一组按钮：
```html
<nav>
	<ul>
		<li>Home</li>
		<li>Products</li>
		<li>Services</li>
		<li>Contact</li>
	</ul>
</nav>
```

按钮之间为鼠标划过效果留出边距：
```css
nav ul li {
	margin: 2em;
}
```

最后，再增加两组按钮：
```html
<nav>
	<ul>
		<li>Home</li>
		<li>Products</li>
		<li>Services</li>
		<li>Contact</li>
	</ul>
</nav>
<nav>
	<ul>
		<li>Home</li>
		<li>Products</li>
		<li>Services</li>
		<li>Contact</li>
	</ul>
</nav>
<nav>
	<ul>
		<li>Home</li>
		<li>Product Vs</li>
		<li>Services</li>
		<li>Contact</li>
	</ul>
</nav>
```

尝试一些变化：
```css
nav {
	--h: 3em;
}

nav:nth-child(1) {
    --rate: 1.5;
    --bgcolor: black;
}

nav:nth-child(2) {
    --rate: 1.732;
    --bgcolor: brown;
}

nav:nth-child(3) {
    --rate: 2;
    --bgcolor: green;
}

nav ul li {
	width: calc(var(--h) * var(--rate));
	background-color: var(--bgcolor);
}

nav ul li::before,
nav ul li::after {
	background-color: var(--bgcolor);
}
```

大功告成！
