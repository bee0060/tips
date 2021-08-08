## reduce的一些常用场景

reduce方法挺常用的，这里简单写下几个常用的场景.

先上MDN的文档吧： [https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

下面的例子需要一些素材， 就拿下面这个学生成绩单数组举例：

```
var student = [
  { id: 1, name: '张三', score: 90, age: 21 },
  { id: 2, name: '李四', score: 87, age: 22 },
  { id: 3, name: '王五', score: 67, age: 20 },
  { id: 4, name: '赵六', score: 92, age: 23 },
  { id: 5, name: '田七', score: 78, age: 21 }
  ...
]
```

#### 求和
```
var sum = student.reduce((acc, cur) => acc + cur.score, 0)
```


#### 汇总

假设需要根据分数分A,B,C,D,E级， A: 90-100， B： 80-89， C: 70-79， D: 60-69， E： 0-59
```
var summary = student.reduce((acc, cur) => {
  var score = cur.score
  var grade = 'EDCBA'[parseInt(score / 10 - 5, 10)]  // 奇技淫巧，只为省点if/else代码，工作中慎用
  acc[grade] = acc[grade] + 1
  return acc
}, {
  A: 0,
  B: 0,
  C: 0,
  D: 0,
  E: 0
})
```


#### 数组转对象

数组转对象适用于需要频繁按id查询的场景，可以提高查询效率

```
var mapping = student.reduce((acc, cur) => Object.assign(acc, {
  [cur.id]: cur
}), {})
```


---------
