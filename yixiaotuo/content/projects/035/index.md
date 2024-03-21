+++
title = '熊猫'
date = 2018-05-28T15:46:19+08:00
image = '/test-hugo-deploy/img/thumbs/035.png'
summary = '#35'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/odKrpy](https://codepen.io/comehope/pen/odKrpy)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cV7J6SK](https://scrimba.com/p/pEgDAM/cV7J6SK)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，只有一个元素：
```html
<div class="panda"></div>
```

居中显示：
```css
body {
	margin: 0;
	height: 100vh;
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: mediumturquoise;
}
```

定义容器尺寸：
```css
.panda {
	width: 21em;
	height: 16em;
	background-color: white;
}
```

画出头部轮廓：
```css
.panda {
	border: 0.5em solid #333;
	border-top-left-radius: 11em;
	border-top-right-radius: 11em;
	border-bottom-left-radius: 11em 6em;
	border-bottom-right-radius: 11em 6em;
}
```

画出右眼轮廓：
```css
.panda {
	position: relative;
}

.panda::before {
	content: '';
	position: absolute;
	width: 7em;
	height: 4em;
	left: 2.9em;
	top: 5.5em;
	background-color: #333;
	border-radius: 50% 50% 45% 42%;
	transform: rotate(-45deg);
}
```

类似地，画出左眼轮廓：
```css
.panda::after {
	content: '';
	position: absolute;
	width: 7em;
	height: 4em;
	left: 11.1em;
	top: 5.5em;
	background-color: #333;
	border-radius: 50% 50% 42% 45%;
	transform: rotate(45deg);
}
```

画出两只耳朵：
```css
.panda::before {
	box-shadow: 1em -7.2em 0 -0.4em #333;
}

.panda::after {
	box-shadow: -1em -7.2em 0 -0.4em #333;
}
```

画出两只眼睛：
```css
.panda::before {
	background-image: 
		radial-gradient(circle at 5.1em 2em, white 0.3em, transparent 0.3em), 
		radial-gradient(circle at 4.6em 2em, #333 0.7em, transparent 0.7em), 
		radial-gradient(circle at 4.5em 2em, white 1em, transparent 1em);
}

.panda::after {
	background-image: 
		radial-gradient(circle at 2.4em 1.5em, white 0.3em, transparent 0.3em), 
		radial-gradient(circle at 2.4em 2em, #333 0.7em, transparent 0.7em), 
		radial-gradient(circle at 2.5em 2em, white 1em, transparent 1em);
}
```

画出鼻子和嘴：
```css
.panda {
	background-image: 
		radial-gradient(ellipse at 50% 60%, #333 1.2em, transparent 1.2em),
		radial-gradient(ellipse at 50% 80%, #555 0.6em, transparent 0.6em);
}
```

增加一点立体效果：
```css
.panda {
	border-bottom-width: 1em;
	box-shadow: inset 1em -1em 0 #eee;
}
```

让右眼动起来：
```css
.panda::before {
	animation: before-animate 1s ease-in-out infinite alternate;
}

@keyframes before-animate {
	to {
		background-image: 
			radial-gradient(circle at 4.9em 1.8em, white 0.3em, transparent 0.3em), 
			radial-gradient(circle at 4.4em 1.8em, #333 0.7em, transparent 0.7em), 
			radial-gradient(circle at 4.5em 2em, white 1em, transparent 1em);
	}
}
```

类似地，让左眼也动起来：
```css
.panda::after {
	animation: after-animate 1s ease-in-out infinite alternate -1s;
}

@keyframes after-animate {
	to {
		background-image: 
			radial-gradient(circle at 2.6em 1.3em, white 0.3em, transparent 0.3em), 
			radial-gradient(circle at 2.6em 1.8em, #333 0.7em, transparent 0.7em), 
			radial-gradient(circle at 2.5em 2em, white 1em, transparent 1em);
	}
}
```

最后，让黑眼圈和耳朵也动起来：
```css
@keyframes before-animate {
	to {
		transform: rotate(-40deg);
	}
}

@keyframes after-animate {
	to {
		transform: rotate(40deg);
	}
}
```

大功告成！
