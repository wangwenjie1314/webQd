#2014年最新前端开发面试题（转自markyun）
### PS：在其基础上完善了一些答案，增加一些问题 欢迎fork wj：）

## <a name='list'>目录</a>

  1. [前言](#user-content-preface)
  1. [HTML 部分](#user-content-html)
  1. [CSS  部分](#user-content-css)
  1. [JavaScript 部分](#user-content-js)
  1. [其他问题](#user-content-other) 
  1. [优质网站推荐](#user-content-web) 
 
 

## <a name='preface' id='preface'>前言</a> ##

本文总结了一些优质的前端面试题（多数源于网络），初学者阅后也要用心钻研其中的原理，重要知识需要系统学习，透彻学习，形成自己的知识链。万不可投机取巧，只求面试过关是错误的！


###面试有几点需注意：(来源程劭非老师 github:@wintercn)

1. 面试题目： 根据你的等级和职位变化，入门级到专家级：范围↑、深度↑、方向↑。

1. 题目类型： 技术视野、项目细节、理论知识题，算法题，开放性题，案例题。

1. 进行追问： 可以确保问到你开始不懂或面试官开始不懂为止，这样可以大大延展题目的区分度和深度，知道你的实际能力。因为这种关联知识是长时期的学习，绝对不是临时记得住的。

1. 回答问题再棒，面试官（可能是你的直接领导面试），会考虑我要不要这个人做我的同事？所以态度很重要。（感觉更像是相亲）

1. 资深的工程师能把absolute和relative弄混，这样的人不要也罢，因为团队需要的你这个人具有可以依靠的才能（靠谱）。



**前端开发面试知识点大纲：**

	HTML&CSS：
	对Web标准的理解、浏览器内核差异、兼容性、hack、CSS基本功：布局、盒子模型、
	选择器优先级及使用、HTML5、CSS3、移动端适应 
	
	JavaScript：  
	数据类型、面向对象、继承、闭包、插件、作用域、跨域、原型链、模块化、自定义事件、
	内存泄漏、事件机制、异步装载回调、模板引擎、Nodejs、JSON、ajax等。
	
	其他：
	HTTP、安全、正则、优化、重构、响应式、移动端、团队协作、可维护、SEO、UED、架构、职业生涯 

作为一名前端工程师，**无论工作年头长短都应该必须掌握的知识点**：

此条由 王子墨 发表在 [前端随笔](http://julying.com/blog/front-end-engineers-must-master-knowledge/) 
   
1、DOM结构——两个节点之间可能存在哪些关系以及如何在节点之间任意移动。

	document.documentElement     返回文档的根节点<html> 
	document.body     <body> 
	document.activeElement 返回当前文档中被击活的标签节点(ie) 
	event.fromElement        返回鼠标移出的源节点(ie) 
	event.toElement       返回鼠标移入的源节点(ie) 
	event.srcElement     返回激活事件的源节点(ie) 
	event.target         返回激活事件的源节点(firefox) 
	当前对象为node 
	返回父节点：node.parentNode, node.parendElement, 
	返回所有子节点：node.childNodes（包含文本节点及标签节点）,node.children 
	返回第一个子节点：node.firstChild 
	返回最后一个子节点： node.lastChild 
	返回同属上一个子节点：node.nextSibling 
	返回同属下一个子节点：node.previousSibling 
	parentNode和parentElement功能一样，childNodes和children功能一样。但是parentNode和
	childNodes是符合W3C标准的，可以说比较通用。而另外两个只是IE支持，不是标准，Firefox就不支持 
	,所以大家只要记得有parentElement和children就行了 

2、DOM操作——怎样添加、移除、移动、复制、创建和查找节点。

	（1）创建新节点
	    createDocumentFragment()    //创建一个DOM片段
	    createElement()   //创建一个具体的元素
	    createTextNode()   //创建一个文本节点
	（2）添加、移除、替换、插入
	    appendChild()
	    removeChild()
	    replaceChild()
	    insertBefore()
	（3）查找
	    getElementsByTagName()    //通过标签名称
	    getElementsByName()    //通过元素的Name属性的值
	    getElementById()    //通过元素Id，唯一性

3、事件——怎样使用事件以及IE和DOM事件模型之间存在哪些主要差别。

	（1）冒泡型事件：事件按照从最特定的事件目标到最不特定的事件目标(document对象)的顺序触发。
	IE 5.5: div -> body -> document
	IE 6.0: div -> body -> html -> document
	Mozilla 1.0: div -> body -> html -> document -> window
	（2）捕获型事件(event capturing)：事件从最不精确的对象(document 对象)开始触发，
	然后到最精确(也可以在窗口级别捕获事件，不过必须由开发人员特别指定)。
	（3）DOM事件流：同时支持两种事件模型：捕获型事件和冒泡型事件，
	但是，捕获型事件先发生。两种事件流会触及DOM中的所有对象，从document对象开始，也在document对象结束。
	DOM事件模型最独特的性质是，文本节点也触发事件(在IE中不会)。

4、XMLHttpRequest——这是什么、怎样完整地执行一次GET请求、怎样检测错误。

	XMLHttpRequest 对象提供了在网页加载后与服务器进行通信的方法。
	
	<script type="text/javascript">
	    varxmlhttp;
	    functionloadXMLDoc(url){
	        xmlhttp=null;
	        if(window.XMLHttpRequest){    //code for all new browsers
	            xmlhttp=newXMLHttpRequest();
	        }elseif(window.ActiveXObject){    //code for IE5 and IE6
	            xmlhttp=newActiveXObject("Microsoft.XMLHTTP");
	        }
	        if(xmlhttp!=null){
	            xmlhttp.onreadystatechange=state_Change;
	               xmlhttp.open("GET",url,true);
	            xmlhttp.send(null);
	        }else{
	            alert("Your browser does not support XMLHTTP.");
	        }
	}
	
	functionstate_Change(){
	    if(xmlhttp.readyState==4){    //4 = "loaded"
	        if(xmlhttp.status==200){    //200 = OK
	            //...our code here...
	        }else{
	            alert("Problem retrieving XML data");
	        }
	    }
	}
	</script>

5、严格模式与混杂模式——如何触发这两种模式，区分它们有何意义。

	在标准模式中，浏览器根据规范呈现页面；
	在混杂模式中，页面以一种比较宽松的向后兼容的方式显示。
	浏览器根据DOCTYPE是否存在以及使用的哪种DTD来选择要使用的呈现方法。
	如果XHTML文档包含形式完整的DOCTYPE，那么它一般以标准模式呈现。
	对于HTML 4.01文档，包含严格DTD的DOCTYPE常常导致页面以标准模式呈现。
	包含过渡DTD和URI的DOCTYPE也导致页面以标准模式呈现，但是有过
	渡DTD而没有URI会导致页面以混杂模式呈现。DOCTYPE不存在或形式不正确会导致HTML和XHTML文档以混杂模式呈现。

6、盒模型——外边距、内边距和边框之间的关系，IE 8以下版本的浏览器中的盒模型有什么不同。

	一个元素盒模型的层次从内到外分别为：内边距、边框和外边距
	IE8以下浏览器的盒模型中定义的元素的宽高不包括内边距和边框。（这句回答有争议，期待能有人解答原因QQ1662484899）
	
	延伸：
	盒子模型分为两类：W3C标准盒子模型和IE盒子模型 （微软确实不喜欢服从他家的标准）
        这两者的关键差别就在于：
	W3C盒子模型——属性高（height）和属性宽（width）这两个值不包含 填充（padding）和边框（border）
        IE盒子模型——属性高（height）和属性宽（width）这两个值包含 填充（padding）和边框（border）
        我们在编写页面代码的时候应该尽量使用标准的W3C盒子模型（需要在页面中声明DOCTYPE类型），
        这样可以避免多个浏览器对同一页面的不兼容。
	因为如果不声明DOCTYPE类型，IE会将盒子模型解释为IE盒子模型，FireFox等会将其解释为W3C盒子模型；
	而如果在页面中声明了DOCTYPE模型，所有的浏览器都会把盒子模型解释为W3C盒子模型。
	

7、块级元素与行内元素——怎么用CSS控制它们、它们怎样影响周围的元素以及你觉得应该如何定义它们的样式。

	块级元素，用CSS中的display:inline;属性则变为行内元素
	行内元素，用CSS中的display:block;属性则变为块级元素
	影响：周围元素显示在同一行或换行显示，根据具体情况调整样式

8、浮动元素——怎么使用它们、它们有什么问题以及怎么解决这些问题。

	需要浮动的元素可使用CSS中float属性来定义元素的浮动位置，left：往左浮动，right：往右浮动
	浮动元素引起的问题：
	（1）父元素的高度无法被撑开，影响与父元素同级的元素
	（2）与浮动元素同级的非浮动元素会跟随其后
	（3）若非第一个元素浮动，则该元素之前的元素也需要浮动，否则会影响页面显示的结构
	解决方法：
	使用CSS中的clear:both;属性来清除元素的浮动可解决2、3问题，
	对于问题1，添加如下样式，给父元素添加clearfix样式：
	.clearfix:after{content: ".";display: block;height: 0;clear: both;visibility: hidden;}
	.clearfix{display: inline-block;}  /* for IE/Mac */

9、HTML与XHTML——二者有什么区别，你觉得应该使用哪一个并说出理由。

	主要区别：
	XHTML 元素必须被正确地嵌套
	XHTML 元素必须被关闭，空标签也必须被关闭，如 <br> 必须写成 <br />
	XHTML 标签名必须用小写字母
	XHTML 文档必须拥有根元素
	XHTML 文档要求给所有属性赋一个值
	XHTML 要求所有的属性必须用引号""括起来
	XHTML 文档需要把所有 < 、>、& 等特殊符号用编码表示
	XHTML 文档不要在注释内容中使“--”
	XHTML 图片必须有说明文字
	XHTML 文档中用id属性代替name属性

10、JSON——它是什么、为什么应该使用它、到底该怎么使用它，说出实现细节来。

	JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。
	易于人阅读和编写。同时也易于机器解析和生成。
	JSON建构于两种结构：
	“名称/值”对的集合（A collection of name/value 
	pairs）。
	不同的语言中，它被理解为对象（object），纪录（record），结构（struct），
	字典（dictionary），哈希表
	（hash table），有键列表（keyed list），或者关联数组 （associative array）。 
	值的有序列表（An ordered list of values）。在大部分语言中，它被理解为数组（array）。
			

**备注：** 

根据自己需要选择性阅读，面试题是对理论知识的总结，让自己学会应该如何表达。

资料答案不够正确和全面，**欢迎补充**答案、题目；最好是现在网上没有的。 

格式不断修改更新中。  


## <a name='html'>HTML</a>

- Doctype作用? 严格模式与混杂模式如何区分？它们有何意义? 

		（1）、<!DOCTYPE> 声明位于文档中的最前面，处于 <html> 标签之前。告知浏览器的解析器，
		用什么文档类型 规范来解析这个文档。 
		
		（2）、严格模式的排版和 JS 运作模式是  以该浏览器支持的最高标准运行。
		
		（3）、在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。
		
		（4）、DOCTYPE不存在或格式不正确会导致文档以混杂模式呈现。

- 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

        （1）CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值，
          比如div默认display属性值为“block”，成为“块级”元素；
          span默认display属性值为“inline”，是“行内”元素。  
        
        （2）行内元素有：a b span img input select strong（强调的语气） 
         块级元素有：div ul ol li dl dt dd h1 h2 h3 h4…p  
                
        （3）知名的空元素： 
        <br> <hr> <img> <input> <link> <meta> 
        鲜为人知的是： 
        <area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>

- 请问css中的区块 inline inline-block block 三者有什么区别呢？

		这样先讲内联元素和块级元素：
		内联元素是不可以控制宽和高、margin等；并且在同一行显示，不换行。
		块级元素时可以控制宽和高、margin等，并且会换行。
		
		inline：使用此属性后，元素会被显示为内联元素，元素则不会换行。
		block：使用此属性后，元素会被现实为块级元素，元素会进行换行。
		inline-block：是使元素以块级元素的形式呈现在行内。
		意思就是说，让这个元素显示在同一行不换行，但是又可以控制高度和宽度，这相当于内联元素的增强。
		
		要注意的是IE6 不支持inline-block


- link 和@import 的区别是？

	
        （1）link属于XHTML标签，而@import是CSS提供的;
        
        （2）页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
        
        （3）import只在IE5以上才能识别，而link是XHTML标签，无兼容问题;
        
        （4）link方式的样式的权重 高于@import的权重.	

- 浏览器的内核分别是什么?
	
		* IE浏览器的内核Trident、Mozilla的Gecko、
		* Chrome的Blink（WebKit的分支）、Opera内核原为Presto，现为Blink；


- 常见兼容性问题？

		* png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.
		
		* 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。
		
		* IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。 
		
		浮动ie产生的双倍距离 #box{ float:left; width:10px; margin:0 0 0 100px;} 
		
		这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中
		加入 ——_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)
		
		渐进识别的方式，从总体中逐渐排除局部。 
		
		首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。 
		接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
		
		css
		.bb{
		background-color:#f1ee18;/*所有识别*/
		.background-color:#00deff\9; /*IE6、7、8识别*/
		+background-color:#a200ff;/*IE6、7识别*/
		_background-color:#1e0bd1;/*IE6识别*/ 
		} 
		
		*  IE下,可以使用获取常规属性的方法来获取自定义属性,
		也可以使用getAttribute()获取自定义属性;
		Firefox下,只能使用getAttribute()获取自定义属性. 
		解决方法:统一通过getAttribute()获取自定义属性.
		
		* IE下,even对象有x,y属性,但是没有pageX,pageY属性; 
		Firefox下,event对象有pageX,pageY属性,但是没有x,y属性.
		
		* 解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。
		
		* Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示, 
		可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决.
		
		超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:
		L-V-H-A :  a:link {} a:visited {} a:hover {} a:active {}



- html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 
HTML5？
	
	
		* HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
		
		* 绘画 canvas  
		用于媒介回放的 video 和 audio 元素 
		本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
		sessionStorage 的数据在浏览器关闭后自动删除
		
		语意化更好的内容元素，比如 article、footer、header、nav、section 
		表单控件，calendar、date、time、email、url、search  
		新的技术webworker, websockt, Geolocation
		
		* 移除的元素
		
		纯表现的元素：basefont，big，center，font, s，strike，tt，u；
		
		对可用性产生负面影响的元素：frame，frameset，noframes；
		
		支持HTML5新标签：
		
		* IE8/IE7/IE6支持通过document.createElement方法产生的标签，
		  可以利用这一特性让这些浏览器支持HTML5新标签，
		
		浏览器支持新标签后，还需要添加标签默认的样式：
		
		* 当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架
		   <!--[if lt IE 9]> 
		   <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script> 
		   <![endif]--> 
		如何区分： DOCTYPE声明\新增的结构元素\功能元素
	

- 语义化的理解？ 
	
		用正确的标签做正确的事情！
	    html语义化就是让页面的内容结构化，便于对浏览器、搜索引擎解析；
	    在没有样式CCS情况下也以一种文档格式显示，并且是容易阅读的。
	    搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，利于 SEO。
	    使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

- HTML5的离线储存？

	    localStorage    长期存储数据，浏览器关闭后数据不丢失；
        sessionStorage  数据在浏览器关闭后自动删除。

- (写)描述一段语义的html代码吧。

		（HTML5中新增加的很多标签（如：<article>、<nav>、<header>和<footer>等）
		就是基于语义化设计原则）  
		< div id="header"> 
		< h1>标题< /h1> 
		< h2>专注Web前端技术< /h2> 
		< /div>


- iframe有那些缺点？ 

		*iframe会阻塞主页面的Onload事件；

		*iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
        使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript
        动态给iframe添加src属性值，这样可以可以绕开以上两个问题。

- 请描述一下 cookies，sessionStorage 和 localStorage 的区别？ 

 		cookie在浏览器和服务器间来回传递。 sessionStorage和localStorage不会
		sessionStorage和localStorage的存储空间更大；
		sessionStorage和localStorage有更多丰富易用的接口；
		sessionStorage和localStorage各自独立的存储空间；
		



## <a name='css'>CSS</a> 

- 介绍一下CSS的盒子模型？

		（1）有两种， IE 盒子模型、标准 W3C 盒子模型；IE的content部分包含了 border 和 pading;

		（2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border).



- CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3新增伪类有那些？

		*   1.id选择器（ # myid）
			2.类选择器（.myclassname）
			3.标签选择器（div, h1, p）
			4.相邻选择器（h1 + p）
			5.子选择器（ul < li）
			6.后代选择器（li a）
			7.通配符选择器（ * ）
			8.属性选择器（a[rel = "external"]）
			9.伪类选择器（a: hover, li: nth - child）
		  
		*   可继承的样式： font-size font-family color, UL LI DL DD DT;

		*   不可继承的样式：border padding margin width height ;
		  
		*   优先级就近原则，同权重情况下样式定义最近者为准;

		*   载入样式以最后载入的定位为准;

	优先级为:
		  
		   !important >  id > class > tag  
		  
		   important 比 内联优先级高

	CSS3新增伪类举例：

		p:first-of-type	选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
		p:last-of-type	选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
        p:only-of-type	选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
		p:only-child	选择属于其父元素的唯一子元素的每个 <p> 元素。
		p:nth-child(2)	选择属于其父元素的第二个子元素的每个 <p> 元素。
 	    :enabled  :disabled 控制表单控件的禁用状态。
		:checked        单选框或复选框被选中。


- 如何居中div？如何居中一个浮动元素？


	*  给div设置一个宽度，然后添加margin:0 auto属性
		 
			div{
				width:200px;
				margin:0 auto;
			 }  

			 
	*  居中一个浮动元素
  
			  确定容器的宽高 宽500 高 300 的层
			  设置层的外边距
			 
		     .div { 
			  Width:500px ; height:300px;//高度可以不设
			  Margin: -150px 0 0 -250px;
			  position:relative;相对定位
              background-color:pink;//方便看效果
			  left:50%;
			  top:50%;
			} 


- 列出display的值，说明他们的作用。position的值， relative和absolute定位原点是？
 
	
	      1.   
	      block 象块类型元素一样显示。
		  none 缺省值。象行内元素类型一样显示。
		  inline-block 象行内元素一样显示，但其内容象块类型元素一样显示。
		  list-item 象块类型元素一样显示，并添加样式列表标记。
	  
	      2. 
		  *absolute	
				生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。 
	
		  *fixed （老IE不支持）
				生成绝对定位的元素，相对于浏览器窗口进行定位。 
	
		  *relative	
				生成相对定位的元素，相对于其正常位置进行定位。 
	
		  * static	默认值。没有定位，元素出现在正常的流中
		  *（忽略 top, bottom, left, right z-index 声明）。
	
		  * inherit	规定从父元素继承 position 属性的值。
	  
- CSS3有哪些新特性？

  		  CSS3实现圆角（border-radius:8px），阴影（box-shadow:10px），
		  对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）
          transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);//旋转,缩放,定位,倾斜
          增加了更多的CSS选择器  多背景 rgba 

- 一个满屏 品 字布局 如何设计?

- 经常遇到的CSS的兼容性有哪些？原因，解决方法是什么？



- 为什么要初始化CSS样式。

		- 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。
	
		- 当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。

		*最简单的初始化方法就是： * {padding: 0; margin: 0;} （不建议）
	
		淘宝的样式初始化： 
		body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, 
		dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; }
		body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; }
		h1, h2, h3, h4, h5, h6{ font-size:100%; }
		address, cite, dfn, em, var { font-style:normal; }
		code, kbd, pre, samp { font-family:couriernew, courier, monospace; }
		small{ font-size:12px; }
		ul, ol { list-style:none; }
		a { text-decoration:none; }
		a:hover { text-decoration:underline; }
		sup { vertical-align:text-top; }
		sub{ vertical-align:text-bottom; }
		legend { color:#000; }
		fieldset, img { border:0; }
		button, input, select, textarea { font-size:100%; }
		table { border-collapse:collapse; border-spacing:0; } 



- absolute的containing block计算方式跟正常流有什么不同？

- position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？

- 对BFC规范的理解？

		（W3C CSS 2.1 规范中的一个概念,它决定了元素如何对其内容进行定位,以及与其他元素的关 系和相互作用。）
- css定义的权重

		以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值：
	 
		/*权重为1*/
		div{
		}
		/*权重为10*/
		.class1{
		}
		/*权重为100*/
		#id1{
		}
		/*权重为100+1=101*/
		#id1 div{
		}
		/*权重为10+1=11*/
		.class1 div{
		}
		/*权重为10+10+1=21*/
		.class1 .class2 div{
		} 
		
		如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现


- 解释下浮动和它的工作原理？清除浮动的技巧

- 用过媒体查询，针对移动端的布局吗？

- 使用 CSS 预处理器吗？喜欢那个？
		
		SASS 

 


## <a name='js'>JavaScript</a>

-  JavaScript原型，原型链 ? 有什么特点？

	```javascript
	什么是原型：
	每一个对象都有原型，使用 __proto__ 标记，原型是一个对象的引用或 null
	（ Object.prototype 的原型为 null ），允许对象使用其原型所引用的对象中的变量。
	var fun = function(){}
	fun.prototype.a = 1;
	var obj = new fun();
	obj.a; //1
	原型的来源：
	对象的原型来自其构造函数的原型属性（用 prototype 标记）的引用。注意原型与原型属性是两个概念。
	  Function 为实例（ function ）定义了原型属性，其中包含一个构造函数（默认是 function 对象自己，用于构造 function 自己的实例），因此所有 function 都有原型属性。
	Function 将自己的的原型属性的引用作为function 的原型。 new 一个 function ，function 的实例便有了原型，指向 function 的原型属性。
	
	var fun = function(){
	  this.a= 1;
	}
	fun.prototype.b = 2;
	var obj = new fun();
	console.log(obj.a+"---"+obj.b);
	原型的作用
	继承。
	  如：
	var fun = function(){}
	fun.prototype = String.prototype;
	new fun().split //function split() {[native code]}
	原型链：
	通过自己的原型并向上寻找直到Object.prototype.__proto__; 这条链就是原型链。
	```

- 看看下面运行结果？

	```javascript
	window.onload=function(){
	  var a=1+"1";
	  var b="1"+1;
	  var c="abc"+12+5+"def";
	  var d="abc"+(12+5)+"def";
	  console.log(a);
	  console.log(b);
	  console.log(c);
	  console.log(d);
	}
	
	//结果
	11
	11
	abc125def
	abc17def
	```

-  eval是做什么的？ 

		它的功能是把对应的字符串解析成JS代码并运行；
		应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。

-  null，undefined 的区别？
		前者的意思是javascript解释器不知道这是什麽东西,会抛出"未定义"的错误
		後者的意思是你定义了它,但它没有分配内存空间,无心肝不痛,不会抛出错误.

-  写一个通用的事件侦听器函数。

	```javascript
	// event(事件)工具集，来源：github.com/markyun
	markyun.Event = {
		// 页面加载完成后
		readyEvent : function(fn) {
			if (fn==null) {
				fn=document;
			}
			var oldonload = window.onload;
			if (typeof window.onload != 'function') {
				window.onload = fn;
			} else {
				window.onload = function() {
					oldonload();
					fn();
				};
			}
		},
		// 视能力分别使用dom0||dom2||IE方式 来绑定事件
		// 参数： 操作的元素,事件名称 ,事件处理程序
		addEvent : function(element, type, handler) {
			if (element.addEventListener) {
				//事件类型、需要执行的函数、是否捕捉
				element.addEventListener(type, handler, false);
			} else if (element.attachEvent) {
				element.attachEvent('on' + type, function() {
					handler.call(element);
				});
			} else {
				element['on' + type] = handler;
			}
		},
		// 移除事件
		removeEvent : function(element, type, handler) {
			if (element.removeEnentListener) {
				element.removeEnentListener(type, handler, false);
			} else if (element.datachEvent) {
				element.detachEvent('on' + type, handler);
			} else {
				element['on' + type] = null;
			}
		}, 
		// 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)
		stopPropagation : function(ev) {
			if (ev.stopPropagation) {
				ev.stopPropagation();
			} else {
				ev.cancelBubble = true;
			}
		},
		// 取消事件的默认行为
		preventDefault : function(event) {
			if (event.preventDefault) {
				event.preventDefault();
			} else {
				event.returnValue = false;
			}
		},
		// 获取事件目标
		getTarget : function(event) {
			return event.target || event.srcElement;
		},
		// 获取event对象的引用，取到事件的所有信息，确保随时能使用event；
		getEvent : function(e) {
			var ev = e || window.event;
			if (!ev) {
				var c = this.getEvent.caller;
				while (c) {
					ev = c.arguments[0];
					if (ev && Event == ev.constructor) {
						break;
					}
					c = c.caller;
				}
			}
			return ev;
		}
	}; 
	```


-  Node.js的适用场景？

		高并发、聊天、实时消息推送

-  介绍js的基本数据类型。

		number,string,boolean,object,undefined
	
-  Javascript如何实现继承？

		通过原型和构造器
		我觉得是类继续与原型链继承
		
		原型链：每个函数都有自己的原型（prototype）属性，这个属性其实是隐藏对象，通过对这个对象的操作，
		子类可以同样持有这个对象的引用，间隔实现继承，这个的好处是大大节省了空间，
		因为下面的子类不用重新去实例化父类定义的属性和方法，而直接引用原型链上的属性与方法，
		也就是说父类的原型链上定义了一个方法，当子类无论实例化多少次时，并没有实例化原型链上内容，
		而是共同享有同一个属性与方法。JavaScript原型继承（对象间的继承）
		
		类继承：在函数内部定义自身的属性的方法，子类继续时，用call或apply实现对象冒充，
		把类型定义的东西都复制过来，这样的继承子类与父类并没有多少关联，不互相影响，
		有利于保护自身的一些私有属性。JavaScript类继承（构造函数间的继承）
		
		
		不过在实际中，肯定是这两种混合使用的
	
-  ["1", "2", "3"].map(parseInt) 答案是多少？

		 [1, NaN, NaN] 因为 parseInt 需要两个参数 (val, radix) 但 map 传了 3 个 (element, index, array)

-  如何创建一个对象? （画出此对象的内存图）

	  ```javascript
	  function Person(name, age) {
	    this.name = name;
	    this.age = age;
	    this.sing = function() { alert(this.name) } 
	  } 
	  ```


-  谈谈This对象的理解。

		this是js的一个关键字，随着函数使用场合不同，this的值会发生变化。
		
		但是有一个总原则，那就是this指的是调用函数的那个对象。
		
		this一般情况下：是全局对象Global。 作为方法调用，那么this就是指这个对象	

-  事件是？IE与火狐的事件机制有什么区别？ 如何阻止冒泡？ 

		 1. 我们在网页中的某个操作（有的操作对应多个事件）。
		 例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为。  
		 2. 事件处理机制：IE是事件冒泡、火狐是 事件捕获；
		 3. ev.stopPropagation();

-  什么是闭包（closure），为什么要用它？

```javascript
	/**就是一个函数里面又套有子函数，在这个函数里面声明的变量可以直接在子函数里面使用而不用再声明
	执行say667()后,say667()闭包内部变量会存在,而闭包内部函数的内部变量不会存在.
	使得Javascript的垃圾回收机制GC不会收回say667()所占用的资源，
	因为say667()的内部函数的执行需要依赖say667()中的变量。这是对闭包作用的非常直白的描述.**/
	  
	function say667() {
		// Local variable that ends up within closure
		var num = 666;
		var sayAlert = function() { alert(num); }
		num++;
		return sayAlert;
	}
	 
	var sayAlert = say667();
	sayAlert()//执行结果应该弹出的667  
```

-  "use strict";是什么意思 ? 使用它的好处和坏处分别是什么？

-  如何判断一个对象是否属于某个类？

		使用instanceof （待完善）
		
		if(a instanceof Person){
		   alert('yes');
		}
-  new操作符具体干了什么呢?

		1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
		2、属性和方法被加入到 this 引用的对象中。
		3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。
		
		var obj  = {};
		obj.__proto__ = Base.prototype;
		Base.call(obj); 

-  Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？
  
		hasOwnProperty

-  JSON 的了解？
		
		JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。
		它是基于JavaScript的一个子集。数据格式简单, 易于读写, 占用带宽小
        {'age':'12', 'name':'back'}

-  js延迟加载的方式有哪些？
		
		defer和async、动态创建DOM方式（用得最多）、按需异步载入js

		
-  ajax 是什么? 

		Ajax允许JavaScript可以发送HTTP请求和响应HTTP响应，依赖来浏览器的实现。
		交互模式： 建立XHR对象， 定义回调处理函数，发送HTTP请求（Get 和 Post 方式），完成HTTP响应后执行回调函数。
-  GET POST 区别

		1. get是从服务器上获取数据，post是向服务器传送数据。
		2. get是把参数数据队列加到提交表单的ACTION属性所指的URL中，
		值和表单内各个字段一一对应，在URL中可以看到。post是通过HTTP post机制，将表单内各个字段与其内容放置在HTML HEADER内一起传送到ACTION属性所指的URL地址。用户看不到这个过程。
		3. 对于get方式，服务器端用Request.QueryString获取变量的值，
		对于post方式，服务器端用Request.Form获取提交的数据。
		4. get传送的数据量较小，不能大于2KB。post传送的数据量较大，一般被默认为不受限制。
		但理论上，IIS4中最大量为80KB，IIS5中为100KB。
		5. get安全性非常低，post安全性较高。但是执行效率却比Post方法好。 
		
		建议：
		1、get方式的安全性较Post方式要差些，包含机密信息的话，建议用Post数据提交方式；
		2、在做数据查询时，建议用Get方式；而在做数据添加、修改或删除时，建议用Post方式；

-  同步和异步的区别?

		同步需要等待返回结果才能继续，异步不必等待，一般需要监听异步的结果
		同步是在一条直线上的队列，异步不在一个队列上 各走各的
		
-  如何解决跨域问题?
	 
		jsonp、 iframe、window.name、window.postMessage、服务器上设置代理页面
		(1) iframe  (2) 动态创建script标签 （3）JSONP （4）crox

-  模块化怎么做？

	```javascript
	[ 立即执行函数](http://benalman.com/news/2010/11/immediately-invoked-function-expression/),不暴露私有成员
	
	var module1 = (function(){
	　　　　var _count = 0;
	　　　　var m1 = function(){
	　　　　　　//...
	　　　　};
	　　　　var m2 = function(){
	　　　　　　//...
	　　　　};
	　　　　return {
	　　　　　　m1 : m1,
	　　　　　　m2 : m2
	　　　　};
	　　})(); 
	```
-  AMD（Modules/Asynchronous-Definition）、CMD（Common Module Definition）规范区别？
	```javascript
	//AMD 依赖前置，提前执行依赖；
	//api一个当多个用
	//全局require和局部require都叫require
	
	require(['/a','/b'],function(a,b){
		a.dosomething();
		b.dosomething();
	});

	//CMD 依赖就近，延迟执行依赖（as lazy as possiable）；
	//api严格区分，职责单一
	//没有全局require，根据模块化系统的完备性 提供seajs.use 来实现模块化的启动

	define(function(require,exports,modules){
		var a=require('/a');
		a.dosomething();
		var b=require('/b');
		b.dosomething();
	});
	```

-  异步加载的方式有哪些？

			
	      (1) defer，只支持IE
	      
	      (2) async：
	      
	      (3) 创建script，插入到DOM中，加载完毕后callBack
	  
- documen.write和 innerHTML的区别
			  
		document.write只能重绘整个页面
		
		innerHTML可以重绘页面的一部分
		  

-  .call() 和 .apply() 的区别？

	```javascript
	//call: 调用一个对象的一个方法，以另一个对象替换当前对象
	//apply: 应用某一对象的一个方法，用另一个对象替换当前对象 
	function add(a,b){
		return a+b;
	}
	function sub(a,b){
		return a-b;
	}
	alert(add.call(sub,3,1));//add替换sub 
	//call函数和apply方法的第一个参数都是要传入给当前对象的对象，及函数内部的this。后面的参数都是传递给当前对象的参数。
	var func=new function(){this.a="func"}
    var myfunc=function(x){
        var a="myfunc";
        alert(this.a);
        alert(x);
    }
    myfunc.call(func,"var");
    /*对于apply和call两者在作用上是相同的，但两者在参数上有区别的。
	对于第一个参数意义都一样，但对第二个参数：
	apply传入的是一个参数数组，也就是将多个参数组合成为一个数组传入，而call则作为call的参数传入（从第二个参数开始）。
	如 func.call(func1,var1,var2,var3)对应的apply写法为：func.apply(func1,[var1,var2,var3])
	同时使用apply的好处是可以直接将当前函数的arguments对象作为apply的第二个参数传入*/
	```

-  Jquery与jQuery UI 有啥区别？ 

			
		*jQuery是一个js库，主要提供的功能是选择器，属性修改和事件绑定等等。

		*jQuery UI则是在jQuery的基础上，利用jQuery的扩展性，设计的插件。
         提供了一些常用的界面元素，诸如对话框、拖动行为、改变大小行为等等


-  JQuery的源码看过吗？能不能简单说一下它的实现原理？

-  jquery 中如何将数组转化为json字符串，然后再转化回来？

			
jQuery中没有提供这个功能，所以你需要先编写两个jQuery的扩展：
 
```javascript
	$.fn.stringifyArray = function(array) {
	    return JSON.stringify(array)
	}

	$.fn.parseArray = function(array) {
	    return JSON.parse(array)
	} 
	//然后调用：
	$("").stringifyArray(array)
```

-  针对 jQuery 的优化方法？

		*基于Class的选择性的性能相对于Id选择器开销很大，因为需遍历所有DOM元素。

		*频繁操作的DOM，先缓存起来再操作。用Jquery的链式调用更好。   
         比如：var str=$("a").attr("href");

		*for (var i = size; i < arr.length; i++) {}
         for 循环每一次循环都查找了数组 (arr) 的.length 属性，在开始循环的时候设置一个变量来存储这个数字，可以让循环跑得更快： 
         for (var i = size, length = arr.length; i < length; i++) {}


-  JavaScript中的作用域与变量声明提升？ 

-  如何编写高性能的Javascript？

-  那些操作会造成内存泄漏？


			 
	    内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。
	    
      垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量。
      如果一个对象的引用数量为 0（没有其他对象引用过该对象），
      或对该对象的惟一引用是循环的，那么该对象的内存即可回收。

        setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。
		闭包、控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）

-  JQuery一个对象可以同时绑定多个事件，这是如何实现的？
  

## <a name='other'>其他问题</a>


- 你遇到过比较难的技术问题是？你是如何解决的？

- 常使用的库有哪些？常用的前端开发工具？开发过什么应用或组件？

- 页面重构怎么操作？

- 列举IE 与其他浏览器不一样的特性？

- 99%的网站都需要被重构是那本书上写的？

- 什么叫优雅降级和渐进增强？

- WEB应用从服务器主动推送Data到客户端有那些方式？

- 对Node的优点和缺点提出了自己的看法？

		
		*（优点）因为Node是基于事件驱动和无阻塞的，所以非常适合处理并发请求，
          因此构建在Node上的代理服务器相比其他技术实现（如Ruby）的服务器表现要好得多。
		  此外，与Node代理服务器交互的客户端代码是由javascript语言编写的，
	      因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情。

		*（缺点）Node是一个相对新的开源项目，所以不太稳定，它总是一直在变，
          而且缺少足够多的第三方库支持。看起来，就像是Ruby/Rails当年的样子。


- 你有哪些性能优化的方法？


		 （看雅虎14条性能优化原则）。
	
		  （1） 减少http请求次数：CSS Sprites, JS、CSS源码压缩、图片大小控制合适；网页Gzip，CDN托管，data缓存 ，图片服务器。
		
		  （2） 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数
		
		  （3） 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。
		
		  （4） 当需要设置的样式很多时设置className而不是直接操作style。
		
		  （5） 少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。
		
		  （6） 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。
		
		  （7） 图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。
		
		  （8） 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢。

- http状态码有那些？分别代表是什么意思？

			100-199 用于指定客户端应相应的某些动作。 
			200-299 用于表示请求成功。 
			300-399 用于已经移动的文件并且常被包含在定位头信息中指定新的地址信息。 
			400-499 用于指出客户端的错误。
			400	1、语义有误，当前请求无法被服务器理解。
			401	当前请求需要用户验证 
			403	服务器已经理解请求，但是拒绝执行它。
			500-599 用于支持服务器错误。 503 – 服务不可用
			
			HTTP协议的状态消息都有哪些?
			“200〃 : OK（成功） 一切正常
			“302〃 : Found（临时移动）类似于301，但新的URL应该被视为临时性的替代，而不是永久性的。
			“400〃 : Bad Request（错误请求）请求出现语法错误。
			“404〃 : Not Found（未找到）无法找到指定位置的资源。 
			“500〃 : Internal Server Error（服务器内部错误）服务器遇到错误，无法完成请求。
			“502〃 : Bad Gateway（错误网关）服务器作为网关或者代理时，
			为了完成请求访问下一个服务器，但该服务器返回了非法的应答。

- 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？（流程说的越详细越好）


			查找浏览器缓存 
		    DNS解析、查找该域名对应的IP地址、重定向（301）、发出第二个GET请求
		    进行HTTP协议会话
		    客户端发送报头(请求报头)
		    服务器回馈报头(响应报头)
		    html文档开始下载
		    文档树建立，根据标记请求所需指定MIME类型的文件
		    文件显示
			[
			浏览器这边做的工作大致分为以下几步：
			
			加载：根据请求的URL进行域名解析，向服务器发起请求，接收文件（HTML、JS、CSS、图象等）。
			
			解析：对加载到的资源（HTML、JS、CSS等）进行语法解析，
			建议相应的内部数据结构（比如HTML的DOM树，JS的（对象）属性表，CSS的样式规则等等）
			}
- 除了前端以外还了解什么其它技术么？你最最厉害的技能是什么？

- 你常用的开发工具是什么，为什么？

- 对前端界面工程师这个职位是怎么样理解的？它的前景会怎么样？

		     前端是最贴近用户的程序员，比后端、数据库、产品经理、运营、安全都近。
			1、实现界面交互
			2、提升用户体验
			3、有了Node.js，前端可以实现服务端的一些事情
			

		前端是最贴近用户的程序员，前端的能力就是能让产品从 90分进化到 100 分，甚至更好，
        
         参与项目，快速高质量完成实现效果图，精确到1px；
        
         与团队成员，UI设计，产品经理的沟通；
        
         做好的页面结构，页面重构和用户体验；
        
         处理hack，兼容、写出优美的代码格式；
        
         针对服务器的优化、拥抱最新前端技术。
- 加班的看法？


   		加班就像借钱，原则应当是------救急不救穷
	


- 平时如何管理你的项目？

		先期团队必须确定好全局样式（globe.css），编码模式(utf-8) 等
		
		编写习惯必须一致（例如都是采用继承式的写法，单样式都写成一行）；
		
		标注样式编写人，各模块都及时标注（标注关键样式调用的地方）；
		
		页面进行标注（例如 页面 模块 开始和结束）；
		
		CSS跟HTML 分文件夹并行存放，命名都得统一（例如style.css）
		
		JS 分文件夹存放 命民以该JS 功能为准英文翻译；
		
		图片采用整合的 images.png png8 格式文件使用 尽量整合在一起使用方便将来的管理
		
- 如何设计突发大规模并发架构？


- 说说最近最流行的一些东西吧？常去哪些网站？


		Node.js、Mongodb、npm、MVVM、MEAN、three.js

- 移动端（Android IOS）怎么做好用户体验?

		清晰的视觉纵线、信息的分组、极致的减法、
		利用选择代替输入、标签及文字的排布方式、
		依靠明文确认密码、合理的键盘利用、

- 你在现在的团队处于什么样的角色，起到了什么明显的作用？

- 你认为怎样才是全端工程师（Full Stack developer）？ 


- 介绍一个你最得意的作品吧？

- 你的优点是什么？缺点是什么？

- 如何管理前端团队?


- 最近在学什么？能谈谈你未来3，5年给自己的规划吗？

- 想问公司的问题？
		
			问公司问题：
			目前关注哪些最新的Web前端技术（未来的发展方向）？
			前端团队如何工作的（实现一个产品的流程）？
			公司的薪资结构是什么样子的？


## <a name='web'>优质网站推荐</a>

1. 极客标签：		 http://www.gbtags.com/

2. 码农周刊：		 http://weekly.manong.io/issues/

3. 前端周刊：		 http://www.feweekly.com/issues

4. 极客头条： 	 http://geek.csdn.net/

5. Startup News：http://news.dbanotes.net/

6. Hacker News： https://news.ycombinator.com/news  

7. InfoQ：  		 http://www.infoq.com/ 

8. w3cplus：     http://www.w3cplus.com/

9. Stack Overflow： http://stackoverflow.com/ 

10. Atp：  		 http://atp-posts.b0.upaiyun.com/posts/ 



了解更多：http://note.youdao.com/share/?id=f179a18d162ce08afa020a8ba8fc0cdf&type=note

—————————————————————————————————————————
##额外推荐：
* 事先声明：

		◆ 这些题目的来源：面试曾经被问过;工作被别人问过或者遇见过;网上看见过...
		◆ 答案真心不给提供，真的是许多问题都需要个人的理解和沉淀，
		所以还请各位自己动手...前端可以试试自己差不多能回答多少题，哈哈。
		◆ 其实很多题我也没有好答案，面试的时候如果遇到牛人我也可以顺便交流交流，
		反正我也只是一面，不丢人也不怕丢人。
		◆ 如果朋友们有好的面试题欢迎提建议，我会其实补充更新的，先谢谢各位了。

* HTML相关

		1. <!DOCTYPE>标签的定义与用法。
		2. 块级元素和行内元素都有哪些?
		3. 你真的了解HTML吗? 雅虎面试题　　把前面黄底那段拿去搜索下就知道了(曾在某浪公司面试的时候被问到过，确实是很好的问题)。
		CSS相关
		1. 介绍所知道的CSS hack技巧(如：_， *， +， \9， !important 之类)。
		2. 介绍CSS盒模型。
		3. CSS层叠是什么?介绍一下。
		4. 都知道哪些CSS浏览器兼容性问题。
		5. 有时会被问到些刁钻点的题，比如position值都有哪些，CSS3都有哪些新内容...
		JavaScript基础相关
		1. HTTP协议的状态消息都有哪些?(如200、302对应的描述)
		2. AJAX是什么? AJAX的交互模型(流程)? AJAX跨域的解决办法?
		3. 同步和异步的区别?
		4. 简述JavaScript封装。
		5. JavaScript继承有哪两种形式形式，进行描述。
		6. 什么是闭包?以下代码点击<p> 会输出什么?为什么?能大概说明白的话继续问能想出几种解决办法。
		<!DOCTYPE HTML> 
		<html> 
		<head> 
		<meta charset="utf-8" /> 
		<title>闭包演示</title> 
		<style type="text/css"> 
		    p {background:gold;}  
		</style> 
		<script type="text/javascript">   
		function init() {      
		    var pAry = document.getElementsByTagName("p");      
		    for( var i=0; i<pAry.length; i++ ) {      
		         pAry[i].onclick = function() {      
		         alert(i);      
		    }   
		  }  
		}  
		</script>   
		</head>   
		<body onload="init();">   
		<p>产品 0</p>   
		<p>产品 1</p>   
		<p>产品 2</p>   
		<p>产品 3</p>   
		<p>产品 4</p>   
		</body>   
		</html>  
		7. 在JS中this关键字的使用场合和用法(如在构造函数中、setTimeout中等)。
		8. 简述下cookie的操作，还有cookie的属性都知道哪些。
		9. IE与FF的JS兼容性都知道哪些。
		10. DOM操作 - 怎样添加、移除、移动、复制、创建和查找节点(这个问题真心是基础题，一般不会问)。
		jQuery相关
		1. jQuery源码是否尝试去读过?说说基本的架构或者 jQuery.fn.init 中都做了哪些判断。
		2. 都知道哪些不好的jQuery书写方式。
		3. Sizzle是否有读过?
		其它相关的加分项：
		1. 都使用和了解过哪些编辑器?都使用和了解过哪些日常工具?
		2. 都知道有哪些浏览器内核?开发过的项目都兼容哪些浏览器?
		3. 国内外的JS牛人都知道哪些?
		4. 瀑布流布局或者流式布局是否有了解
		4. 正则表达式有系统学习过吗(看书或网上教程)?有的话就问问简单点的邮箱验证、URL验证， 或者问问 贪婪匹配与懒惰匹配 的理论知识。
		5. Node.js是否有过尝试?到什么程度?说说个人理解的看法?
		6. HTML5都有哪些新的JS API?
		7. 前端优化知识都知道哪些?
		8. 基础算法题(如快速排序，能否一两句说说重要的核心原理或者数组消重等)。
		9. 是否有接触过或者了解过重构。
		原文：http://www.cnblogs.com/Darren_code/archive/2012/01/31/questions.html

* 【编辑推荐】

[什么是Node.js？](http://developer.51cto.com/art/201109/288849.htm)

[前端必读：浏览器内部工作原理](http://developer.51cto.com/art/201202/314376.htm)

[HTML 5 APIs程序员指南](http://developer.51cto.com/art/201202/314376.htm)

[10个在线正则表达式测试网站推荐](http://developer.51cto.com/art/201103/251633.htm)

[从新浪微博的改版谈网页重构](http://developer.51cto.com/art/201109/290414.htm)

### add by wwj 2014-7-30 16:08:38
