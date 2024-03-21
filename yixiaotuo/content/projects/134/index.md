+++
title = '树枝发芽'
date = 2018-09-13T17:48:15+08:00
image = '/test-hugo-deploy/img/thumbs/134.png'
summary = '#134'
+++

![](./work.gif)

## 效果预览

点击链接可以在 Codepen 预览。

[https://codepen.io/comehope/pen/LJmpXZ](https://codepen.io/comehope/pen/LJmpXZ)

## 可交互视频

此视频是可以交互的，你可以随时暂停视频，编辑视频中的代码。

[https://scrimba.com/p/pEgDAM/cdD8WHV](https://scrimba.com/p/pEgDAM/cdD8WHV)

## 源代码下载

每日前端实战系列的全部源代码请从 github 下载：

[https://github.com/comehope/front-end-daily-challenges](https://github.com/comehope/front-end-daily-challenges)

## 代码解读

定义 dom，容器包含 2 个元素，`branch` 代表枝，`leaves` 代表叶，叶有 6 个子元素，代表 6 个叶片：
```html
<figure class="sapling">
    <div class="branch"></div>
    <div class="leaves">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
    </div>
</figure>
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

定义容器尺寸，并设置子元素水平居中：
```css
.sapling {
    position: relative;
    width: 5em;
    height: 17.5em;
    font-size: 10px;
    display: flex;
    justify-content: center;
}
```

画出树枝：
```css
.branch {
    position: absolute;
    width: 0.2em;
    height: inherit;
    border-radius: 25%;
    background: burlywood;
}
```

定义树叶容器，设置为叶片在垂直方向均匀分布，并且从下到上排列：
```css
.leaves {
    position: absolute;
    width: inherit;
    height: 15em;
    top: 1em;
    display: flex;
    justify-content: space-between;
    flex-direction: column-reverse;
}
```

设置叶片的尺寸和和背景渐变效果：
```css
.leaves span {
    width: 2.5em;
    height: 2.5em;
    background: linear-gradient(55deg, #47cf73, #9df179, #47cf73 70%);
}
```

设置左右叶片的各自样式：
```css
.leaves span:nth-child(odd) {
    border-bottom-left-radius: 3em;
    border-top-right-radius: 3em;
    transform-origin: right bottom;
    align-self: flex-start;
}

.leaves span:nth-child(even) {
    border-bottom-right-radius: 3em;
    border-top-left-radius: 3em;
    transform-origin: left bottom;
    align-self: flex-end;
}
```

至此，静态效果绘制完成，接下来开始写动画脚本。
引入 GSAP 库：
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.0.2/TweenMax.min.js"></script>
```

声明一个时间线对象：
```javascript
let animation = new TimelineMax();
```

增加树枝的动画效果，并为这个动画设置一个标签 `branch`：
```javascript
animation.from('.branch', 4, {scaleY: 0, ease: Power1.easeOut}, 'branch');
```

增加树叶的动画效果，它的参数中有 3 个 `0.5`，从左到右的含义分别是动画时长、多个叶片动画的间隔时长、相对 `branch` 标签动画的延迟时间：
```javascript
animation.from('.branch', 4, {scaleY: 0, ease: Power1.easeOut}, 'branch')
    .staggerFrom('.leaves span', 0.5, {scale: 0, ease: Power1.easeOut}, 0.5, 0.5, 'branch');
```

增加叶片变黄的动画效果：
```javascript
animation.from('.branch', 4, {scaleY: 0, ease: Power1.easeOut}, 'branch')
    .staggerFrom('.leaves span', 0.5, {scale: 0, ease: Power1.easeOut}, 0.5, 0.5, 'branch')
    .to(['.branch', '.leaves span'], 3, {backgroundColor: 'yellow'});
```

增加淡出效果：
```javascript
animation.from('.branch', 4, {scaleY: 0, ease: Power1.easeOut}, 'branch')
    .staggerFrom('.leaves span', 0.5, {scale: 0, ease: Power1.easeOut}, 0.5, 0.5, 'branch')
    .to(['.branch', '.leaves span'], 3, {backgroundColor: 'yellow'})
    .to(['.branch', '.leaves span'], 1, {autoAlpha: 0});
```

修改声明时间线的代码，使动画重复播放：
```javascript
let animation = new TimelineMax({repeat: -1, repeatDelay: 0.5});
```

大功告成！
