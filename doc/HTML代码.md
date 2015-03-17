@(示例笔记本)[HTML规则|CSS规则]
# HTML代码
### 硬规范
**1)** LUI目前主要划分为Layout、Components、Animation库，三大块：
     **Layout: ** class 命名必须是以`layout-` 开头，千万不可滥用. 如：`.layout-items .layout-item` 最好是  `.layout-items .item`；
     **Components: ** class 命名必须是以`ui-` 开头，需要特殊化类名会以`--` 开头，如：`layer--primary`
     **Animation库** 提供各种动画class接口,具体见库的说明文档；
**2)** **font-face** `font-family`必须是 `'icon-font'` , 图标Unicode 字符命名必须是`font-`;
**3)** **icon** 对于字体无法实现的`icon`,我们采用`图片sprite`技术，class命名必须是`icon-`开头;
**4)** **公共CSS** class 命名必须是 `g-` 开头;
**5)** ID是用来标识具体模块，命名必须具体且唯一，由前缀和名字组成。不要滥用ID。如： `#ticket-list、#flight-tab`等。
**6)** 如JS需要增加class ，可以 `.js-xxx` 类型，区别的CSS工程师class.

### z-index 规范
z-index 在整个 `left.ui` 框架中应用非常广特别是组件的组合运用时，我们对组件拆分成三大类：
`alert`、`toast`、`loading`、`layer`、`share` ：**`z-index:9999`**
`mask`：**`z-index:999`**
`header`、`warning404` ： **`z-index:99`**
`viewport 默认不设`


### 基本要求
**1)** 采用HTML5声明
``` html
<!doctype html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>	
</body>
</html>
```
**2)** 编码必须声明为UTF-8;
**3)** <link rel="stylesheet" href="" type="text/css">  `type="text/css"`可省略;
**4)** 如非必要，不允许在`html`或标签里写`style`;
**5)** `Link` 和`style` 标签都应该放在head里;
**6)** 引入CSS文件或JavaScript文件时, 须略去默认类型声明，并在最后给出版本号标示，格式为：`?t=20140212`，默认版本号为当前修改时间，当文件有更新时，需要相应地修正文件的版本号。如`：<link href="main.css?t=20140212" rel="stylesheet" />`;

### 注释
HTML 模块注释
`<!--模块描述  Star-->`
`<!--模块描述  End-->`
建议上线前使用打包工具删除这些注释

### 属性
`<input type=”text” />`, 必要时我们需要针对产品设置type默认值，比如: `email、number、url、tel、required`等

### 标签
**1)** 更多的使用`HTML5`新标签，禁止使用被废弃标签;
**2)** `h1/h2/h3/h4/h5`的标签使用，应遵循从大到小的原则去使用;
**3)** 用`div`代替`table`布局，可以使HTML更具灵活性，也方便利用CSS控制;
**4)** `table`不建议用于布局，但表现具有明显表格形式的数据，table还是首选;
**5)** `<a href=”#”></a>`建议都转成`block`元素，便于用户点击;
### Viewport
基本设置：`<meta name="viewport" content="width=device-width,initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">` 需要注意 `ios7`是不支持`device-width`的，可以直接把`width=320.1或JS`方法

### Media Queries
``` python 
orientation: landscape(横屏)或portrait(竖屏)
@media screen and (orientation:portrait) {
      body{
	    background:red;	
      }
}

@media only screen and (min-device-width : 320px) and (max-device-width : 480px) {
     body{
	    background:red;	
      }
}

@media only screen and (-webkit-min-device-pixel-ratio : 1.5),
only screen and (min-device-pixel-ratio : 1.5) {
}

<link rel="stylesheet" media="only screen and (-webkit-min-device-pixel-ratio: 2)" type="text/css" href="iphone4.css" />
<link rel=”stylesheet” media=”all and (orientation:portrait)” href=”portrait.css”>
```
> 资料：http://nmsdvid.com/snippets/# (Media Query Snippets)

### HTML<META>
> https://gist.github.com/ericlva/9071491

-------------------
# CSS代码
### 基本要求
**1)** CSS文件顶部需要申明编码为`UTF-8`;
**2)** 避免使用`filter、expression、@import`，尽量不要在CSS中使用`!important`，更不能使用 `* `选择器;
**3)** 字体设置
`font:normal 14px/1.5 "Arial","Lucida Grande",Verdana,"Microsoft YaHei","hei"`;
**4)** 缩进 4 空格;
**5)** 规则声明的顺序：定位、盒模型`（width/height/padding/border/margin）`、行高、字体/字号/颜色、背景、CSS3效果等
**6)** CSS3兼容书写形式和对齐方式，拆分成多行:
``` python 
a:hover {
	-webkit-transition:color .2s linear;
	   -moz-transition:color .2s linear;
	    -ms-transition:color .2s linear;
	     -o-transition:color .2s linear;
	        transition:color .2s linear;
}
```
**7)** CSS3中用逗号分隔的长属性值：
``` python 
box-shadow:1px 1px 1px #000,2px 2px 1px 1px #ccc inset;
background-image:linear-gradient(#fff, #999),linear-gradient(#666, #333);
```
**8)** 多个selector(>2)每个占一行
``` python
.selector1,
.selector2,
.selector3 { ... }
```

**9)** 所有的属性可以按类型分块写,便于查找和观看:
``` css
.selector {
    width:10px;
    height:10px;
    margin:10px;
    padding:10px;
    
    -webkit-box-flex: 1;
    -moz-box-flex: 1;
    -webkit-flex: 1;
    -ms-flex: 1;
    flex: 1;
    
    -webkit-transform:rotate(-45deg);
    -moz-transform:rotate(-45deg);
    -ms-transform:rotate(-45deg);
    -o-transform: rotate(-45deg);
    transform: rotate(-45deg);
}
```



##### 更多资料：
[书写更好性能的CSS]( http://flippinawesome.org/2013/08/12/writing-better-css/?utm_source=html5weekly&utm_medium=email)
https://github.com/jtyjty99999/mobileTech
http://www.slideshare.net/lijing00333/web-13546648
