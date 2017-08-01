# meta
1. H5页面窗口自动调整到设备宽度，并禁止用户缩放页面
    >   \<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />

2. 忽略将页面中的数字识别为电话号码
    >  \<meta name="format-detection" content="telephone=no" />

3. 忽略Android平台中对邮箱地址的识别
    >  \<meta name="format-detection" content="email=no" />

4. 当网站添加到主屏幕快速启动方式，可隐藏地址栏，仅针对ios的safari
    >  \<meta name="apple-mobile-web-app-capable" content="yes" /><!-- ios7.0版本以后，safari上已看不到效果 -->

5. 将网站添加到主屏幕快速启动方式，仅针对ios的safari顶端状态条的样式
    >  \<meta name="apple-mobile-web-app-status-bar-style" content="black" /><!-- 可选default、black、black-translucent -->

# viewport模板
1. viewport模板——通用
    >  \<!DOCTYPE html><html><head><meta charset="utf-8"><meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport"><meta content="yes" name="apple-mobile-web-app-capable"><meta content="black" name="apple-mobile-web-app-status-bar-style"><meta content="telephone=no" name="format-detection"><meta content="email=no" name="format-detection"><title>标题</title><link rel="stylesheet" href="index.css"></head>
    <body></body></html>

2. viewport模板 – target-densitydpi=device-dpi，android 2.3.5以下版本不支持

    > \<!DOCTYPE html><html><head><meta charset="utf-8"><meta name="viewport" content="width=750, user-scalable=no, target-densitydpi=device-dpi"><!-- width取值与页面定义的宽度一致 --><meta content="yes" name="apple-mobile-web-app-capable"><meta content="black" name="apple-mobile-web-app-status-bar-style"><meta content="telephone=no" name="format-detection"><meta content="email=no" name="format-detection"><title>标题</title><link rel="stylesheet" href="index.css"></head><body></body></html>

# 移动端如何定义字体font-family
中文字体使用系统默认即可，英文用Helvetica
> /* 移动端定义字体的代码 */body{font-family:Helvetica;}

rem配置参考：

> html{font-size:10px}@media screen and (min-width:321px) and (max-width:375px){html{font-size:11px}}@media screen and (min-width:376px) and (max-width:414px){html{font-size:12px}}@media screen and (min-width:415px) and (max-width:639px){html{font-size:15px}}@media screen and (min-width:640px) and (max-width:719px){html{font-size:20px}}@media screen and (min-width:720px) and (max-width:749px){html{font-size:22.5px}}@media screen and (min-width:750px) and (max-width:799px){html{font-size:23.5px}}@media screen and (min-width:800px){html{font-size:25px}}

# 什么是Retina 显示屏，带来了什么问题

retina：一种具备超高像素密度的液晶屏，同样大小的屏幕上显示的像素点由1个变为多个，如在同样带下的屏幕上，苹果设备的retina显示屏中，像素点1个变为4个,在高清显示屏中的位图被放大，图片会变得模糊，因此移动端的视觉稿通常会设计为传统PC的2倍

### 前端方案:
1. 设计稿切出来的图片长宽保证为偶数，并使用backgroud-size把图片缩小为原来的1/2

## ios系统中元素被触摸时产生的半透明灰色遮罩怎么去掉

ios用户点击一个链接，会出现一个半透明灰色遮罩, 如果想要禁用，可设置-webkit-tap-highlight-color的alpha值为0，也就是属性值的最后一位设置为0就可以去除半透明灰色遮罩

>  a,button,input,textarea{-webkit-tap-highlight-color: rgba(0,0,0,0;)}

## 部分android系统中元素被点击时产生的边框怎么去掉

android用户点击一个链接，会出现一个边框或者半透明灰色遮罩, 不同生产商定义出来额效果不一样，可设置-webkit-tap-highlight-color的alpha值为0去除部分机器自带的效果

> a,button,input,textarea{-webkit-tap-highlight-color: rgba(0,0,0,0-webkit-user-modify:read-write-plaintext-only;}

## webkit表单元素的默认外观怎么重置

> .css{-webkit-appearance:none;}

## webkit表单输入框placeholder的颜色值能改变么

> input::-webkit-input-placeholder{color:#AAAAAA;}input:focus::-webkit-input-placeholder{color:#EEEEEE;}

## ::-ms-expand 适用于表单选择控件下拉箭头的修改，有多个属性值，设置它隐藏 (display:none) 并使用背景图片来修饰可得到我们想要的效果。

> select::-ms-expand {display: none;}

## 禁用 radio 和 checkbox 默认样式

::-ms-check 适用于表单复选框或单选按钮默认图标的修改，同样有多个属性值，设置它隐藏 (display:none) 并使用背景图片来修饰可得到我们想要的效果。
> input[type=radio]::-ms-check,input[type=checkbox]::-ms-check{display: none;}

## 禁用PC端表单输入框默认清除按钮

当表单文本输入框输入内容后会显示文本清除按钮，::-ms-clear 适用于该清除按钮的修改，同样设置使它隐藏 (display:none) 并使用背景图片来修饰可得到我们想要的效果。
> input[type=text]::-ms-clear,input[type=tel]::-ms-clear,input[type=number]::-ms-clear{display: none;}

## 禁止ios 长按时不触发系统的菜单，禁止ios&android长按时下载图片
> .css{-webkit-touch-callout: none}

## 禁止ios和android用户选中文字

> .css{-webkit-user-select:none}

### 打电话
> \<a href="tel:0755-10086">打电话给:0755-10086</a>
### 发短信，winphone系统无效
> \<a href="sms:10086">发短信给: 10086</a>
### 写邮件，可参考《移动web页面给用户发送邮件的方法》
> \<a href="mailto:peun@foxmail.com">peun@foxmail.com</a>

## 模拟按钮hover效果
移动端触摸按钮的效果，可明示用户有些事情正要发生，是一个比较好体验，但是移动设备中并没有鼠标指针，使用css的hover并不能满足我们的需求，还好国外有个激活css的active效果，代码如下，

> <!DOCTYPE html><html><head><meta charset="utf-8"><meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport"><meta content="yes" name="apple-mobile-web-app-capable"><meta content="black" name="apple-mobile-web-app-status-bar-style"><meta content="telephone=no" name="format-detection"><meta content="email=no" name="format-detection"><style type="text/css">a{-webkit-tap-highlight-color: rgba(0,0,0,0);}.btn-blue{display:block;height:42px;line-height:42px;text-align:center;border-radius:4px;font-size:18px;color:#FFFFFF;background-color: #4185F3;}.btn-blue:active{background-color: #357AE8;}</style></head><body><div class="btn-blue">按钮</div><script type="text/javascript">document.addEventListener("touchstart", function(){}, true)</script></body></html>

## 屏幕旋转的事件和样式
事件window.orientation，取值：正负90表示横屏模式、0和180表现为竖屏模式

>window.onorientationchange = function(){
    switch(window.orientation){
        case -90:case 90:alert("横屏:" + window.orientation);
    case 0:case 180:alert("竖屏:" + window.orientation);break;
    }}

### 取消input在ios下，输入的时候英文首字母的默认大写

>  /<input autocapitalize="off" autocorrect="off" />
### android 上去掉语音输入按钮

>   input::-webkit-input-speech-button {display: none}
