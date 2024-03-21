+++
title = 'Vue logo'
date = 2018-06-05T15:51:01+08:00
image = '/test-hugo-deploy/img/thumbs/043.png'
summary = '#43'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/zaqKPx](https://codepen.io/comehope/pen/zaqKPx)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cw9WzuV](https://scrimba.com/p/pEgDAM/cw9WzuV)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，一个容器中包含 3 个子元素：
```html
<div class="vue">
	<span class="outer"></span>
	<span class="middle"></span>
	<span class="inner"></span>
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
	background-color: gray;
	background: radial-gradient(circle at center,lightgreen, white);
}
```

定义 3 层三角形的尺寸：
```css
:root {
	--outer-w: 49em;
	--outer-h: 40em;
	--middle-w: 32em;
	--middle-h: 26em;
	--inner-w: 16em;
	--inner-h: 13em;
}
```

定义容器的尺寸：
```css
.vue {
	width: var(--outer-w);
	height: var(--outer-h);
	font-size: 8px;
}
```

画出 3 层三角形：
```css
.vue {
	position: relative;
	display: flex;
	justify-content: center;
}

.outer,
.medium,
.inner {
	position: absolute;
	border-style: solid;
	border-color: transparent;
	border-top-width: var(--h);
	border-top-color: var(--c);
	border-left-width: calc(var(--w) / 2);
	border-right-width: calc(var(--w) / 2);
}

.outer {
	--w: var(--outer-w);
	--h: var(--outer-h);
	--c: #42b883; /* aragon green */
}

.middle {
	--w: var(--middle-w);
	--h: var(--middle-h);
	--c: #35495e;  /* derk denim */
}

.inner {
	--w: var(--inner-w);
	--h: var(--inner-h);
	--c: white;
}
```

定义动画效果：
```css
.outer,
.middle,
.inner {
	animation: 3s in ease-out infinite;
}

@keyframes in-and-out {
	0%, 5% {
		top: -100%;
	}

	15%, 80% {
		top: 0;
		filter: opacity(1);
		transform: scale(1);
	}

	90%, 100% {
		top: 100%;
		filter: opacity(0);
		transform: scale(0);
	}
}
```

最后，隐藏容器外的内容：
```css
.vue {
	overflow: hidden;
}
```

大功告成！

