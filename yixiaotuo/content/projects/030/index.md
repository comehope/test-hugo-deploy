+++
title = '晃动的公告牌'
date = 2018-05-23T15:44:42+08:00
image = '/test-hugo-deploy/img/thumbs/030.png'
summary = '#30 已发布30个作品，感谢大家的支持！'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/wjZoGV](https://codepen.io/comehope/pen/wjZoGV)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/c/cD8yKHb](https://scrimba.com/c/cD8yKHb)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含公告牌、挂公告牌的细绳和固定绳子的 3 个图钉：
```html
<div class="signboard">
	<div class="sign">THANKS</div>
	<div class="strings"></div>
	<div class="pin top"></div>
	<div class="pin left"></div>
	<div class="pin right"></div>
</div>
```

居中显示：
```css
html, body {
	width: 100%;
	height: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	background: radial-gradient(circle at center 60%, white, sandybrown);
}
```

定义公告牌的整体尺寸：
```css
.signboard {
	width: 400px;
	height: 300px;
}
```

设置木板的样式：
```css
.signboard {
	position: relative;
}

.sign {
	width: 100%;
	height: 200px;
	background: burlywood;
	border-radius: 15px;
	position: absolute;
	bottom: 0;
}
```

设置有雕刻效果的文字样式：
```css
.sign {
	color: saddlebrown;
	font-family: sans-serif;
	font-weight: bold;
	text-align: center;
	line-height: 200px;
	text-shadow: 0 2px 0 rgba(255, 255, 255, 0.3),
				0 -2px 0 rgba(0, 0, 0, 0.7);
}
```

画出细绳：
```css
.strings {
	width: 150px;
	height: 150px;
	border: 5px solid brown;
	position: absolute;
	border-right: none;
	border-bottom: none;
	transform: rotate(45deg);
	top: 38px;
	left: 122px;
}
```

画出细绳顶部的图钉：
```css
.pin {
	width: 25px;
	height: 25px;
	border-radius: 50%;
	position: absolute;
}

.pin.top {
	background: gray;
	left: 187px;
}
```

画出木板上左右两侧的图钉：
```css
.pin.left,
.pin.right {
	background: brown;
	top: 110px;
	box-shadow: 0 2px 0 rgba(255, 255, 255, 0.3);
}

.pin.left {
	left: 80px;
}

.pin.right {
	right: 80px;
}
```

最后，让告示牌晃动起来：
```css
.signboard {
	animation: swing 1.5s ease-in-out infinite alternate;
}

@keyframes swing {
	from {
		transform: rotate(10deg) translateX(-23px);
	}

	to {
		transform: rotate(-10deg) translateX(23px);
	}
}
```

大功告成！
