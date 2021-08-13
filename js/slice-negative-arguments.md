## slice 方法负参数截取字符串或数组最后N个字符或元素

先上文档： https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice

本贴仅说下slice传负数参数的用法，常规用法就不说了。
 
首先，slice方法对数组和字符串都适用。
 
当slice接受begin和end两个参数，传负数参数时，会从尾部往前数,begin和end都适用。使用这个特性，我们可以方便的截取尾部，或放弃尾部的若干个字符， 如

1. 某字符串不要最后一个字符，如`http:` 不要`:`，代码如下:
```js
var protocal = 'http:';
var pureProtocal = protocal.slice(0, -1); // => 'http'
```

2. 某数组只要最后N个，代码如下：
```
var str = [1, 2, 3, 4, 5];
var lastChar = str.slice(-1); // => [5]
```

2.1. 另外，如果是想判断字符串是否已某个字符串结尾，更好的办法是用`String.prototype.endsWith`方法

----

