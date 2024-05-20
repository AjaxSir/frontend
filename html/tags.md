# HTML

### html5 新特性

#### 新增语义化标签

```html
<section></section> 表示页面中的一个内容区块,比如章节、页眉、页脚或页面的其他部分。可以和h1、 h2……等元素结合起来使用，表示文档结构。
<article></article> 表示页面中一块与上下文不相关的独立内容。比如一篇文章。
<aside></aside> 表示article元素内容之外的、与article元素内容相关的辅助信息。
<header></header> 表示页面中一个内容区块或真个页面的标题。
<hgroup></hgroup> 表示对整个页面或页面中的一个内容区块的标题进行组合。
<footer></footer> 表示整个页面或页面中一个内容区块的脚注。一般来说，他会包含创作者的姓名、创作日期以及创作者的联系信息。
<nav></nav> 表示页面中导航链接的部分。
```

#### 多媒体元素

```html
<audio>	定义音频内容
<video>	定义视频内容
<source>定义多媒体资源（audio或vedio）
<embed>	定义嵌入的内容，比如插件
<track>	为如video和 audio元素之类的媒介规定外部文本轨道
```



#### 图形绘制元素

```html
<canvas></canvas> 标签定义图形，比如图表和其他图像。该标签基于 JavaScript 的绘图 API
```

### 标签详解

#### meta

```html
<!--[页面关键词]，每个网页应具有描述该网页内容的一组唯一的关键字。-->
<meta name="keywords" content="your tags" />

<!-- [页面描述]，每个网页都应有一个不超过 150 个字符且能准确反映网页内容的描述标签。 -->
<meta name="description" content="150 words" />

<!-- viewport：能优化移动浏览器的显示 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0,maximum-scale=1.0, user-scalable=no"/>
<!-- initial-scale：初始的缩放比例  -->
<!-- maximum-scale：允许用户缩放到的最大比例  -->
<!-- user-scalable：用户是否可以手动缩 (no,yes) -->
```

#### input

```html
属性：
	1.accept: 当input的type值为file时生效 
					常用取值: 
						1. 上传.xls格式 <input text="file"  accept="application/vnd.ms-excel"/>
						2. 上传.xslx格式 <input text="fiel" accept="application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"/>
						3. 上传jpg、png <input type="file" name="" accept="image/jpg, image/png"> 图片的文件格式大概有以下几种：'jpg' 、'JPG' 、 'jpeg' 、'JPEG'、 'png' 、 'PNG' 、 'gif' 、'GIF')

2.type: 输入框的类型
					常用取值
						1. text 普通文本
						2. password 密码文本
						3. radio 单选
								1). 配合label使用 点击文本也会同时选择
										<label><input type="radio" name="sex" value="male">男</label>
										<label><input type="radio" name="sex" value="female">女</label>
								2). name 为字段名
						4. checkbox 多选 同radio
						h5新增:
						1. color:  颜色选择器
						2. number: 应该包含数值的输入域
3. inputmode: 指定输入字段的输入模式 一般用于移动端
					常用取值
						text： 		默认值，文本输入模式，适用于一般文本输入。
            tel： 			电话号码输入模式，对应手机号、座机号等电话号码的输入。
            url： 			URL 输入模式，适用于输入网址 URL。
            email： 		电子邮件输入模式，适用于输入电子邮件地址。
            decimal：  小数表示键盘，除了数字之外可能会有小数点 . 或者千分符逗号 ,。
            numeric：  会显示 0-9 的数字键盘。
            search：   提交按钮会显示 “search” 或者 “搜索”。
4. enterkeyhint: 指示浏览器在虚拟键盘上的"Enter"键要如何表现
					常用取值
						enter：表示按下"Enter"键时会提交表单。
            done：表示按下"Enter"键完成输入，通常用于表示输入完成或确认。
            go：表示按下"Enter"键后执行默认操作。比如，在 URL 输入框中按下"Enter"键后会转到该网址。
            next：表示按下"Enter"键会切换到下一个输入字段。通常用于表单中的多个输入字段的切换。
            previous：表示按下"Enter"键会切换到上一个输入字段。同样用于表单中的多个输入字段的切换。
5. autofocus： input 获取焦点
6. required: 在form中必填
结合实际应用中常关联的(后续会逐步更新)：
	1.节流防抖 自写或者loadsh
	2.输入中文时触发input事件 compositionstart事件中将该标志位置为true，在compositionend事件中将其置为false。通过判断此标志位，我们可以确定何时处理input事件。
	3.事件触发
		1). input事件是改变值即触发
		2). change事件则是失去焦点时并且值发生改变才会触发
		3). blur 失去焦点则触发事件
	4. 移动端当输入框fixed定位在底部聚焦后 键盘挡住输入框
		1. window.addEventListener("resize", () => {
        document.activeElement.scrollIntoView(true);
      });
		2. document.body.scrollTop = document.body.scrollHeight
	5. 输入框清除两侧空白符 
		1.原生 document.getElementById("inputId").trim();
		2.在vue中使用 <input v-model.trim="msg">
	6.web端输入后回车执行
		1.原生  <input onkeydown="keydownMsg(event)" type="text" />
           function keydownMsg(key) {
                  keyCode = key.keyCode; //获取按键代码
                  if (keyCode == 13) {  //判断按下的是否为回车键
                      // 在input上监听到回车 do something
                  }
              }
		2. vue中 <input @keyup.enter="enterActive">
```

#### link

```html
说明：标签定义文档与外部资源之间的关系，大多数用来连接样式表
属性:
	1.href 外部资源所在位置
	2.ref
		1). stylesheet 览器链接的资源是一个样式表，并且浏览器应该将其应用于当前文档。样式表会在文档渲染过程中按需加载并应用。
		2). preload    指示浏览器预加载资源的提示。预加载的资源会在页面加载的早期阶段（甚至在解析 HTML 之前）开始下载，但它们不会自动执行或应用。这通常用于优化页面加载性能，特别是当你知道某个资源即将被请求时。示例：<link rel="preload" as="style" href="styles.css"> 使用了 as="style" 来明确指定预加载资源的类型为样式表
		3). prefetch   预取的资源会在浏览器空闲时下载，但并不会在当前的导航上下文中使用。预取通常用于预测用户接下来的行为，以便提前加载可能需要的资源
		4). icon       链接网站图标 示例：<link rel="icon" href="favicon.ico" type="image/x-icon">
	3. type
		1). text/css   链接到CSS样式表
		2). image/x-icon 或 image/vnd.microsoft.icon   链接到网站图标（favicon）
		3). application/font-woff、application/font-woff2、application/vnd.ms-fontobject    链接到Web字体
	
```

#### script

```html
说明： 标签用于嵌入或引用客户端脚本
属性：
	1.src 引入javascript脚本的路径
	2.async 这意味着脚本将在后台加载，而不会阻塞HTML解析器。然而，一旦脚本下载完成，HTML解析器将暂停并立即执行脚本，然后再继续解析HTML。请注意，如果有多个异步脚本，则它们可能会按照它们在HTML中出现的顺序执行，但也可能不会。 示例： <script async src="script.js"></script>
  3.defer 当设置为defer时，脚本也会异步加载，但会等到整个HTML文档解析完成后再执行。这意味着如果有多个defer脚本，它们将按照它们在HTML中出现的顺序执行。使用defer是优化页面加载速度的一个好方法，因为它允许HTML文档在脚本加载和执行时继续解析和渲染。 示例： <script defer src="script.js"></script>
	4.type 省略type属性，或者将其设置为"text/javascript"或"application/javascript"
				 对于ES6模块脚本，你应该使用type="module"。这告诉浏览器该脚本应该作为JavaScript模块来加载和执行。模块脚本具有一些特殊的特性，如静态导入/导出、严格模式等。
```

#### canvas

[详细api](https://www.canvasapi.cn/)

```html
1.height
	示例 获取高度： var pixel = canvas.height; 设置高度：canvas.height = pixel;
2.width 同理
3.getContext
	示例：常用 canvas.getContext('2d') 获取当前canvas绘制上下文
4.toBlob void canvas.toBlob(callback, mimeType, quality);  异步的
	callback: 成功后的回调方法，支持一个参数，表示当前转换的Blob对象
	mimeType: 默认值是image/png，还可以是image/jpeg
	quality: 范围是0-1 默认是0.92
	兼容性： toBlob()方法IE9浏览器不支持，
	示例：1.将canvas图像上传
	canvas.toBlob((blob) => {
		var formData = new FormData()
		formData.append('image', blob)
		var xhr = new XMLHttpRequest();
    // 文件上传成功
    xhr.onload = function() {
        // xhr.responseText就是返回的数据
    };
      // 开始上传
      xhr.open('POST', 'upload.php', true);
      xhr.send(data); 
		})
			2. 将blob转为img的src展示
        canvas.toBlob((blob) => {
        var url = URL.createObjectURL(blob); // Blob数据转URL地址
        p.innerHTML = `<img src=${url}>`
    }, 'image/png')
	5. toDataURL canvas.toDataURL(mimeType, quality); 参数含义同上 同步
		示例： 转为base64 image/png 默认
		canvas.toDataURL(); 或者canvas.toDataURL('image/jpeg');
console.log(dataURL);
"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAAF0lEQVQoU2NkIBIwEqmOYVQh3pAiOngACmkAC5eMKzgAAAAASUVORK5CYII="
	5.fillStyle
		示例1: 色值填充
			canvas.fillStyle = 'RGB(255,0,0)' 也支持透明色 rgba(1,1,1, .1)
		示例2: 线性渐变
			创建线性渐变
			var gradientLinear = canvas.createLinearGradient(0,0,0, 100)
			// 线性渐变效果比较好脑补，就是从坐标点[x0, y0]到坐标点[x1, y1]的位置画一条线，然后整个渐变色带与与这条线垂直。
		示例3:. 渐变填充-径向
			var gradientRadial = contextRadial.createRadialGradient(60, 60, 0, 60, 60, 50);
			【前60, 60 表示初始圆心坐标
        0 表示起始圆半径
        60，60 结束圆心坐标
        50 结束圆半径】
			gradientLinear.addColorStop(0, 'red');
			gradient.addColorStop(0.2, 'red'); // 0-0.2 为红色 依次类推
			gradient.addColorStop(0.2, 'orange');
			gradient.addColorStop(0.4, 'orange');// 0-0.2 为橘色 依次类推
      gradientLinear.addColorStop(1, 'green');
      contextLinear.fillStyle = gradientLinear 或 gradientRadial;
      contextLinear.fillRect(10, 10, 100, 100);
6.font 设置字号字体值
		示例1: context.font = '24px SimSun, Songti SC'; 
7. fillText context.fillText(text, x, y [, maxWidth]);
		text 文本信息 x为文本横坐标 y为纵坐标 maxwidth 最大宽度 超过则横向压缩
		示例  context.fillText('Canvas API，不只是文档', 20, 66, 200);
8.wrapText context.wrapText(text, x, y [, maxWidth]);
		示例 context.wrapText('Canvas APi，不只是文档', 24, 56, 200); 到文本在200像素宽度范围内自动换行显示了
9.textAlign 文字对齐方式
	示例 canvas.textAlign = 'left'   类似效果 |left
		  canvas.textAlign = 'right'   类似效果 left｜
			canvas.textAlign = 'center'   类似效果 le｜ft
10.drawImage 在cancas画图片
	context.drawImage(image, dx, dy);
	context.drawImage(image, dx, dy, dWidth, dHeight);
	context.drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight); // 注意参数位置变化
	image // 图片路径
	dx     // Canvas画布上规划一片区域用来放置图片，dx就是这片区域的左上角横坐标
 	dy     // Canvas画布上规划一片区域用来放置图片，dy就是这片区域的左上角纵坐标
	dWidth // 在Canvas画布上规划一片区域用来放置图片，dWidth就是这片区域的宽度
	dHeight// 在Canvas画布上规划一片区域用来放置图片，dHeight就是这片区域的高度
	sx     // 表示图片元素绘制在Canvas画布上起始横坐标。
	sy。   // ------------------------------纵---
  sWidth // 表示图片元素从坐标点开始算，多大的宽度内容绘制Canvas画布上。
  sHeight//表示图片元素从坐标点开始算，多大的高度内容绘制Canvas画布上。
11. beginPath	开始一个新的路径
 示例
    context.beginPath();
    context.strokeStyle = 'blue';
    context.moveTo(60, 20); 
    context.lineTo(220, 20);
    context.stroke();
    // 开始路径 again
    context.beginPath(); 非连续路径绘制，都要记得都要执行一句context.beginPath()。 删除该行则两条线都为绿色
    context.strokeStyle = 'green';
    context.moveTo(60, 20);
    context.lineTo(160, 120);
    context.stroke();
```



代码雨效果：[示例查看](./canvas/codeRain.html)

粒子效果： [示例查看](./canvas/point.html)

刮刮卡效果：[示例查看](./canvas/scratchCard.html)



#### ruby

```html
实现文字标注读音 
示例： <ruby>我<rt>diāo</rt></ruby>
      <ruby>厉<rt>chóng</rt></ruby>
      <ruby>害<rt>xiǎo</rt></ruby>
      <ruby>吧<rt>jì</rt></ruby>
rt： 对 ruby 注释文本的解释
一般结合第三方库 npm install pinyin --save
使用示例：
var chineseText = "你好，世界！";  
var pinyinArray = pinyin(chineseText, {  
    style: pinyin.STYLE_NORMAL, // 拼音风格，默认是不带声调的
    heteronym: false, // 是否启用多音字处理，默认是 false  
}); 
```

#### 



