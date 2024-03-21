+++
title = '在文本前后穿梭的边框'
date = 2018-05-27T15:46:03+08:00
image = '/fe/img/thumbs/034.png'
summary = '#34'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/qYepNv](https://codepen.io/comehope/pen/qYepNv)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cQ73Vt8](https://scrimba.com/p/pEgDAM/cQ73Vt8)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含文本：
```html
<div class="warning">ERROR 404</div>
```

居中显示：
```css
body {
  margin: 0;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgb(20%, 20%, 20%);
}
```

定义文字样式：
```css
.warning {
	color: whitesmoke;
	font-size: 100px;
	font-family: sans-serif;
	font-weight: bold;
}
```

用伪元素定义边框尺寸：
```css
.warning {
	position: relative;
	padding: 0.6em 0.4em;
}

.warning::before,
.warning::after {
	content: '';
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	border: 0.2em solid;
	box-sizing: border-box;
}
```

把边框分为两部分，拼在一起：
```css
.warning::before,
.warning::after {
	border: 0.2em solid transparent;
	color: orangered;
}

.warning::before {
	border-top-color: currentColor;
	border-right-color: currentColor;
}

.warning::after {
	border-bottom-color: currentColor;
	border-left-color: currentColor;
}
```

把上边框和右边框下沉一层：
```css
.warning::before {
	z-index: -1;
}
```

为下边框和在边框加上阴影：
```css
.warning::after {
	box-shadow: 0.3em 0.3em 0.3em rgba(20%, 20%, 20%, 0.8);
}
```

最后，让边框转起来：
```css
.warning::before,
.warning::after {
	animation: rotating 10s infinite;
}

@keyframes rotating {
	to {
		transform: rotate(360deg);
	}
}
```

大功告成！
