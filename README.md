# 移动端适配知识点

**提示：以下内容全部为移动端知识点，只用于移动端，pc端可能会有所差异**


![layout](https://github.com/wangx1229/viewport/blob/master/imgs/px.png)

### 手机设备独立像素

iphone 6s手机像素分辨率375*667， 他的物理像素就是750px * 1334px。

### 手机物理像素

iphone 6s手机像素分辨率750*1334， 他的物理像素就是750px * 1334px。

### 设备像素比 Device Pixel Ratio

dpr = 物理像素/设备像素

### 移动端视口

![viewport](https://github.com/wangx1229/viewport/blob/master/imgs/viewport.png)

<meta name="viewport" content="width=device-width,initial-scale=1"/>

##### 一、布局视口 Layout Viewport

布局视口，可以理解为要展示的所有内容所占据的空间。

在移动端默认情况下布局视口是980px，可以通过meta标签中content属性去设置布局视口。上面width所代表的就是布局视口的宽度。 

注意，虽然width可以设置布局视口宽度，但实际上布局视口的宽度取决于视觉视口和布局视口中的最大值。即Math.max(Layout Viewport, Visual Viewport)

![layout](https://github.com/wangx1229/viewport/blob/master/imgs/layout.png)

##### 二、视觉视口 Visual Viewport

视觉视口，是我们通过手机屏幕所看到的视口范围。他和设备像素的物理像素相关联。

默认情况下也是980px。因为initial-scale=设备宽度/视觉视口，而每一台设备的设备度是固定的，所以我们可以通过initial-scale来设置视觉视口的大小。

例如，ip6s设备宽度为375，当设置intial-scale=1时，视觉视口变为375px，initial-scale=0.5时，视觉视口变为750px。

![layout](https://github.com/wangx1229/viewport/blob/master/imgs/visual.png)

##### 三、理想视口 Ideal Viewport

这里的理想视口，其实是理想化的布局视口。布局视口的最理想的值就是设备宽度，所以经常会看到在meta中设置width=device-width。

##### 四、适配布局

1.rem布局

原理： 1rem的大小指的就是html上font-size的大小。

根据dpr，动态设置initial-scale，使得视觉视口和物理像素保持一致

然后将设备宽度设置为10rem， 那么1rem = 设备宽度/10 = font-size 大小

假设 a=元素在设备上的宽度，b=设备的宽度，x=设计稿中元素的宽度，y=设计稿的宽度。 

a/b = x/y ， a = x / y * b = x / y * 10rem = x / y * (10 * font-size) 

每次自己计算a肯定很麻烦，可以使用sass函数封装fn，每次只需要传入x自动计算得到a。


##### 五、宽度的获取

screen.width：移动端指设备的独立像素 PC端是屏幕的宽度

window.innerWidth：移动端指视觉视口的宽度 PC端是包含滚动条的视口宽度

document.documentElement.clientWidth：布局视口的宽度 也就是document中文档的宽度

> 参考

[很久以前手淘使用flexsible适配h5](https://github.com/amfe/article/issues/17)

[关于meta详解](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta)

[CSS Device Adaptation](https://drafts.csswg.org/css-device-adapt/#viewport-desc)

[flexsible.js](https://github.com/amfe/lib-flexible/blob/2.0/index.js)

