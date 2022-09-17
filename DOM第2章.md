# 元素节点操作

### 切换图片

~~~html
 <style>
        p {
            text-align: center;
            width: 400px;
            height: 50px;
        }

        div {
            width: 400px;
            height: 400px;
            background: goldenrod;
            margin: auto;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
        }

        img {
            width: 360px;
            height: 200px;
        }

        .img {
            width: 360px;
            height: 200px;
        }
    </style>
</head>

<body>
    <div>
        <p></p>
        <div class="img">
            <img src="img/1 (1).jpg" alt="">
        </div>
        <button>上一张</button>
        <button>下一张</button>
    </div>
    <script>
        let btn = document.querySelectorAll('button');
        let img = document.querySelector('img');
        let span = document.querySelectorAll('span');
        let p = document.querySelector('p')
        let imgsrc = ["img/1 (1).jpg", "img/1 (2).jpg", "img/1 (3).jpg", "img/1 (4).jpg", "img/1 (5).jpg"];
        let n = 1;
        let index = 0;
        btn[0].addEventListener("click", () => {
            if (index <= 0) {
                index = imgsrc.length - 1;
            } else {
                index--;
            }
            n = index + 1;
            img.setAttribute("src", imgsrc[index]);
            p.innerHTML = '这里一共有 ' + imgsrc.length + ' 张图片这是' + n + '张';
        })
        btn[1].addEventListener("click", () => {
            if (index >= imgsrc.length - 1) {
                index = 0;
            } else {
                index++;
            }
            n = index + 1;
            img.setAttribute("src", imgsrc[index]);
            p.innerHTML = `这里一共有 ${imgsrc.length} 张图片这是${n}张`
        })
    </script>
</body>
~~~

### 节点操作

~~~js
<body>
    <section id="news">
        <header>京东快报<a href="#">更多 > </a></header>
        <ul class="red" name="myul">
            <li><a href="#">志玲姐姐：墨镜300减30</a></li>
            <li><a href="#">京东无锡馆正式启动</a></li>
            <li><a href="#">99元抢平板！品牌配件199-100</a></li>
            <li><a href="#">节能领跑京东先行</a></li>
            <li><a href="#">高洁丝实力撩货，领券五折</a></li>
        </ul>
    </section>
    <script>
        //修改列表项的内容
        //找到header元素，将它父级元素内容打印出来
        let sectionContent = document.querySelector("header").parentNode.innerHTML;
        console.log(sectionContent);
        //获取ul的孩子节点们  （子节点）
        let ul0bj = document.querySelector("ul");
        //Node节点对象﹑包含元素对象，属性对象，文本对象，解析空白对象(文本对象)//所以产生的孩子节点的数量并不是你想象中的元素对象
        console.log(ul0bj.childNodes);
        //获取ul的子元素 ()
        console.log(ul0bj.children);
        //获取ul元素的第一个子元素 li
        // console.log(ul0bj.firstChild);
        console.log(ul0bj.firstElementChild);
        //查看dom对象的类型
        console.log(ul0bj.nodeType, ul0bj.nodeName);  //元素的类型1   节点的名称就是标签名
        console.log(ul0bj.firstChild.nodeType, ul0bj.firstChild.nodeName);  //文本的类型3   节点名称#text
        console.log(document.nodeType, document.nodeName);    //document  的类型9    节点名称document
        //获取ul元素的最后一个子元素li
        console.log(ul0bj.lastChild);
        console.log(ul0bj.lastElementChild);
        //获取ul元素的第二个子元素li
        //先获取第一个子元素1i(志玲姐姐)，再找它的下一个元素
        console.log(ul0bj.firstElementChild.nextElementSibling);
        //获取ul元素的倒数第二个子元素li
        //先获取最后一个子元素li,再找他的上一个元素
        console.log(ul0bj.lastElementChild.previousElementSibling);
        //获取ul属性
        console.log(ul0bj.attributes[0].nodeType);   //2

        //总结：dom里面的元素对象的获取
        /*
        dom core方式  document.getElement系列
        /选择器方式，推荐使用
        document.querySelector()
        document.querySelectorAll()
        //层次关系方式
        找到父元素  parentNode
        所有孩子元素  children
        第一个孩子   firstElementChild
        最后一个孩子  lastElementChild
        下一个孩于  nextElementsibling
        上一个孩子  previousElementSibling

        node和element之间的关系
        Node父类型     1:元素类型 2:属性类型3: 文本类型 8:注释类型 9:文档类型
        Element子类型  (标签  p div html h1.... )

        通过判断和获取节点信息
        nodeType   nodeName    nodeValue

        掌握点击事件触发方法执行一些功能
        理解js :事件驱动机制
        */

    // var obj=document.getElementById("news");
    // var str=obj.lastChild.firstChild.nextSibling.nextSibling.innerHTML;
    // ////var str=obj.lastChild.lastChild.previousSibling.previousSibling.innerHTML;
    // var str=obj.lastElementChild.firstElementChild.innerHTML||obj.lastChild.firstChild.innerHTML;
    // alert(str);
    </script>
~~~

| 属性名称       | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| parentNode     | 返回节点的父节点                                             |
| childNodes     | 返回子节点集合，childNodes[i]                                |
| firstChild     | 返回节点的第一个子节点，最普遍的用法是访问，该元素的文本节点 |
| lastChild      | 返回节点的最后一个子节点                                     |
| nextSibling    | 下一个节点                                                   |
| previouSibling | 上一个节点                                                   |

