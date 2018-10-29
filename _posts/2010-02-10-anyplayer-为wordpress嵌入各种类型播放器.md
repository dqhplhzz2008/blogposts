---
ID: 576
post_title: >
  AnyPlayer –
  为WordPress嵌入各种类型播放器
post_name: 'anyplayer-%e4%b8%bawordpress%e5%b5%8c%e5%85%a5%e5%90%84%e7%a7%8d%e7%b1%bb%e5%9e%8b%e6%92%ad%e6%94%be%e5%99%a8'
author: 小奥
post_date: 2010-02-10 01:52:23
layout: post
link: >
  http://www.yushuai.me/2010/02/10/576.html
published: true
tags:
  - WP插件
categories:
  - Wordpress
---
声明：以下内容转自<a href="http://cpiz.com/blog/archives/159">http://cpiz.com/blog/archives/159</a><!--more-->
<ul>
	<li><strong>使用是这样子的：</strong></li>
</ul>
在文章编辑模式入插入［anyplayer:type=swf url=http://xxxx.com/swf width=400 height=300］，注意，两边要使用半角方括号。
<ol>
	<li>type是媒体类型，支持swf flv mp3 wma wmv rm ra qt</li>
	<li>url是媒体地址</li>
	<li>width是播放器宽度，缺省则为450</li>
	<li>height是播放器高度，缺省则为350</li>
</ol>
PS：属性不能用引号括起来
<ul>
	<li><strong>效果是这样子的：</strong></li>
</ul>
<strong>swf:</strong>支持各种标准的flash文件，常见视频网站上的视频都可采用这种方式发布

［anyplayer:type=swf url=http://cpiz.com/files/bloxorz.swf width=500 height=300］ 

［anyplayer:type=swf url=http://www.youtube.com/v/flwnaJXi9y0&amp;rel=1 width=425 height=355]

<strong>flv:</strong>基本上和swf使用一样

［anyplayer:type=flv url=http://www.whosworks.com/upload/20081111992260222.flv width=460 height=330］ 

<strong>mp3:</strong>如果不需要皮肤自定义功能的话，可以替下<a href="http://www.1pixelout.net/code/audio-player-wordpress-plugin/">Audio player</a>了，该模式下宽高属性无效

［anyplayer:type=mp3 url=http://bbmedia.qq.com/media/yule/kekewang/music/jindie/sunyanzitonglei.mp3 ] 

<strong>wma:</strong>调用MediaPlayer播放音频，Firefox下要额外插件支持，该模式下宽高属性无效

［anyplayer:type=wma url=http://show.jj.jx.cn/upload_mp3/20071021196261562.wma］

<strong>wmv:</strong>调用MediaPlayer播放音频，Firefox下要额外插件支持

［anyplayer:type=wmv url=http://mtv26.3378.com.cn/071110/梁静茹_www.3378.com.cn崇拜(完整版).wmv width=460 height=400］ 
<ul>
	<li><strong>最新修改:</strong></li>
</ul>
v0.0.4 修正了部分主机对js参数有安全性检查, 可能导致无法显示播放器的Bug