### 什么是BOM

`BOM ( Browser Object Model)` 即**浏览器对象模型**，它提供了独立于内容而与**浏览器窗口进行交互的对象**，其核心对象是 `window`。

BOM 由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。

- 浏览器对象模型
- 把「浏览器」当做一个「对象」来看待
- BOM 的顶级对象是 `window`
- BOM 学习的是浏览器窗口交互的一些对象
- BOM 是浏览器厂商在各自浏览器上定义的，兼容性较差

BOM 的顶级对象 `window` 都可以省略不写，具体继续往下看👇

### API接口

> window.document  返回当前窗口内的文档节点
>
> window.location  包含有关文档当前位置的信息
>
> window.navigation 用于请求运行当前代码的应用程序的相关信息
>
> window.screen 返回当前渲染窗口中和屏幕有关的属性
>
> window.history 提供了操作浏览器*会话历史*（浏览器地址栏中访问的页面，以及当前页面中通过框架加载的页面）的接口

### 打开新窗口

##### window.open

通过 `window.open()` 既可以导航到一个特定的URL，也可以打开一个新的浏览器窗口

```js
// 如果浏览器中已经存在 Dachui 窗口，则在 Dachui 窗口打开指定 url,否则新创建一个窗口并命名为 Dachui
window.open('http://www.baidu.com','Dachui')
```

#### 窗口加载对象

##### window.onload

`window.onload` 是窗口(页面)加载事件，当文档内容完全加载完成会触发该事件(包括图像、脚本文件、CSS文件等)，就调用的处理函数。

```js
window.onload = function()｛
     // 文档加载完后做相关操作
｝
```

##### DOMcontentLoaded

`DOMcontentLoaded` 事件触发 ，仅当 DOM 加载完成，不包括样式表，图片，flash 等等。 IE9 以上才支持

如果页面的图片很多的话,从用户访问到 onload 触发可能需要较长的时间交互效果就不能实现，必然影响用户的体验，此时用`DOMContentLoaded` 事件比较合适。

```js
 btn.addEventListener('DOMcontentLoaded', () => {
     // 做相关操作
 })
```

##### window.onresize

`window.onresize` 是调整窗口大小加载事件，当触发时就调用的处理函数。

只要窗口大小发生变化，就会触发这个事件。

我们经常利用这个事件完成响应式布局。

```js
window.onresize = function() {
    // 浏览器窗口缩放的时候就会触发这个事件
}
```

##### 定时器

分别有 `window.setTimeout` 和 `window.setInterval` 两个定时器。前面的 `window.` 也可以省略掉。它们的第一个参数都是一个回调函数，可以是匿名的箭头函数，第二个参数是执行时间

```js
setTimeout(() => {
    console.log('一秒钟后会触发这个回调函数')
}, 1000)
```

```js
setInterval(() => {
    console.log('每一秒钟都会触发这个回调函数')
}, 1000)
```

也可以给它们起一个名字，然后结束某个事件之后把定时器给清除

```js
let timer = setInterval(() => {
    console.log('每一秒钟都会触发这个回调函数')
}, 1000)

clearTimeout(timer)
```

#### Location 对象

| location属性或方法    | 返回值                                                       |
| --------------------- | ------------------------------------------------------------ |
| location.pathname     | 服务器下面的文件路径                                         |
| location.hostname     | 当前浏览器访问 url 的域名                                    |
| location.port         | 当前浏览器访问 url 的端口信息                                |
| location.href         | 当前浏览器访问的 url                                         |
| location.search       | ?a=10&b=20 url的查询字符串，通常为？后面的内容               |
| location.protocol     | 所使用的 web 协议                                            |
| location.assign()     | 跟 href 一样，可以跳转页面（也称为重定向页面)                |
| location.replace()    | 替换当前页面，因为不记录历史，所以不能后退页面               |
| location.reload(参数) | 重新加载页面，相当于刷新按钮或者按f5，如果参数为 true 强制刷新 ctrl+f5 |

#### Navigator 对象

 对象包含有关访问者浏览器的信息

| navigator对象属性       | 返回值      |
| ----------------------- | ----------- |
| navigator.appCodeName   | 浏览器代号  |
| navigator.appName       | 浏览器名称  |
| navigator.appVersion    | 浏览器版本  |
| navigator.cookieEnabled | 平台信息    |
| navigator.platform      | 启用Cookies |
| navigator.userAgent     | 用户代理    |
| navigator.language      | 用户语言    |

#### History 对象

包含浏览器的历史

| history 对象方法  | 返回值                                                       |
| ----------------- | ------------------------------------------------------------ |
| history.back()    | 与在浏览器点击后退按钮效果相同                               |
| history.forward() | 与在浏览器中点击向前按钮效果相同                             |
| history.go(参数)  | 参数填 -1 的话就是后退，参数填 1 就是前进，跟上面的方法对应，0 的话就是刷新页面 |

### Screen 对象

包含有关用户屏幕的信息

| Screen 对象属性                                              | 返回值                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| window.screen.width <br />window.screen.height               | 获取整块屏幕的大小(桌面宽高的大小)                      |
| window.outerWidth<br />window.outerHeight                    | 获取浏览器宽高                                          |
| window.innerWidth<br />window.innerHeight                    | 获取当前窗口宽高(浏览器视口宽高，不包括控制台导航栏等） |
| element.offsetWidth<br />element.offsetHeight                | 获取元素布局宽高(包括border，不包括margin)              |
| element.scrollWidth<br />element.scrollHeight                | 获取元素内容宽高(溢出滚动可见范围的也算)                |
| document.documentElement.scrollTop<br />document.documentElement.scrollLeft | 获取滚动后被隐藏页面的宽高                              |
| element.offsetTop<br />element.offsetLeft                    | 获取元素距离顶部和左边距离                              |

