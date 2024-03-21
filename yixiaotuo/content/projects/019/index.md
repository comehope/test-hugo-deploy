+++
title = '文字被切开的菜单导航特效'
date = 2018-05-12T15:40:37+08:00
image = '/test-hugo-deploy/img/thumbs/019.png'
summary = '#19'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

https://codepen.io/comehope/pen/XqYroe

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

https://scrimba.com/p/pEgDAM/c7EbPuW

## 代码解读

定义 dom，一个列表中包含一个列表项，列表项有一个 data-text 属性：
```html
<ul class="menu">
	<li data-text="New Game">New Game</li>
</ul>
```

居中显示：
```css
html,
body {
	height: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: black;
}
```

设置文本样式：
```css
.menu {
    padding: 0;
}

.menu li {
	list-style-type: none;
	color: white;
	font-size: 3em;
	font-weight: bold;
	text-transform: uppercase;
	text-align: center;
	line-height: 1em;
	width: 7em;
}
```

画出文字的分割线：
```css
.menu li {
	border-top: 1px solid yellow;
}
```

隐藏文本：
```css
.menu li {
	color: transparent;
}
```

用伪元素增加文本：
```css
.menu li {
	position: relative;
}

.menu li::before {
	content: attr(data-text);
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	color: silver;
}
```

把伪元素文本向上移，竖跨分割线：
```css
.menu li::before,
.menu li::after {
	top: -0.5em;
}
```

用遮罩切出分割线上下二部分的文本：
```css
.menu li::before {
	clip-path: polygon(0 0, 100% 0, 100% 50%, 0 50%);
}

.menu li::after {
	clip-path: polygon(0 50%, 100% 50%, 100% 100%, 0 100%);
}
```

dom 中再增加几个菜单项：
```html
<ul class="menu">
	<li data-text="New Game">New Game</li>
	<li data-text="Load Game">Load Game</li>
	<li data-text="Options">Options</li>
	<li data-text="Exit">Exit</li>
</ul>

.menu li {
	margin: 0.5em;
}
```

为分割线增加动画效果：
```css
.menu li {
	border-top: 1px solid transparent;
	transition: 0.3s;
}

.menu li:hover {
	border-top: 1px solid yellow;
}
```

为文字增加动画效果：
```css
.menu li::before,
.menu li::after {
	transition: 0.3s ease-out;
}

.menu li:hover::before,
.menu li:hover::after {
	color: yellow;
	transition: left 0.3s ease-out;
	transition-delay: 0.2s;
}

.menu li:nth-child(odd):hover::before,
.menu li:nth-child(even):hover::after {
	left: -0.15em;
}

.menu li:nth-child(even):hover::before,
.menu li:nth-child(odd):hover::after {
	left: 0.15em;
}
```

大功告成！
