+++
title = '彩虹背景文字'
date = 2018-06-22T17:09:04+08:00
image = '/test-hugo-deploy/img/thumbs/059.png'
summary = '#59'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/jKxyXN](https://codepen.io/comehope/pen/jKxyXN)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cZ8LNA7](https://scrimba.com/p/pEgDAM/cZ8LNA7)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中有一段文本：
```html
<p>thanks</p>
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

定义文字样式：
```css
p {
	font-size: 20vw;
	color: white;
	font-family: sans-serif;
	text-transform: uppercase;
	font-weight: bold;
}
```

设置彩虹背景：
```css
p {
	background-image: linear-gradient(
		to right,
		orangered,
		orange,
		gold,
		lightgreen,
		cyan,
		dodgerblue,
		mediumpurple,
		hotpink,
		orangered);
	background-size: 110vw;
}
```

定义动画效果：
```css
p {
	animation: sliding 30s linear infinite;
}

@keyframes sliding {
	to {
		background-position: -2000vw;
	}
}
```

最后，把彩虹背景移到文字下面：
```css
p {
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
}
```

大功告成！
