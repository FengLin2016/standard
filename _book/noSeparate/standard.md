# 前端规范

### 项目文件夹命名规范

我主要针对文件夹命名或者css命名都是根据功能模块划分的。

1. css 文件夹： 主要放整体css文件
   - 针对功能模块进行命名文件及分布，如：公用common.css 新闻news.css 个人中心center.css
2. js文件夹：存放项目所用的js文件
   - 公用js写在外部文件进行引用如： common.js  其他可根据功能进行存放
3. images文件夹： 存放所用图片
   - 针对功能模块进行图片文件夹命名如：新闻news 个人中心center 公用直接放images根目录下
4. fonts文件夹： 存放字体图标或者独立字体
   - 尽量把页面小图标进行字体化（iconfont）,可以方便改变大小、颜色等
   - 如果需要特殊字体，可以用字蛛软件剔除网页不需要的字（针对一些特殊标题只能切图问题），减少字体文件大小

### css部分

主要针对css的class命名，以及css划分和格式等规范

1. 重置样式
   - 移动端

   ```css
   * { -webkit-tap-highlight-color: transparent; outline: 0; margin: 0; padding: 0; vertical-align: baseline; }
   body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin: 0; padding: 0; vertical-align: baseline; }
   img { border: 0 none; vertical-align: top; }
   i, em { font-style: normal; }
   ol, ul { list-style: none; }
   input, select, button, h1, h2, h3, h4, h5, h6 { font-size: 100%; font-family: inherit, Helvetica; }
   table { border-collapse: collapse; border-spacing: 0; }
   a { text-decoration: none; color: #666; }
   body { margin: 0 auto; min-width: 320px; max-width: 640px; height: 100%; font-size: 14px; font-family: -apple-system,Helvetica,sans-serif; line-height: 1.5; color: #666; -webkit-text-size-adjust: 100% !important; text-size-adjust: 100% !important; }
   input[type="text"], textarea { -webkit-appearance: none; -moz-appearance: none; appearance: none; }
   ```

   - pc端

    ```css
    html, body, div, h1, h2, h3, h4, h5, h6, p, dl, dt, dd, ol, ul, li, fieldset, form, label, input, legend, table, caption, tbody, tfoot, thead, tr, th, td, textarea, article, aside, audio, canvas, figure, footer, header, mark, menu, nav, section, time, video { margin: 0; padding: 0; }
    h1, h2, h3, h4, h5, h6 { font-size: 100%; font-weight: normal }
    article, aside, dialog, figure, footer, header, hgroup, nav, section, blockquote { display: block; }
    ul, ol { list-style: none; }
    img { border: 0 none; vertical-align: top; }
    blockquote, q { quotes: none; }
    blockquote:before, blockquote:after, q:before, q:after { content: none; }
    table { border-collapse: collapse; border-spacing: 0; }
    strong, em, i { font-style: normal; font-weight: normal; }
    ins { text-decoration: underline; }
    del { text-decoration: line-through; }
    mark { background: none; }
    input::-ms-clear { display: none !important; }
    body { font: 12px/1.5 \5FAE\8F6F\96C5\9ED1, \5B8B\4F53, "Hiragino Sans GB", STHeiti, "WenQuanYi Micro Hei", "Droid Sans Fallback", SimSun, sans-serif; background: #fff; }
    a { text-decoration: none; color: #333; }
    a:hover { text-decoration: underline; }
    ```

2. 多组合，少继承
   - 定义一些常用的原子类。如： 浮动、圆角、清除浮动、间距、字体大小、一切常见的独立样式
   - 为了模块之间样式更加灵活，少用继承。如： .naver .list .item a 

3. 针对classname命名规范(全英文小写)：

   - 命名必须按功能模块英文或者页面名称英文命名，不能采用拼音。如：toper(顶部)、header(头)、content(内容)、naver(导航)、title-catalog-00(栏目标题类)、tab-catalog-00(table切换类)、list-text-00(列表类)、btn-00(按钮类)、icon-name(图标类)、footer(尾)
   - 针对模块之间的链接符号必须采用“-”不能用“\_”, 因为’\_‘是js中运用的，我们需要做好区分

4. css书写顺序（这部分可以用工具自动化构成）。

   - 显示定位（display、position、float、list-style）—>元素自身（width、height、margin、padding、border、background）—>文本外观（color、font、line-height、text-align、text-decoration）—>特殊内容（css3）

5. 兼容要求。

   - pc端不采用flex布局，兼容要求IE9及以上，如果要用一些新属性也要做好过渡效果，不能影响正常显示和功能问题（如：圆角、阴影等）
   - wap站点可以采用一些新的属性 动画、弹性布局等

### html部分

主要针对结构清晰、语义化、seo等方面。

1. 一定记得对标签进行关闭如：

   ```html
   <div class="naver">关闭</div>
   <img src="" title="" alt="" />
   ```

2. html的嵌套问题：

   ```html
   1. 块元素可以包含内联元素或某些块元素，但内联元素却不能包含块元素，它只能包含其它的内联元素：
   <div><h1></h1><p></p></div> —— 对
   <a href=”#”><span></span></a> —— 对
   <span><div></div></span> —— 错
   
   2. 块级元素不能放在<p>里面：
   <p><ol><li></li></ol></p> —— 错
   <p><div></div></p> —— 错
   
   3. 有几个特殊的块级元素只能包含内嵌元素，不能再包含块级元素，这几个特殊的标签是：
   h1、h2、h3、h4、h5、h6、p、dt
   
   4. li 内可以包含 div 标签 —— 这一条其实不必单独列出来的，但是网上许多人对此有些疑惑，就在这里略加说明：
   li 和 div 标 签都是装载内容的容器，地位平等，没有级别之分（例如：h1、h2 这样森严的等级制度^_^）
   ，要知道，li 标签连它的父级 ul 或者是 ol 都 可以容纳的，为什么有人会觉得 li 偏偏容纳不下一个 div 呢？别把 li 看得那么小气嘛，别看 li 长得挺瘦小，其实 li 的胸襟很大。
   
   5. 块级元素与块级元素并列、内嵌元素与内嵌元素并列：
   <div><h2></h2><p></p></div> —— 对
   <div><a href=”#”></a><span></span></div> —— 对
   <div><h2></h2><span></span></div> —— 错
   ```

3. 语义化结构书写

   - 多用意义标签，少用无意义标签

   ```text
   意义标签：
   p、header、nav、section 、article、aside 、hgroup 、footer 、time 、address、em、b、h1~h6...
   无意义标签
   div、span
   ```
   - 尽量减少结构嵌套，太深的嵌套会加深dom结构、不利于页面渲染

   ```html
   一个列表：
   <ul>
   	<li>
   		<span class="time">2019-2-28</span>
   		<a href="#" title="标题">标题</a>
   	</li>
   </ul>
   ```
   - 如果页面本身是表格,就直接用table标签，不必局限于非要用div，之前不建议的也是采用table布局，不是table本身问题

4. SEO

   - img标签加入title、alt属性 

   - a标签加上herf，如果没有连接也要书写Javascript:void(0) ， target 书写标准是 跳转后的页面能跳转回来就不要_blank,否则加上 ，特殊要求除外;

   - H标签的使用，值得注意的是，不论任何页面，h1标签只能出现一次，它是当前页面的主标题，权重最高，对蜘蛛的吸引力是最强的。再往下就是h2、h3、h4、h5、h6这些副标题了，所强调的重点也是递减的，当然，它们的出现频率没有明确限制

### javascript部分

针对平台特殊性，统一一些规范函数命名、数据绑定、框架选择等方面

1. 框架，我们统一采用jquery，版本控制在1.8~1.11之间。

   ```html
   api文档：http://jquery.cuishifeng.cn
   文件下载：http://www.jq22.com/jquery-info122
   ```

2. 表单、数据绑定

   ```html
   1. form 表单尽量采用from表单提交，不建议使用ajax提交， 除非不需要发生跳转的情况 例子：
   	<form action="http://www.baidu.com" onsubmit="return toVaild()">
                 <input type="text" id="ff">
                 <input type="submit" id="submit" value ="提交"/>
       </form>
   
       <script language="javascript">
           function toVaild(){
               var val = document.getElementById("ff").value;
               alert(val);
               if(val == "可以提交"){
                   alert("校验成功，之后进行提交");
                   return true;
               }
               else{
                   alert("校验失败，不进行提交");
                   return false;
               }
           }
       </script>
   
   2. 采用统一的表单验证规则，我建议封装我们自己常用的一些验证规则
   有效数字验证、长度、中文、特殊字符等
   
   3. 数据绑定中，采用传统的jq方式。尽量不要采用vue的数据驱动方式, 不能js中混合php代码，后期难以维护
   避免重复绑定
   <script language="javascript">
   // 不推荐
   var comForm = {
       name:"{!! $agency->name ?? '' !!}",//公司名称
       province:"{!! $agency->pname->id ??  '' !!}",//公司省份
       city:"{!! $agency->cname->id ?? '' !!}",//公司城市
       address:"{!! $agency->address ?? '' !!}",//公司地址
       licenseuri:"{!! $agency->licenseuri ?? '' !!}"//公司营业执照
   };
   //推荐
   var comForm = {
       name: $("#name").val(),//公司名称
       province: $("#province").val(),//公司省份
       city: $("#city").val(),//公司城市
       address: $("#address").val(),//公司地址
       licenseuri: $("#licenseuri").val()//公司营业执照
   };    
   </script>
   ```

   

3. 书写规范（建议采用统一代码格式化插件）

   ```javascript
   1.在单行代码块中使用空格
   //不推荐
   function foo () {return true}
   if (foo) {bar = 0}
   //推荐
   function foo () { return true }
   if (foo) { bar = 0 }
   
   2.拖尾逗号
   在 ECMAScript5 里面，对象字面量中的拖尾逗号是合法的，但在 IE8（非 IE8 文档模式）下，当出现拖尾逗号，则会抛出错误。
   拖尾逗号的例子：
   var foo = {
     name: 'foo',
     age: '22',
   }
   
   3.当命名变量时，主流分为驼峰式命名（variableName）和下划线命名（variable_name）两大阵营。
   团队约定用驼峰式命名法（variableName）
   
   4.逗号空格
   逗号前后的空格可以提高代码的可读性，团队约定在逗号后面使用空格，逗号前面不加空格。
   //不推荐
   var foo = 1,bar = 2
   var foo = 1 , bar = 2
   var foo = 1 ,bar = 2
   //推荐
   var foo = 1, bar = 2
   
   5.构造函数、类名首字母大写
   //不推荐
   var fooItem = new foo()
   //推荐
   var fooItem = new Foo()
   
   6.链式调用
   链式调用如果放在同一行，往往会造成代码的可读性差，但有些时候，短的链式调用并不会影响美观。所以本规范约定一行最多只能有四个链式调用，超过就要求换行。
   
   7. 函数格式。合理利用空格
   //不推荐
   function func(x) {
     // ...
   }
   //推荐
   function func (x) {
     // ...
   }
   ```

### 图片部分

针对网页的图片划分、命名方式等规范

1. 根据图片用途命名如：img_banner_00.jpg 、img_nav_00.jpg、icon_nav_00.png、icon_list_00.png、temp_product_00.jpg (临时图片，上线后可以删除的)等
2. 利用工具实现雪碧图制作
3. 将常见的小图标做成字体图标



​	