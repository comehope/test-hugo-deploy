+++
title = '菱形方块 loader 动画'
date = 2018-06-07T17:03:08+08:00
image = '/test-hugo-deploy/img/thumbs/045.png'
summary = '#45'
+++

![](./work.png)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/eKzjqK](https://codepen.io/comehope/pen/eKzjqK)

## 可交互视频教程

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/c8eyJUE](https://scrimba.com/p/pEgDAM/c8eyJUE)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，一个容器中包含 9 个子元素：
```html
<div class="loader">
	<span></span>
	<span></span>
	<span></span>
	<span></span>
	<span></span>
	<span></span>
	<span></span>
	<span></span>
	<span></span>
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

定义容器和子元素尺寸，是一个大正方形里包含 9 个小正方形：
```css
.loader {
	width: 10em;
	height: 10em;
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-gap: 0.5em;
}
```

把图案调整为大菱形中包含 9 个小菱形：
```css
.loader {
	transform: rotate(45deg);
}
```

以竖向的小菱形为单位，为小菱形块上色：
```css
.loader span {
	background-color: var(--c);
}

.loader span:nth-child(7) {
	--c: tomato;
}

.loader span:nth-child(4),
.loader span:nth-child(8) {
	--c: gold;
}

.loader span:nth-child(1),
.loader span:nth-child(5),
.loader span:nth-child(9) {
	--c: limegreen;
}

.loader span:nth-child(2),
.loader span:nth-child(6) {
	--c: dodgerblue;
}

.loader span:nth-child(3) {
	--c: mediumpurple;
}
```

定义动画效果：
```css
.loader span {
	animation: blinking 2s linear infinite;
	animation-delay: var(--d);
	transform: scale(0);
}

@keyframes blinking {
	0%, 100% {
		transform: scale(0);
	}

	40%, 80% {
		transform: scale(1);
	}
}
```

最后，为小菱形设置时延，增强动感：
```css
.loader span:nth-child(7) {
	--d: 0s;
}

.loader span:nth-child(4),
.loader span:nth-child(8) {
	--d: 0.2s;
}

.loader span:nth-child(1),
.loader span:nth-child(5),
.loader span:nth-child(9) {
	--d: 0.4s;
}

.loader span:nth-child(2),
.loader span:nth-child(6) {
	--d: 0.6s;
}

.loader span:nth-child(3) {
	--d: 0.8s;
}
```

大功告成！
