## 2019-04-01 ~ 2019-04-07

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
 