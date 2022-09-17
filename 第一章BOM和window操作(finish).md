# 第一章 BOM 

### 1.1 什么是BOM

BOM ( Browser Object Model )即浏览器对象模型,它提供了独位于内容而与浏览器窗口进行交互的对象,其核心
对象是window。
BOM由一系列相关的对象构成,組每个对象都提供了很多方法与属性。
BOM缺乏标准, JavaScript 语法的标准化组织是ECMA , DOM的标准化组织是W3C , BOM最初是Netscape浏
览器标准的一部分。

- **DOM**

1、文档对象模型
2、DOM就是把[文档」当做一个「对象来看待
3、DOM的顶级对象是document
4、DOM主要学习的是操作页面素
5、DOM是W3C标准规范

- **BOM**

1、浏览器对象模型
2、把「浏览器」当做一个「对象|来看待
3、BOM的顶级对象是window
4、BOM学习的是浏览器窗口交互的一些对象
5、BOM是浏览器厂商在各自浏览器上定义的,兼容性较差

### 1.2 BOM构成

BOM比DOM更大，它包含DOM

![01](https://img2022.cnblogs.com/blog/2940460/202209/2940460-20220916144716789-1036172348.png)

**`window对象是游览器的顶级对象`**，它具有双重色

- 它是js访问游览器窗口的一个接口
- 它是一个全局对象。 义在全局作用域中的变量、函数都会变成window对象的属性和方法。
- 在调用的时候可以省略window ,前学习的对话框都属于window对象方法,如alert(、prompt(）等。

> 注意： 
>
>   	window下的一个特殊属性 window.name

~~~js
 window.document.querySelector()//doc是win下面的一个对象
        var num = 10;
        console.log(num);
        //完整的写法
        console.log(window.num);

        function fn() {
            console.log(111);
        }
        fn();//现在写法
        window.fn();//完整写法
        // alert("111");
        // window.alert("111");
        //看看window里面有什么
        console.dir(window);

~~~

### 2.1 window常见事件

- **window加载事件**

~~~js
//window加载事件
        window.onload = function () { };
        window.addEventListener("load", function () { });
~~~

window.onload是窗口页面)加载事件，当文档内容完全加载完成会触发该事件(包括图像、脚本文件、CSS文件等),就调用的处理函数。

> 注意:
> 1.有了window.onload就可以把JS代码写到页面元素的上方,因为onload是等页面内容全部加载完毕，再去执行处理函数。
>
> 2.window.onload传统注册事件方式只能写- -次 ,如果有多个,郐以后一个window.onload为准。
>
> 3.如果使用addEventLi stener则没有限制

~~~js
document.addEventListener('DoMContentLoaded', function () { })
~~~

1.DOMContentLoaded事件触发时,仅当DOM加载完成,不包括样式表, flash等等。ie9以上支持

2.如果页面的图片很多的话，从用户访问到onload触发可能需要较长的时间，交互效果就不能实现,必然影响用户的体验,此时用DOMContentL oaded事件比较合适。

~~~js
		window.onload = function () { };
        window.addEventListener("load", function () { });
        document.addEventListener('DoMContentLoaded', function () { })
        // load等页面内容全部加载完毕，包含页面dom元素图片flash css等等
        // DOMContentLoaded是DOM加载完毕，不包含图片falsh css等就可以执行加载速度比load更快一些
~~~

- **调整窗口大小事件**

~~~js
 //调整窗口大小事件
        window.onresize = function () { }
        window.addEventListener("resize", function () { });
~~~

window . onresi ze是调整窗口大小加载事件,当触发时就调用的处理函数。

> 注意:
> 1.只要窗口大小发生像变化,就会触发这个事件。
> 2.我们经常利用这个事件完成响应式布局。window.innerWidth 当前屏幕的宽度

- 通过屏幕大小让页面元素显示或隐藏

~~~js
<style>
        div {
            width: 300px;
            height: 300px;
            background: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        window.addEventListener("load", function () { //页面加载完毕在执行js
            let div = document.querySelector('div');
            window.addEventListener("resize", function () {
                if (window.innerWidth <= 800) {
                    div.style.display = "none";
                } else {
                    div.style.display = "block";
                }
            })
        })
    </script>
</body>
~~~

### 2.2 window常见属性操作

~~~js
window.history//查看历史记录   前进后退查看的历史记录
window.history.length   //查看历史记录次数，打开新窗口不算次数包括 a标签 跳转
 window.location.href = "https://www.baidu.com/"  //页面内跳转
window.open('http://www.baidu.com') //新窗口打开链接
//***************************************
//本地存储数据，无期限
localStorage.setItem("stuname", '张三');
        console.log('本地存储了一个学生：');
 console.log(localStorage);//获取存储的数据
~~~

> 查看文档    
>
> https://www.runoob.com/jsref/obj-window.html

**window属性**

| [closed](https://www.runoob.com/jsref/prop-win-closed.html)  | 返回窗口是否已被关闭。                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [defaultStatus](https://www.runoob.com/jsref/prop-win-defaultstatus.html) | 设置或返回窗口状态栏中的默认文本。                           |
| [document](https://www.runoob.com/jsref/dom-obj-document.html) | 对 Document 对象的只读引用。(请参阅[对象](https://www.runoob.com/jsref/dom-obj-document.html)) |
| [frames](https://www.runoob.com/jsref/prop-win-frames.html)  | 返回窗口中所有命名的框架。该集合是 Window 对象的数组，每个 Window 对象在窗口中含有一个框架。 |
| [history](https://www.runoob.com/jsref/obj-history.html)     | 对 History 对象的只读引用。请参数 [History 对象](https://www.runoob.com/jsref/obj-history.html)。 |
| [innerHeight](https://www.runoob.com/jsref/prop-win-innerheight.html) | 返回窗口的文档显示区的高度。                                 |
| [innerWidth](https://www.runoob.com/jsref/prop-win-innerheight.html) | 返回窗口的文档显示区的宽度。                                 |
| [localStorage](https://www.runoob.com/jsref/prop-win-localstorage.html) | 在浏览器中存储 key/value 对。没有过期时间。                  |
| [length](https://www.runoob.com/jsref/prop-win-length.html)  | 设置或返回窗口中的框架数量。                                 |
| [location](https://www.runoob.com/jsref/obj-location.html)   | 用于窗口或框架的 Location 对象。请参阅 [Location 对象](https://www.runoob.com/jsref/obj-location.html)。 |
| [name](https://www.runoob.com/jsref/prop-win-name.html)      | 设置或返回窗口的名称。                                       |
| [navigator](https://www.runoob.com/jsref/obj-navigator.html) | 对 Navigator 对象的只读引用。请参数 [Navigator 对象](https://www.runoob.com/jsref/obj-navigator.html)。 |
| [opener](https://www.runoob.com/jsref/prop-win-opener.html)  | 返回对创建此窗口的窗口的引用。                               |
| [outerHeight](https://www.runoob.com/jsref/prop-win-outerheight.html) | 返回窗口的外部高度，包含工具条与滚动条。                     |
| [outerWidth](https://www.runoob.com/jsref/prop-win-outerheight.html) | 返回窗口的外部宽度，包含工具条与滚动条。                     |
| [pageXOffset](https://www.runoob.com/jsref/prop-win-pagexoffset.html) | 设置或返回当前页面相对于窗口显示区左上角的 X 位置。          |
| [pageYOffset](https://www.runoob.com/jsref/prop-win-pagexoffset.html) | 设置或返回当前页面相对于窗口显示区左上角的 Y 位置。          |
| [parent](https://www.runoob.com/jsref/prop-win-parent.html)  | 返回父窗口。                                                 |
| [screen](https://www.runoob.com/jsref/obj-screen.html)       | 对 Screen 对象的只读引用。请参数 [Screen 对象](https://www.runoob.com/jsref/obj-screen.html)。 |
| [screenLeft](https://www.runoob.com/jsref/prop-win-screenleft.html) | 返回相对于屏幕窗口的x坐标                                    |
| [screenTop](https://www.runoob.com/jsref/prop-win-screenleft.html) | 返回相对于屏幕窗口的y坐标                                    |
| [screenX](https://www.runoob.com/jsref/prop-win-screenx.html) | 返回相对于屏幕窗口的x坐标                                    |
| [sessionStorage](https://www.runoob.com/jsref/prop-win-sessionstorage.html) | 在浏览器中存储 key/value 对。 在关闭窗口或标签页之后将会删除这些数据。 |
| [screenY](https://www.runoob.com/jsref/prop-win-screenx.html) | 返回相对于屏幕窗口的y坐标                                    |
| [self](https://www.runoob.com/jsref/prop-win-self.html)      | 返回对当前窗口的引用。等价于 Window 属性。                   |
| [status](https://www.runoob.com/jsref/prop-win-status.html)  | 设置窗口状态栏的文本。                                       |
| [top](https://www.runoob.com/jsref/prop-win-top.html)        | 返回最顶层的父窗口。                                         |

**window对象操作**

| 方法                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [alert()](https://www.runoob.com/jsref/met-win-alert.html)   | 显示带有一段消息和一个确认按钮的警告框。                     |
| [atob()](https://www.runoob.com/jsref/met-win-atob.html)     | 解码一个 base-64 编码的字符串。                              |
| [btoa()](https://www.runoob.com/jsref/met-win-btoa.html)     | 创建一个 base-64 编码的字符串。                              |
| [blur()](https://www.runoob.com/jsref/met-win-blur.html)     | 把键盘焦点从顶层窗口移开。                                   |
| [clearInterval()](https://www.runoob.com/jsref/met-win-clearinterval.html) | 取消由 setInterval() 设置的 timeout。                        |
| [clearTimeout()](https://www.runoob.com/jsref/met-win-cleartimeout.html) | 取消由 setTimeout() 方法设置的 timeout。                     |
| [close()](https://www.runoob.com/jsref/met-win-close.html)   | 关闭浏览器窗口。                                             |
| [confirm()](https://www.runoob.com/jsref/met-win-confirm.html) | 显示带有一段消息以及确认按钮和取消按钮的对话框。             |
| [createPopup()](https://www.runoob.com/jsref/met-win-createpopup.html) | 创建一个 pop-up 窗口。                                       |
| [focus()](https://www.runoob.com/jsref/met-win-focus.html)   | 把键盘焦点给予一个窗口。                                     |
| [getSelection](https://www.runoob.com/jsref/met-win-getselection.html)() | 返回一个 Selection 对象，表示用户选择的文本范围或光标的当前位置。 |
| [getComputedStyle()](https://www.runoob.com/jsref/jsref-getcomputedstyle.html) | 获取指定元素的 CSS 样式。                                    |
| [matchMedia()](https://www.runoob.com/jsref/met-win-matchmedia.html) | 该方法用来检查 media query 语句，它返回一个 MediaQueryList对象。 |
| [moveBy()](https://www.runoob.com/jsref/met-win-moveby.html) | 可相对窗口的当前坐标把它移动指定的像素。                     |
| [moveTo()](https://www.runoob.com/jsref/met-win-moveto.html) | 把窗口的左上角移动到一个指定的坐标。                         |
| [open()](https://www.runoob.com/jsref/met-win-open.html)     | 打开一个新的浏览器窗口或查找一个已命名的窗口。               |
| [print()](https://www.runoob.com/jsref/met-win-print.html)   | 打印当前窗口的内容。                                         |
| [prompt()](https://www.runoob.com/jsref/met-win-prompt.html) | 显示可提示用户输入的对话框。                                 |
| [resizeBy()](https://www.runoob.com/jsref/met-win-resizeby.html) | 按照指定的像素调整窗口的大小。                               |
| [resizeTo()](https://www.runoob.com/jsref/met-win-resizeto.html) | 把窗口的大小调整到指定的宽度和高度。                         |
| scroll()                                                     | 已废弃。 该方法已经使用了 [scrollTo()](https://www.runoob.com/jsref/met-win-scrollto.html) 方法来替代。 |
| [scrollBy()](https://www.runoob.com/jsref/met-win-scrollby.html) | 按照指定的像素值来滚动内容。                                 |
| [scrollTo()](https://www.runoob.com/jsref/met-win-scrollto.html) | 把内容滚动到指定的坐标。                                     |
| [setInterval()](https://www.runoob.com/jsref/met-win-setinterval.html) | 按照指定的周期（以毫秒计）来调用函数或计算表达式。           |
| [setTimeout()](https://www.runoob.com/jsref/met-win-settimeout.html) | 在指定的毫秒数后调用函数或计算表达式。                       |
| [stop()](https://www.runoob.com/jsref/met-win-stop.html)     | 停止页面载入。                                               |
| [postMessage()](https://www.runoob.com/jsref/met-win-postmessage.html) | 安全地实现跨源通信。                                         |



### 3.1 定时器

window对象给我们提供了2个非常好用的方法 -*** `定时器`***

#### setTimeout（）

- 创建定时器

~~~js
window.setTimeout（调用函数，[延迟的毫秒数]
~~~

setTimeout(方法用于设置一个定时器 ,该定时器在定时器到期后执行调用函数。

> 注意:
> 1. window可以省略。
> 2. 这个调用函数可以直接写函数,或者写函数名或者采取字符串‘函数名()'三种形式。 第三种不推荐
> 3. 延迟的毫秒数省略默认是0 ,如果写,必须是秒。
> 4. 因为定时器可能有很多,所以我们经常给定时器赋值一 个标识符。

~~~js
 //2.这个延迟时间是毫秒，但是省略，如果省略则默认为0
        //3.这个调用函数可以直接写函数 还可以写  函数名  还有一种写法 '函数名（）'
        //页面中可能有很多定时器 ，我们经常给他一个标识符 （名字）
        function callback() {
            {
                console.log('时间到了，执行吧');
            }
        }
        //setTimeout(callback, 2000);
        // setTimeout('callback()', 2000); // 不提倡这种写法
        var timer1 = setTimeout(callback, 2000);
        var timer2 = setTimeout(callback, 5000);
~~~

~~~
setTimeout0这个调用函数我们也称为回调函数callback
普通函数是按照代码顺序直接调用。
而这个函数,需要等待时间,时间到了才去调用这个函数,因此称为回调函数。
简单理解:回调,就是回头调用的意思。上一 件事干完,再回头再调用这个函数。
以前我们讲的element.onclick = function(){}或者element. addEventListener("click", fn);面的函数也是回调函数。
~~~

- 停止setTimeout（）定时器

clearTimeout ()方法取消了先前通过调用setTimeout ()建立的定时器。

~~~js
// window.clearTimeout((timeoutID)); 停止定时器
            var btn = document.querySelector("button");
            var div = document.querySelector("div");
            var timer = setTimeout(function () {
                div.innerHTML = "不犯法京东数科飞机付货款啦";
            }, 3000);
            btn.addEventListener('click', function () {
                clearTimeout(timer);
            })
~~~

> 注意:
> 1. window可以省略。
> 2. 面的参数就是定时器的标识符。

#### setInterval（）

- **创建定时器**

~~~js
window.setInterval(回调函数,[间隔的毫秒数])
~~~

setInterval()方法重复调用一个函数,每隔这个时间,就去调用一-次回调函数。

> 注意:
> 1. window可以省略。
> 2. 这个调用函数可以直接写函数,或者写函数名或者采取字符串'函数名()'三种形式。
> 3. 间隔的毫秒数省略默认是0 ,如果写,必须是毫秒,示每隔多少秒就自动调用这个函数。
> 4. 因为定时器可能有多, 所以我们经常给定时器赋值一个标识符。

~~~js
setInterval(function () {
            console.log('哈哈哈');
        }, 1000)
~~~

- 制作京东倒计时效果

<img src="../img/dom-1/02.png"  />

~~~js
  <style>
        div {
            width: 200px;
            height: 300px;
            border: 1px solid #000;
            display: flex;
            align-items: center;
            justify-content: space-around;
            margin: 20% auto;
        }

        span {
            display: inline-block;
            width: 50px;
            height: 50px;
            border: 1px solid #000;
            text-align: center;
            line-height: 50px;
            font-size: 30px;
            font-weight: bolder;
            background: #000;
            color: #FFFFFF;
        }
    </style>
</head>

<body>
    <div>
        <span class="hour">1</span>
        <span class="minute">2</span>
        <span class="second">3</span>
    </div>
    <script>
        //获取元素
        let hour = document.querySelector('.hour');
        let minute = document.querySelector('.minute');
        let second = document.querySelector('.second');
        var inputTime = +new Date('2022-10-1 00:00:00'); // 返回的是用户输入时间总的毫秒数
        countDown();//先调用一次函数刷新页面不会显示sapn里面的值  必须得放在输入的后面
        setInterval(countDown, 1000);//设置定时器
        //倒计时
        function countDown() {
            var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
            var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数
            var d = parseInt(times / 60 / 60 / 24); // 天
            d = d < 10 ? '0' + d : d;
            var h = parseInt(times / 60 / 60 % 24); //时
            h = h < 10 ? '0' + h : h;
            hour.innerHTML = h;
            var m = parseInt(times / 60 % 60); // 分
            m = m < 10 ? '0' + m : m;
            minute.innerHTML = m;
            var s = parseInt(times % 60); // 当前的秒
            s = s < 10 ? '0' + s : s;
            second.innerHTML = s;
        }
    </script>
</body>
~~~

<img src="../img/dom-1/03.png"  />

- **停止定时器**

~~~js
window.clearInterval(intervalId);//停止定时器
~~~

clearInterval ()方法取消了先前通过调用setInterval ()建立的定时器。

> 注意:
> 1. window可以省略。
> 2. 面的参数就是定时器的标识符。

**京东停止**

~~~js
<style>
        div {
            width: 200px;
            height: 300px;
            border: 1px solid #000;
            display: flex;
            align-items: center;
            justify-content: space-around;
            flex-wrap: wrap;
            margin: 20% auto;
        }

        span {
            display: inline-block;
            width: 50px;
            height: 50px;
            border: 1px solid #000;
            text-align: center;
            line-height: 50px;
            font-size: 30px;
            font-weight: bolder;
            background: #000;
            color: #FFFFFF;
        }
    </style>
</head>

<body>
    <div>
        <span class="hour">00</span>
        <span class="minute">00</span>
        <span class="second">00</span>
        <button>开启定时器</button>
        <button>关闭定时器</button>
    </div>
    <script>
        //获取元素
        let hour = document.querySelector('.hour');
        let minute = document.querySelector('.minute');
        let second = document.querySelector('.second');
        let btn = document.querySelectorAll('button');
        var inputTime = +new Date('2022-10-1 00:00:00'); // 返回的是用户输入时间总的毫秒数
       let open = null; //空对象
		btn[0].addEventListener('click', function () {
            open = setInterval(countDown, 1000);
        })
        btn[1].addEventListener('click', function () {
            window.clearInterval(open)
        })
        //countDown();//先调用一次函数刷新页面不会显示sapn里面的值  必须得放在输入的后面
        //setInterval(countDown, 1000);//设置定时器
        //倒计时
        function countDown() {
            var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
            var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数
            var d = parseInt(times / 60 / 60 / 24); // 天
            d = d < 10 ? '0' + d : d;
            var h = parseInt(times / 60 / 60 % 24); //时
            h = h < 10 ? '0' + h : h;
            hour.innerHTML = h;
            var m = parseInt(times / 60 % 60); // 分
            m = m < 10 ? '0' + m : m;
            minute.innerHTML = m;
            var s = parseInt(times % 60); // 当前的秒
            s = s < 10 ? '0' + s : s;
            second.innerHTML = s;
        }


        // window.clearInterval(intervalId);


    </script>
~~~















































