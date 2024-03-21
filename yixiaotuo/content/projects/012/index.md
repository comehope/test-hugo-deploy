+++
title = '断开的文字特效'
date = 2018-05-04T15:19:27+08:00
image = '/test-hugo-deploy/img/thumbs/012.png'
summary = '#12'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/zhang-ou/pen/LmjNgL](https://codepen.io/zhang-ou/pen/LmjNgL)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/c/c2EvWHN](https://scrimba.com/c/c2EvWHN)

## 源代码下载

请从 github 下载。

[https://github.com/comehope/front-end-daily-challenges/tree/master/012-broken-text-effects](https://github.com/comehope/front-end-daily-challenges/tree/master/012-broken-text-effects)

## 代码解读

定义 dom，只有一个元素，元素有一个 data-text 属性，属性值等于元素内的文本：
```html
<div class="text" data-text="BREAK">BREAK</div>
```

居中显示：
```css
html, body {
	height: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
}
```

设置渐变背景色：
```css
body {
	background: linear-gradient(brown, sandybrown);
}
```

设置文本的字体字号：
```css
.text {
	font-size: 5em;
	font-family: "arial black";
}
```

利用伪元素增加文字：
```css
.text {
	position: relative;
}

.text::before,
.text::after {
	content: attr(data-text);
	position: absolute;
	top: 0;
	left: 0;
	color: lightyellow;
}
```

设置左侧文字的遮罩：
```css
.text::before {
	background-color: darkgreen;
	clip-path: polygon(0 0, 60% 0, 30% 100%, 0 100%);
}
```

设置右侧文字的背景和遮罩：
```css
.text::after {
	background-color: darkblue;
	clip-path: polygon(60% 0, 100% 0, 100% 100%, 30% 100%);
}
```

当鼠标划过时，遮罩的文字分别向两侧偏移：
```css
.text::before,
.text::after {
	transition: 0.2s;
}

.text:hover::before {
	left: -0.15em;
}

.text:hover::after {
	left: 0.15em;
}
```

隐藏辅助元素，包括原始文字和伪元素的背景色：
```css
.text {
	color: transparent;
}

.text::before {
	/*background-color: darkgreen;*/
}

.text::after {
	/*background-color: darkblue;*/
}
```

两侧文字增加歪斜效果：
```css
.text:hover::before {
	transform: rotate(-5deg);
}

.text:hover::after {
	transform: rotate(5deg);
}
```

微调文字的高度：
```css
.text:hover::before {
	top: -0.05em;
}

.text:hover::after {
	top: 0.05em;
}
```

大功告成！
