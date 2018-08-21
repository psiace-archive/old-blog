---
layout: post
title: Javascript 轮播图
categories: [Javascript 练习]
tags: [Javascript, 沸点工作室]
excerpt: 原生代码实现轮播图，这里并没有什么特别的内容，前人已经总结的很好了，仅仅是用来自己记录一下。
comments: true
---

*这里并没有什么特别的内容，前人已经总结的很好了，仅仅是用来自己记录一下*

轮播图可以想象成几张图片并排连接成环带，进行抽动，被只能显示一张图的窗口遮盖其余部分。

轮播图的 html 部分很简单，在下面所示的代码中，我们的主体部分是 container 容器；其中 list 用来填充图片，为了实现无缝切换，我们采用在图 1 的前面放置图 5、在图 5 后面也放置了图 1 的办法；为了实现箭头切换和按钮切换两种模式，所以我们也添加了相应的部分。

```html
    <body>
        <div id = "container">
            <div id = "list" style = "left:-600px;">
                <img src="img/5.jpg" alt="" />
                <img src="img/1.jpg" alt="" />
                <img src="img/2.jpg" alt="" />
                <img src="img/3.jpg" alt="" />
                <img src="img/4.jpg" alt="" />
                <img src="img/5.jpg" alt="" />
                <img src="img/1.jpg" alt="" />  
            </div>
            <div id = "buttons">
                <span index="1" class="on"><center>1</center></span>
                <span index="2"><center>2</center></span>
                <span index="3"><center>3</center></span>
                <span index="4"><center>4</center></span>
                <span index="5"><center>5</center></span>
            </div>
            <a href="javascript:;" class="arrow" id="prev"><center>&lt;</center></a>
            <a href="javascript:;" class="arrow" id="next"><center>&gt;</center></a>
        </div>
    </body>
```

接下来看 CSS 部分，这里没有什么不好理解的，container 起到了窗口的作用，`overflow: hidden` 使得只有窗口内的图片可以显示，这里宽度设为 600px 仅仅是因为我们图片的宽度如此，这也是 list 的总宽度为 4200px 的原因（600 x 7）。如果回顾 html 代码的话，会看到 list 里我们设置了 `style = "left:-600px;"` 这使得我们的图片从第二张，也就是图 1 开始显示。为了能够在窗口上显示箭头和按钮，我们使用了 `z-index` 属性设置元素的堆叠顺序，拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。

```css
           body{
                padding:20px;
            }
            #container{
                width:600px; 
                height:392px; 
                border:3px solid #787878; 
                overflow: hidden; 
                position:relative;
                margin:0 auto; 
            }
            #list{
                width: 4200px; 
                height: 400px; 
                position: absolute; 
                z-index: 1;
            }
            #list img{
                float:left;
            }
            #buttons{
                position: absolute; 
                height: 15px; 
                width: 150px; 
                z-index: 2; 
                bottom: 20px; 
                left: 250px;
            }
            #buttons span{
                cursor: pointer; 
                float: left; 
                border:1px solid #fffffb; 
                width: 15px; 
                height: 15px; 
                background: #828282;
                margin-right: 5px;
                color: #fffffb;
            }
            #buttons .on{
                background: #f7c242;
            }
            .arrow{
                cursor: pointer; 
                display: none; line-height: 30px; 
                font-size: 36px; 
                font-weight: bold; 
                width: 36px; 
                height: 36px; 
                z-index: 1;
                position: absolute; 
                top: 180px; 
                background-color: #828282; 
                color: #fffffb; 
            }
            .arrow:hover{
                background-color: #787878;
            }
            #container:hover .arrow{
                display:block;
            }
            #prev{
                left:20px;
            }
            #next{
                right: 20px;
            }
```

最后是 Javascript 代码，该代码主要是设定一个计时器，每隔某一个指定时间就移动一次位置，使得图片切换。接下来考虑鼠标与轮播图的交互问题，要考虑当你点击按钮时会出现 4 -> 5 -> 1 和 5 <- 1 <- 2 的情况，以及离开时自动轮播，放上时停止计时器。
 
```javascript
            window.onload = function (){
                var container = document.getElementById('container');
                var list = document.getElementById('list');
                var buttons = document.getElementById('buttons').getElementsByTagName('span');
                var prev = document.getElementById('prev');
                var next = document.getElementById('next');
                var index = 1;
                var changed = false;
                var timer;
                function showButton(){
                    for(var i = 0;i < buttons.length; i++){
                        if (buttons[i].className == 'on'){
                            buttons[i].className = '';
                            break;
                        }
                    }
                    buttons[index - 1].className = 'on';
                }
                function change(offset){
                    changed = true;
                    var newleft = parseInt(list.style.left) + offset;
                    var time = 300;
                    var interval = 10;
                    var speed = offset/(time/interval);
                    function go(){
                        if((speed < 0 && parseInt(list.style.left) > newleft)||(speed > 0 && parseInt(list.style.left) < newleft)){
                             list.style.left = parseInt(list.style.left) + speed + 'px';
                               setTimeout(go,interval);
                        }
                    else{
                    changed = false;
                    list.style.left = newleft + 'px';
                    if(newleft > -600){
                        list.style.left = -3000 + 'px';
                    }
                    if(newleft < -3000){
                        list.style.left = -600 + 'px';
                        }
                      }
                    }
                    go();
                }
                function play(){
                    timer = setInterval(function(){
                        next.onclick();
                    },3000);
                }
                function stop(){
                    clearInterval(timer);
                }
                next.onclick = function() {
                    if(index == 5){
                        index = 1;
                    }
                    else{
                        index += 1;
                    }
                    showButton();
                    if(!changed){
                        change(-600);
                    }
                }
                prev.onclick = function() {
                    if(index == 1){
                        index = 5;
                    }
                    else{
                        index -= 1;
                    }
                    showButton();
                    if(!changed){
                        change(600);
                    }
                }         
                for(var i =0; i <buttons.length; i++){
                    buttons[i].onclick = function(){
                        if(this.classname == 'on'){
                            return;
                        }
                       var myindex = parseInt(this.getAttribute('index'));
                       var offset = -600 * (myindex - index);

                       index = myindex;
                       showButton();
                       if(!changed){
                        change(offset);
                       } 
                    }
                }
                container.onmouseover = stop;
                container.onmouseout = play;
                play();
            }
```


