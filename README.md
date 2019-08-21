# 移动端适配知识点

warn：以下内容全部为移动端知识点，只用于移动端，pc端可能会有所差异

![layout](https://github.com/wangx1229/viewport/blob/master/imgs/px.png)

### 手机设备像素

iphone 6s手机像素分辨率375*667， 他的物理像素就是750px * 1334px。

### 手机物理像素

iphone 6s手机像素分辨率750*1334， 他的物理像素就是750px * 1334px。

### 设备像素比 Device Pixel Ratio

dpr = 物理像素/设备像素

### 移动端视口

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

a/b = x/y   

a=元素在设备上的宽度，b=设备的宽度，x=设计稿中元素的宽度，y=设计稿的宽度。 a = x * b / y

[很久以前手淘使用flexsible适配h5](https://github.com/amfe/article/issues/17)

[关于meta详解](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta)

