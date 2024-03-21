+++
title = '变色旋转 loading 特效'
date = 2018-05-10T15:36:35+08:00
image = '/fe/img/thumbs/017.png'
summary = '#17'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/bMvbRp](https://codepen.io/comehope/pen/bMvbRp)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cp2dZcQ](https://scrimba.com/p/pEgDAM/cp2dZcQ)

## 源代码下载

请从 github 下载。

[https://github.com/comehope/front-end-daily-challenges/tree/master/017-swapping-colors-loader-animation](https://github.com/comehope/front-end-daily-challenges/tree/master/017-swapping-colors-loader-animation)

## 代码解读

定义 dom，一个容器中包含一个 span：
```html
<div class="loader">
	<span></span>
</div>
```

居中显示：
```css
html,
body,
.loader {
	height: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: black;
}
```

设置 span 的样式：
```css
.loader {
	width: 10em;
	height: 10em;
	font-size: 28px;
	position: relative;
}

.loader span {
	position: absolute;
	width: 100%;
	height: 100%;
	background-color: rgba(100%, 0%, 0%, 0.3);
	box-sizing: border-box;
	border: 0.5em solid;
	border-color: white rgba(100%, 100%, 100%, 0.2);
}
```

在 dom 中把 span 增加到 5 个：
```html
<div class="loader">
	<span></span>
	<span></span>
	<span></span>
	<span></span>
	<span></span>
</div>
```

分别设置 5 个 span 的尺寸：
```css
.loader span:nth-child(1) {
	width: calc(20% + 20% * (5 - 1));
	height: calc(20% + 20% * (5 - 1));
}

.loader span:nth-child(2) {
	width: calc(20% + 20% * (5 - 2));
	height: calc(20% + 20% * (5 - 2));
}

.loader span:nth-child(3) {
	width: calc(20% + 20% * (5 - 3));
	height: calc(20% + 20% * (5 - 3));
}

.loader span:nth-child(4) {
	width: calc(20% + 20% * (5 - 4));
	height: calc(20% + 20% * (5 - 4));
}

.loader span:nth-child(5) {
	width: calc(20% + 20% * (5 - 5));
	height: calc(20% + 20% * (5 - 5));
}
```

增加颜色变幻的动画效果：
```css
.loader span {
	animation: animate 5s ease-in-out infinite alternate;
}

@keyframes animate {
	0% {
		/* red */
		background-color: rgba(100%, 0%, 0%, 0.3);
	}

	25% {
		/* yellow */
		background-color: rgba(100%, 100%, 0%, 0.3);
	}

	50% {
		/* green */
		background-color: rgba(0%, 100%, 0%, 0.3);
	}

	75% {
		/* blue */
		background-color: rgba(0%, 0%, 100%, 0.3);
	}

	100% {
		/* purple */
		background-color: rgba(100%, 0%, 100%, 0.3);
	}
}
```

再增加旋转效果：
```css
@keyframes animate {
	0% {
		transform: rotate(0deg);
	}

	100% {
		transform: rotate(720deg);
	}
}
```

最后，为每个 span 设置动画延时，增加动感：
```css
.loader span:nth-child(1) {
	animation-delay: calc(0.2s * (5 - 1));
}

.loader span:nth-child(2) {
	animation-delay: calc(0.2s * (5 - 2));
}

.loader span:nth-child(3) {
	animation-delay: calc(0.2s * (5 - 3));
}

.loader span:nth-child(4) {
	animation-delay: calc(0.2s * (5 - 4));
}

.loader span:nth-child(5) {
	animation-delay: calc(0.2s * (5 - 5));
}
```

大功告成！
