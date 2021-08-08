## 数组map、filter方法集合原生类型的小技巧


#### 过滤

filter + Boolean

```js
var arr = [{ name: 'someObject' }, null, 'someString', 100, 0, '']
var notNullArr = arr.filter(Boolean) // => [{ name: 'someObject' }, 'someString', 100]

/*
  有时处理数组时，经过map或filter后，得出的结果可能有undefined、null、0、空字符串等，可以用filter+Boolean进行简单快捷的过滤
*/
```


#### 字符串转数组

map + Number

```js
var str= '1,2,3,4,5,6,7,8,9'
var numbers = str.split(',').map(Number) // => [1, 2, 3, 4, 5, 6, 7, 8, 9]

/*
  数字（特别是一些id）和字符串互转的时候，可以简单的map+Number保证字符串转出来的是数字，
  避免后续使用id数组时，用includes、indexOf时因为类型问题无法返回期望的结果
*/
```


---------

