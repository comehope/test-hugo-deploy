+++
title = '同心圆弧旋转 loading 特效'
date = 2018-05-02T15:11:39+08:00
image = '/fe/img/thumbs/010.png'
summary = '#10'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/zhang-ou/pen/OZmXQX](https://codepen.io/zhang-ou/pen/OZmXQX)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/c/cPdWVuD](https://scrimba.com/c/cPdWVuD)

## 源代码下载

请从 github 下载。

[https://github.com/comehope/front-end-daily-challenges/tree/master/010-concentric-arc-rotating-loader-animation](https://github.com/comehope/front-end-daily-challenges/tree/master/010-concentric-arc-rotating-loader-animation)

## 代码解读

定义 dom，只包含一个元素：
```html
<div class="circle"></div>
```

居中显示：
```css
html,
body,
.circle {
	height: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: black;
}
```

一共画三层圆弧，先画最外一层的样式：
```css
.circle {
	width: 10em;
	height: 10em;
	border-width: 0.4em;
	border-style: solid;
	border-radius: 50%;
	border-left-color: transparent;
	border-right-color: transparent;
	border-top-color: red;
	border-bottom-color: blue;
}
```

再用伪元素画中间一层的样式：
```css
.circle {
	position: relative;
}

.circle::before {
	content: '';
	position: absolute;
	width: 75%;
	height: 75%;
	border-width: 0.4em;
	border-style: solid;
	border-radius: 50%;
	border-left-color: transparent;
	border-right-color: transparent;
	border-top-color: orange;
	border-bottom-color: cyan;
}
```

再用伪元素画最内一层的样式：
```css
.circle::before {
	content: '';
	position: absolute;
	width: 75%;
	height: 75%;
	border-width: 0.4em;
	border-style: solid;
	border-radius: 50%;
	border-left-color: transparent;
	border-right-color: transparent;
	border-top-color: yellow;
	border-bottom-color: limegreen;
}
```

定义动画效果：
```css
@keyframes animate {
	from {
		transform: rotate(0deg);
	}

	to {
		transform: rotate(1440deg);
	}
}
```

最后，应用动画效果到每层：
```css
.circle {
	animation: animate 4s ease-in-out infinite alternate;
}

.circle::before {
	animation: animate 8s ease-in-out infinite alternate;
}

.circle::after {
	animation: animate 16s ease-in-out infinite alternate;
}
```

大功告成！
