+++
title = '彩虹条纹文字'
date = 2018-05-15T15:42:10+08:00
image = '/test-hugo-deploy/img/thumbs/022.png'
summary = '#22'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/ELpRxj](https://codepen.io/comehope/pen/ELpRxj)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/c/czrWDfZ](https://scrimba.com/c/czrWDfZ)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含文本，并且包含4个 <span> 用于特效，<span> 的 data-text 属性值为与文本相同：
```html
<p class="rainbow">
	web
	<span data-text="web"></span>
	<span data-text="web"></span>
	<span data-text="web"></span>
	<span data-text="web"></span>
</p>
```

居中显示：
```css
html, body {
	height: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	background: black;
}
```

定义文本样式：
```css
.rainbow {
	color: white;
	font-size: 300px;
	text-transform: uppercase;
	font-family: sans-serif;
	font-weight: bold;
	line-height: 1em;
	position: relative;
}
```

用伪元素增加图层，形成彩虹效果：
```css
.rainbow span::before,
.rainbow span::after {
	content: attr(data-text);
	position: absolute;
	top: 0;
	left: 0;
	overflow: hidden;
}

.rainbow span:nth-child(1)::before {
	color: orchid;
	z-index: 1;
	height: calc(100% - 10% * 1);
}

.rainbow span:nth-child(1)::after {
	color: mediumpurple;
	z-index: 2;
	height: calc(100% - 10% * 2);
}

.rainbow span:nth-child(2)::before {
	color: deepskyblue;
	z-index: 3;
	height: calc(100% - 10% * 3);
}

.rainbow span:nth-child(2)::after {
	color: cyan;
	z-index: 4;
	height: calc(100% - 10% * 4);
}

.rainbow span:nth-child(3)::before {
	color: mediumspringgreen;
	z-index: 5;
	height: calc(100% - 10% * 5);
}

.rainbow span:nth-child(3)::after {
	color: yellow;
	z-index: 6;
	height: calc(100% - 10% * 6);
}

.rainbow span:nth-child(4)::before {
	color: gold;
	z-index: 7;
	height: calc(100% - 10% * 7);
}

.rainbow span:nth-child(4)::after {
	color: tomato;
	z-index: 8;
	height: calc(100% - 10% * 8);
}
```

增加动画效果：
```css
.rainbow span::before,
.rainbow span::after {
	animation: animate 0.8s infinite alternate;
	filter: opacity(0);
}

@keyframes animate {
	from {
		filter: opacity(0);
	}

	to {
		filter: opacity(1);
	}
}
```

为图层设置延时，增强动感：
```css
.rainbow span:nth-child(1)::before {
	animation-delay: calc(0.8s - 0.1s * 1);
}

.rainbow span:nth-child(1)::after {
	animation-delay: calc(0.8s - 0.1s * 2);
}

.rainbow span:nth-child(2)::before {
	animation-delay: calc(0.8s - 0.1s * 3);
}

.rainbow span:nth-child(2)::after {
	animation-delay: calc(0.8s - 0.1s * 4);
}

.rainbow span:nth-child(3)::before {
	animation-delay: calc(0.8s - 0.1s * 5);
}

.rainbow span:nth-child(3)::after {
	animation-delay: calc(0.8s - 0.1s * 6);
}

.rainbow span:nth-child(4)::before {
	animation-delay: calc(0.8s - 0.1s * 7);
}

.rainbow span:nth-child(4)::after {
	animation-delay: calc(0.8s - 0.1s * 8);
}
```

最后，把原始文本设置为透明色：
```css
.rainbow {
	color: transparent;
}
```

大功告成！
