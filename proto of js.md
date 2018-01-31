## JS 原型链笔记

![来源：https://juejin.im/post/5a6d90fd6fb9a01c96586152?utm_source=gold_browser_extension#heading-2](https://user-gold-cdn.xitu.io/2018/1/28/1613bfe784db6292?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

- instanceof: *判断consctructor的prototype属性值是否能在object的原型链中找到*
> MDN: The instanceof operator tests whether the prototype property of a constructor appears anywhere in the prototype chain of an object.
- JS原型链的顶部是null
- Object.\_\_proto\_\_ === Function.prototype


```javascript

//构造函数Letter
function Letter(number) {
  this.number = number
}

//原型添加getNumber方法
Letter.prototype.getNumber = function() {
  return this.number
}

//new新对象
let a = new Letter(1)
let b = new Letter(2)
let z = new Letter(26)

console.log(
  a.getNumber(), // 1
  b.getNumber(), // 2
  z.getNumber() // 26
)

```

![来源：https://juejin.im/post/5a6d90fd6fb9a01c96586152?utm_source=gold_browser_extension#heading-2](https://user-gold-cdn.xitu.io/2018/1/28/1613bfe83c26cac1?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
