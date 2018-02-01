## JS 原型链笔记


### MDN 对于原型的解释
> JavaScript 常被描述为一种基于原型的语言 (prototype-based language)——每个对象拥有一个原型对象，对象以其原型为模板、从原型继承方法和属性。原型对象也可能拥有原型，并从中继承方法和属性，一层一层、以此类推。这种关系常被称为原型链 (prototype chain)，它解释了为何一个对象会拥有定义在其他对象中的属性和方法。
准确地说，这些属性和方法定义在Object的构造器函数(constructor functions)之上的prototype属性上，而非对象实例本身。
在传统的 OOP 中，首先定义“类”，此后创建对象实例时，类中定义的所有属性和方法都被复制到实例中。在 JavaScript 中并不如此复制——而是在对象实例和它的构造器之间建立一个链接（它是__proto__属性，是从构造函数的prototype属性派生的），之后通过上溯原型链，在构造器中找到这些属性和方法。

实例对象中的\_\_proto\_\_属性指向它的构造函数的prototype属性，也就是俗称的原型，同理，往上可以继续追溯。
`Object.getPrototypeOf(new Foobar()) === Foobar.prototype //true`

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
