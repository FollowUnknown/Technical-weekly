## 2019-04

### 阅读整理记录

#### 《掘金》「从源码中学习」Vue源码中的JS骚操作
http://note.youdao.com/noteshare?id=17cbaa2c9b6694dcd33bd8480e264cc5
```
  针对官方的一些代码规范和使用技巧，有了初步的认识。发现自身对于ts语法还不熟悉。
```

#### 《掘金小册》你不知道的 Chrome 调试技巧
https://juejin.im/book/5c526902e51d4543805ef35e

```
对Chrome开发者工具有更深入的了解，对于一些小技巧有眼前一亮的感觉，能增加自身对工具的认识和使用
```

### 知识整理记录

#### 如何在读取本地图片文件对象
```
  通过file获取文件对象-createObjectURL
  /**
    * [_uploadImg_getObjectURL 从对象中获取文件路径]
    */
  _uploadImg_getObjectURL(file) {
    let url = null
    if(window.createObjectURL !== undefined) { // basic
      url = window.createObjectURL(file);
    } else if(window.URL !== undefined) { // mozilla(firefox)
      url = window.URL.createObjectURL(file);
    } else if(window.webkitURL !== undefined) { // web_kit or chrome
      url = window.webkitURL.createObjectURL(file);
    }
    return url
  }
```

#### webpack 多页面

#### 前端搭建npm包
 

### 题目整理记录【答案在后面】

#### 1、写出以下代码执行结果
```
  var big = "test"
  var b = {
    a: "test1",
    showBig: function() {
      return this.big
    }
  }
  b.showBig.call(big)
```
#### 2、写出以下代码执行结果
```
  Object.prototype.a = 1;
  Function.prototype.a = 2;
  function test() {}
  var ins = new test()
  console.log(ins.a)
```

### 题目解析
```
1、
b.showA.call(big)： this 被指向全局变量big，上去寻找big变量，没找到，所以再往上寻找big的__protp__，因为big是字符串，所以big的__proto__ = String, String上存在big函数（big方法用于将字符串显示为大号字体），所以结果是打印了big的函数体
function big() {}
```

```
2、原型&原型链
// __proto__: 这个属性是实例对象的属性，每个实例对象都有一个__proto__属性，这个属性指向实例化该实例的构造函数的原型对象（prototype）
// prototype：每个构造函数都有一个prototype对象，这个对象指向该构造函数的原型。
ins.a = 1
ins.__proto__ = { constructor, __protp__ }
ins.__proto__ === test.prototype // true 指向实例化该实例的构造函数的原型对象
ins.__proto__.__proto__ === Object.prototype // true
ins.constructor.__proto__ === Function.prototype // true 实例对象构造器的原型链指向构建函数的原型对象
ins.constructor.__proto__ === Function.__proto__ // true

// 函数自身
test.constructor === Function // true 指向ƒ Function() { [native code] }
test.constructor.__proto__ === Function.prototype // true ，指向ƒ () { [native code] }
test.constructor.__proto__.__proto__ === Object.prototype // true prototype自身
test.__proto__ === Function.prototype // true
test.__proto__ === Function.__proto__ // true

// 对象自身属性方法和原型中的属性方法的区别: 对象自身的属性和方法只对该对象有效，而原型链中的属性方法对所有实例有效。
```

### 其他