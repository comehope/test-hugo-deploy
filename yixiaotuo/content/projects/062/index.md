+++
title = '蒸锅'
date = 2018-06-26T17:09:52+08:00
image = '/fe/img/thumbs/062.png'
summary = '#62'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/YvOzNy](https://codepen.io/comehope/pen/YvOzNy)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cg46aSG](https://scrimba.com/p/pEgDAM/cg46aSG)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器中包含 2 个元素，分别表示锅盖和锅体：
```html
<div class="steamer">
	<div class="lid"></div>
	<div class="pot"></div>
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
	background: linear-gradient(to right bottom, violet, midnightblue);
}
```

定义容器尺寸：
```css
.steamer {
	width: 30em;
	height: 30em;
	background-color: snow;
	font-size: 10px;
	border-radius: 50%;
}
```

画出锅体：
```css
.steamer {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
}

.pot {
	position: relative;
	width: 16em;
	height: 12em;
	background: darkslateblue;
	border-radius: 0.5em 0.5em 6.5em 6.5em;
	border-right: 1.5em solid midnightblue;
}
```

画出锅把手：
```css
.steamer {
	z-index: 1;
}

.pot::before {
	content: '';
	position: absolute;
	width: 27em;
	height: 2.5em;
	background-color: tomato;
	left: -4.75em;
	top: 2em;
	z-index: -1;
}
```

画出锅盖：
```css
.lid {
	width: 17em;
	height: 6em;
	background-color: gold;
	position: relative;
	border-radius: 6em 6em 0 0;
	border-right: 1.5em solid goldenrod;

```

画出锅盖上的钮扣把手：
```css
.lid::before {
	content: '';
	position: absolute;
	width: 4em;
	height: 4em;
	background-color: tomato;
	border-radius: 50%;
	left: 7em;
	top: -2.5em;
}
```

接下来润色一下。

为锅体增加光影：
```css
.pot::after {
	content: '';
	position: absolute;
	width: 8em;
	height: 8em;
	border: 0.6em solid transparent;
	border-radius: 50%;
	border-left-color: white;
	transform: rotate(-60deg);
	top: 1em;
	left: 2em;
}
```

为锅盖增加光影：
```css
.lid::after {
	content: '';
	position: absolute;
	width: 7em;
	height: 7em;
	border: 0.6em solid transparent;
	border-radius: 50%;
	border-left-color: white;
	transform: rotate(40deg);
	top: 0.6em;
	left: 2.5em;
}
```

最后，增加动画效果：
```css
.lid {
	animation: animate 1s infinite alternate;
}

@keyframes animate {
	from {
		transform: traslateY(-0.5em);
	}

	to {
		transform: traslateY(0.5em);
	}
}
```

大功告成！

