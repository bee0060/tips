## 策略模式应用壹 - `干掉if else`


### 什么是策略模式

策略模式作为一种软件设计模式，指对象有某个行为，但是在不同的场景中，该行为有不同的实现算法。

### 例如

小明要去地点A，可以采用如下交通工具，每种交通工具会有不同的做法：

1. 步行 -> 穿好运动鞋，出发
2. 骑单车 -> 把单车推出来，骑上出发
3. 公交车 -> 带上零钱或公交车需要的卡， 出发
4. 地铁 -> 带上零钱或卡或手机，出发

体现到代码里, 最简单也是常见的写法可能就是:

```
function goTo(by) {
   if (by === 'walking') {
    // do something for walking
   } else if (by === 'bicycle') {
    // do something for bicycle
   } else if (by === 'bus') {
    // do something for bus
   } else if (by === 'subway') {
    // do something for subway
   }
}

```

这样写的问题主要有2个：
1. 各种出行方式的处理都在这里，代码里也就跟各种出行方式耦合了
2. 将来可能可以扩展更多的出行方式， 代码会越来越长、难读、难维护。

用策略模式的话，可以重构成以下这样：
```
const byWalking = () => {
   // do something for walking
}
const byBicycle = () => {
   // do something for bicycle
}
const byBus = () => {
   // do something for by bus
}
const bySubway = () => {
   // do something for subway
}
const ways = {
   walking: byWalking,
   bicycle: byBicycle,
   bus: byBus,
   subway: bySubway,
};

function goTo(by) {
   const handler = ways[by]
   if (typeof handler === 'function') {
      handler();
   }
}

```

好了，经过这样的重构， goTo与具体的出行方式已经解耦。
之后需要增加出行方式，只需要修改`ways`，或者提供一种注册方法往ways中注册即可，无需再修改goTo方法。
解耦和扩展性都得到了满足。
而且各出行方法都拆出去，更独立，可读性和可维护性也提升了。 

而且也更符合`开放封闭原则`：

> 开放封闭原则： 对扩展开放，对修改封闭


### 参考资料：
1. [策略模式](https://baike.baidu.com/item/%E7%AD%96%E7%95%A5%E6%A8%A1%E5%BC%8F/646307?fr=aladdin)
2. [开放封闭原则]()

