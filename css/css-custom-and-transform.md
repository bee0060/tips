# CSS变量与transform

本贴简单讲讲用css变量结合transform（形变），来更简洁的实现多种形变同时生效。

如果对CSS变量或transform不太了解的可以查看：
CSS变量：
- MDN: https://developer.mozilla.org/zh-CN/docs/Web/CSS/Using_CSS_custom_properties
- ruanyifeng: https://www.ruanyifeng.com/blog/2017/05/css-variables.html

transform:
- MDN: https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform


由于transform可以设置多种形变， 如：
```css
div {
  transform: translate(12px, 50%) scale(2, 0.5) rotate(0.5turn) ...;
}
```

如果只是直接写这个样式，当然没什么问题。 
但有时我们会需要在某些情况下增加或改变一些形变规则， 如鼠标悬停（`:hover`) 或被激活状态（`.active`)时等等。

如果不借助css变量，我们的css可能看起来时这样:
```css
div {
  transform: translate(12px, 50%);
}

div:hover {
  transform: translate(12px, 50%) scale(2);
}

div.active {
  transform: translate(12px, 50%) rotate(0.5turn);
}

div.active:hover {
  transform: translate(12px, 50%) scale(2) rotate(0.5turn);
}

```

很麻烦， 实际情况可能更麻烦，有各种排列组合。 麻烦的原因在于， 我们不太好单独设置transform中的单个形变函数（新标准有将形变函数拆出来的更新，如[rotate](https://developer.mozilla.org/zh-CN/docs/Web/CSS/rotate)等，但是由于还未普及，暂不讨论）。
这时我们可以借助css变量来简化上述代码：

```css
div {
  --scale-time: 1;
  --rotate-angle: 0;
  transform: translate(12px, 50%) scale(var(--scale-time, 1)) rotate(var(--rotate-angle, 0));
}

div:hover {
  --scale-time: 2;
}

div.active {
  --rotate-angle: 0.5turn;
}
```

这样可以极大简化我们的css代码中transform的值的设置。 transform变成一个像函数的属性， css变量则是参数，在不同的情况给css变量设置不同的值即可。

除了transform， 其他`复合`型的css属性都可以使用这个策略， 如:
- shadow
- transition
- font

等等






