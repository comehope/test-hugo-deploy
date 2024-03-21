+++
title = '小球绕着圆环盘旋'
date = 2018-06-15T17:07:15+08:00
image = '/fe/img/thumbs/052.png'
summary = '#52'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/gKxyWo](https://codepen.io/comehope/pen/gKxyWo)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cg48mty](https://scrimba.com/p/pEgDAM/cg48mty)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含一个圆环和3个小球：
```html
<div class="container">
	<div class="ring"></div>
	<div class="spheres">
		<span class="sphere"></span>
		<span class="sphere"></span>
		<span class="sphere"></span>
	</div>
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
	background-color: darkslategray;
}
```

改变盒模型：
```css
* {
	box-sizing: border-box;
}
```

画出圆环：
```css
.container {
	position: relative;
	font-size: 20px;
}

.ring {
	position: relative;
	width: 10em;
	height: 10em;
	border: 1.5em solid paleturquoise;
	border-radius: 50%;
}
```

在圆环的左上方画出一个小球：
```css
.sphere {
	position: absolute;
	top: -20%;
  	left: -20%;
}

.sphere::after {
	content: '';
	position: absolute;
	width: 3em;
	height: 3em;
	background-color: lightseagreen;
	border-radius: 50%;
}
```

让小球在圆环的左上方盘旋：
```css
.sphere {
	width: 80%;
	height: 80%;
	animation: rotate 1.5s linear infinite;
}

@keyframes rotate {
  to {
    transform: rotate(360deg);
  }
}
```

让小球的圆环的上下穿梭：
```css
.ring {
	z-index: 2;
}

.sphere {
	animation: 
	    rotate 1.5s linear infinite,
	    overlapping 1.5s linear infinite;
}

@keyframes overlapping {
  to {
  	z-index: 2;
  }
}
```

通过设置动画延时，制造 3 个小球同时盘旋的效果：
```css
.sphere:nth-child(2) {
	animation-delay: -0.5s;
}

.sphere:nth-child(3) {
	animation-delay: -1s;
}
```

最后，让容器转动起来，制造小球围绕圆环盘旋的效果：
```css
.container {
	animation: rotate 5s linear infinite;
}
```

大功告成！
