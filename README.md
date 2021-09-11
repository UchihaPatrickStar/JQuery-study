# JQuery-study笔记

### jq的学习

### 关于jQ版本问题

1.x：兼容ie678，但相对其他版本文件较大，官方只做BUG维护，功能不再新增，最终版本：1.12.4（2016年5月20日）。
2.x:不兼容ie678，相对1.x文件较小，官方只做BUG维护，功能不再新增，最终版本：2.2.4（2016年5月20日）。
3.x:不兼容ie678，只支持最新的浏览器，很多老的jQuery插件不支持这个版本，相对1.x文件较小，提供不包含Ajax/动画API版本。

### 关于jQ压缩版与未压缩版的问题

未压缩版方便我们的学习使用，可以看到jQ的源码，压缩版的在项目上线时使用，方便提升文件的传输速率。

### 原生JS和jQuery入口函数的区别（03.html）

1.原生JS和jQuery入口函数的加载模式不同，原生JS会等到DOM元素加载完毕，并且图片也加载完毕才会执行，jQuery会等到DOM元素加载完毕，但不会等到图片也加载完毕就会执行。
2.原生的JS如果编写了多个入口函数，后面编写的会覆盖前面编写的；jQuery中编写多个入口函数，后面的不会覆盖前面的。

### jQuery冲突问题（05.html）

1.释放$的使用权，释放操作必须在编写其他jQuery代码之前编写，释放之后就不能再使用$，改为使用jQuery。
2.自定义一个访问符号。

### jQuery对象（07.html）

1.什么是jQuery对象------jQuery对象是一个伪数组。
2.什么是伪数组？------有0到length-1的属性，并且有length属性。

### jQuery的each方法（9.html）

jQuery的each方法不仅可以遍历真数组，也可以遍历伪数组，而JS中的each方法只可以遍历真数组，不能遍历伪数组。

### jQuery的map方法（10.html）

1.和原生的forEach一样，不能遍历伪数组，和jQuery中的each静态方法一样，map静态方法也可以遍历伪数组。
2.jQuery中的each静态方法和map静态方法的区别: each静态方法默认的返回值就是，遍历谁就返回谁，map静态方法默认的返回值是一个空数组；each静态方法不支持在回调函数中对遍历的数组进行处理，map静态方法可以在回调函数中通过return对遍历的数组进行处理，然后生成一个新的数组返回。

### 静态方法holdReady方法（12.html）

$.holdReady(true);作用是暂停ready执行，即使DOM结构加载完成也不会执行ready函数，恢复为$.holdReady(false);

### jQuery内容选择器（14.html）

:contains(text) 作用：找到包含指定文本内容的指定元素。
:has(selector)  作用：找到包含指定子元素的指定元素。
:empty 作用：找到既没有文本内容也没有子元素的指定元素。
:parent 作用：找到有文本内容或有子元素的指定元素。

### 属性和属性节点（15.html）

1.什么是属性？
  对象身上保存的变量就是属性
2.如何操作属性？
            对象.属性名称 = 值;
            对象.属性名称;
            对象["属性名称"] = 值;
            对象["属性名称"];
3.什么是属性节点?
            在编写HTML代码中，在HTML标签中添加的属性就是属性节点
            在浏览器中找到span这个DOM元素之后，展开看到的都是属性
            在attributes属性中保存的所有内容都是属性节点
4.如何操作属性节点？
            DOM元素.setAttribute("属性名称","值");
            DOM.getAttribute("属性名称");
5.属性和属性节点有什么区别？
            任何对象都有属性，但是只有DOM对象才有属性节点

### jQuery的attr方法（16.html）

1.attr(name|pro|key,val|fn)
            作用：获取或者设置属性节点的值
            可以传递一个参数，也可以传递两个参数
            如果传递一个参数，代表获取属性节点的值
            如果传递两个参数，代表设置属性节点的值

            注意点：
            如果是获取：无论找到多少个元素，都只会返回第一个元素指定的属性节点的值
            如果是设置：找到多少个元素，就会设置多少个元素
            如果是设置：如果设置的属性节点不存在，name系统会自动新增
2.removeAttr(name)
            删除属性节点

            注意点：
            会删除所有找到元素指定的属性节点
            $("span").removeAttr("class name");删除多个属性节点用空格隔开

### jQuery的prop方法（17.html）

1.prop方法
            有则修改，无则新增
            特点和attr方法一致
2.removeProp方法
            特点和removeAttr方法一致
注意点：
            prop方法不仅能够操作属性，它还能操作属性节点
            官方推荐在操作属性节点时，具有true和false两个属性的属性节点，如checked，selected或者disabled使用prop(),其他使用attr()

### jQuery操作类相关的方法（19.html）

1.addClass(class|fn)
           作用：添加一个类
           如果要添加多个类，多个类名之间用空格隔开即可
2.removeClass([class|fn])
           作用：删除一个类
           如果要删除多个类，多个类名之间用空格隔开即可
3.toggleClass(class|fn[.sw])
           作用：切换类
           有就删除，没有就添加

### jQuery文本值相关的方法（20.html）

1.html(val|fn)
            和原生JS中的innerHTML一模一样
            2.text([val|fn])
            和原生JS中的innerText一模一样
            3.val([val|fn|arr])

### jQuery操作CSS样式的方法（21.html）

1.逐个设置
2.链式设置
            注意点：链式操作如果大于3步，建议分开
3.批量设置    (推荐)
4.获取CSS样式值

### jQuery事件绑定（24.html）

jQuery中有两种绑定事件方式

            1.eventName(fn):
            编码效率略高/ 部分事件jQuery没有实现，所以不能添加

            2.on(eventName,fn):
            编码效率略低/ 所有js事件都可以添加

            注意点：均可以添加多个相同或者不同类型的事件，且不会覆盖

### jQuery事件自动触发（27.html）

trigger:如果你用trigger自动触发事件，会触发事件冒泡

triggerHandler：如果你用triggerHandler自动触发事件，不会触发事件冒泡

trigger:如果利用trigger自动触发事件，会触发默认行为

triggerHandler:如果你用triggerHandler自动触发事件，不会触发默认行为

注意：这里有一个特例：如果用trigger触发a标签的默认行为，将不会发生页面的跳转，除非在a标签里嵌套一个span标签，然后监听span标签的事件，此时trigger才会触发a标签的默认行为

### jQuery自定义事件（28.html）

想要自定义事件，必须满足两个条件

            1.事件必须是通过on绑定的
            2.事件必须通过trigger或triggerHandler来触发

### jQuery事件命名空间（29.html）

想要事件的命名空间有效，必须满足两个条件

            1.事件是通过on来绑定的
            2.通过trigger触发事件

### jQuery事件命名空间面试题（30.html）

利用trigger触发子元素带命名空间的事件，name父元素带相同命名空间的事件也会被触发，而父元素没有命名空间的事件不会被触发

利用trigger触发子元素不带命名空间的事件，那么子元素所有相同类型的事件和父元素所有相同类型的事件都会被触发

### jQuery事件委托（31.html）

1.什么是事件委托？

            请别人帮忙做事情，然后将做完的结果反馈给我们

 在jQuery中，如果通过核心函数找到的元素不止一个，那么添加事件的时候，jQuery会遍历所有找到的元素，给所有找到的元素添加事件

### jQuery移入移出事件（33.html）

mouseover/mouseout事件，子元素被移入移出也会触发父元素的事件

mouseenter/mouseleave事件，子元素被移入移出不会触发父元素的事件
推荐使用下面的两个方法：

```
$(".father").mouseenter(function(){
                console.log("father被移入了");
            });
            $(".father").mouseleave(function(){
                console.log("father被移出了");
            });
$(".father").hover(function(){
                console.log("father被移入了");
            },function(){
                console.log("father被移出了");                
            });
```
