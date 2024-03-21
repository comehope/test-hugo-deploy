+++
title = '背景色块变换按钮特效'
date = 2018-06-06T15:51:18+08:00
image = '/test-hugo-deploy/img/thumbs/044.png'
summary = '#44'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/XYKdwg](https://codepen.io/comehope/pen/XYKdwg)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cM7RLUG](https://scrimba.com/p/pEgDAM/cM7RLUG)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，标准导航结构下，<li> 中的每个字母用 <span> 包裹：
```html
<nav>
	<ul>
		<li>
			<span>p</span>
			<span>r</span>
			<span>o</span>
			<span>d</span>
			<span>u</span>
			<span>c</span>
			<span>t</span>
			<span>s</span>
		</li>
	</ul>
</nav>
```

居中显示：
```css
body {
	margin: 0;
	height: 100vh;
	display: flex;
	align-items: center;
	justify-content: center;
	background: linear-gradient(to right bottom, dimgray, black);
}
```

定义文字样式：
```css
ul {
	padding: 0;
}

li {
	list-style-type: none;
}

li span {
	color: white;
	font-size: 50px;
	font-family: monospace;
	text-transform: uppercase;
	letter-spacing: 0.1em;
}
```

当鼠标悬停时，用伪元素绘制倾斜的背景色块：
```css
li span {
	position: relative;
	transition: 500ms;
}

li:hover span {
	color: #333;
}

li span::before {
	content: '';
	position: absolute;
	height: 100%;
	width: 0;
	z-index: -1;
	transition: 500ms;
}

li:hover span::before {
	width: 70%;
	transform: rotate(-25deg);
	background: white;
}
```

设置缓动延时，增加动画效果：
```css
li:hover span {
	transition-delay: calc(80ms * var(--n) + 10ms);
}

li:hover span::before {
	transition-delay: calc(80ms * var(--n));
}

li span:nth-child(1) {
	--n: 1;
}

li span:nth-child(2) {
	--n: 2;
}

li span:nth-child(3) {
	--n: 3;
}

li span:nth-child(4) {
	--n: 4;
}

li span:nth-child(5) {
	--n: 5;
}

li span:nth-child(6) {
	--n: 6;
}

li span:nth-child(7) {
	--n: 7;
}

li span:nth-child(8) {
	--n: 8;
}
```

在单词左侧增加一条鼠标悬停时变亮的竖线：
```css
li {
	padding-left: 2em;
	border: 2px solid transparent;
	border-left-color: silver;
	transition: 500ms;
}

li:hover {
	border-left-color: white;
}
```

dom 中增加几个按钮，形成一组按钮：
```css
<nav>
	<ul>
		<li>
			<span>h</span>
			<span>o</span>
			<span>m</span>
			<span>e</span>
		</li>
		<li>
			<span>p</span>
			<span>r</span>
			<span>o</span>
			<span>d</span>
			<span>u</span>
			<span>c</span>
			<span>t</span>
			<span>s</span>
		</li>
		<li>
			<span>s</span>
			<span>e</span>
			<span>v</span>
			<span>i</span>
			<span>c</span>
			<span>e</span>
			<span>s</span>
		</li>
		<li>
			<span>c</span>
			<span>o</span>
			<span>n</span>
			<span>t</span>
			<span>a</span>
			<span>c</span>
			<span>t</span>
		</li>
	</ul>
</nav>
```

最后，文字居中对齐，再调整一下按钮间距：
```css
li {
	text-align: center;
	margin: 1em 0;
}
```

大功告成！
