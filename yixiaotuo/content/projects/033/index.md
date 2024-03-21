+++
title = '牛奶文字'
date = 2018-05-26T15:45:48+08:00
image = '/fe/img/thumbs/033.png'
summary = '#33'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/MGNWOm](https://codepen.io/comehope/pen/MGNWOm)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cvPryA6](https://scrimba.com/p/pEgDAM/cvPryA6)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 DOM，容器中包含 2 段文本：
```html
<div class="container">
	<p>Explorer</p>
	<p>Discovery</p>
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
	background-color: black;
}
```

设置字体样式：
```css
p {
	color: white;
	font-size: 50px;
	font-weight: bold;
	font-family: sans-serif;
	text-transform: uppercase;
	text-align: center;
}
```

让 2 段文本重叠：
```css
p {
	margin: 0;
}

p:nth-child(1) {
	transform: translateY(50%);
}

p:nth-child(2) {
	transform: translateY(-50%);
}
```

定义动画，让 2 段文本交替显示：
```css
p {
	animation: show-hide 10s infinite;
	filter: opacity(0);
}

p:nth-child(1) {
	animation-direction: normal;
}

p:nth-child(2) {
	animation-direction: reverse;
}

@keyframes show-hide {
	0% {
		filter: opacity(0);
	}

	25% {
		filter: opacity(1);
	}

	40% {
		filter: opacity(1);
	}

	50% {
		filter: opacity(0);
	}
}
```

增加字间距的变化效果：
```css
@keyframes show-hide {
	0% {
		filter: opacity(0);
		letter-spacing: -0.8em;
	}

	25% {
		filter: opacity(1);
	}

	40% {
		filter: opacity(1);
	}

	50% {
		filter: opacity(0);
		letter-spacing: 0.24em;
	}
}
```

增加文本模糊效果：
```css
@keyframes show-hide {
	0% {
		filter: opacity(0) blur(0.08em);
		letter-spacing: -0.8em;
	}

	25% {
		filter: opacity(1) blur(0.08em);
	}

	40% {
		filter: opacity(1) blur(0.24em);
	}

	50% {
		filter: opacity(0) blur(0.24em);
		letter-spacing: 0.24em;
	}
}
```

最后，为容器设置对比度滤镜：
```css
.container {
	filter: contrast(10);
	background-color: black;
	overflow: hidden;
}
```

大功告成！

