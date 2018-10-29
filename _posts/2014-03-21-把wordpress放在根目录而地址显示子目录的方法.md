---
ID: 2433
post_title: >
  把WordPress放在根目录而地址显示子目录的方法
post_name: '%e6%8a%8awordpress%e6%94%be%e5%9c%a8%e6%a0%b9%e7%9b%ae%e5%bd%95%e8%80%8c%e5%9c%b0%e5%9d%80%e6%98%be%e7%a4%ba%e5%ad%90%e7%9b%ae%e5%bd%95%e7%9a%84%e6%96%b9%e6%b3%95'
author: 小奥
post_date: 2014-03-21 16:20:54
layout: post
link: >
  http://www.yushuai.me/2014/03/21/2433.html
published: true
tags: [ ]
categories:
  - Wordpress
---
把WordPress安装在根目录但是让博客首页显示在子目录，这和上篇的教程实现的效果刚好相反。要实现这样的效果前提是你的空间必须支持rewrite功能。我们可以用两种方法实现：<!--more-->

1、参照上篇的方法，相信大家已经心中有数了：WordPress安装到根目录，我们在根目录下再新建一个子目录，比如”blog”目录。同样将根目录的index.php和.htaccess文件转移到”blog”目录目录中。在index.php里查找：

require(’./wp-blog-header.php’);

修改为：

require(’../wp-blog-header.php’);

再加个点就行了，表示引用上个目录中的文件。

其他更改博客和WordPress地址方法和上篇类似，照葫芦画瓢即可。注意把博客地址改为：http://example.com/blog，同时要把页面结构更改成”/blog/xxx…”类型。

2、下面这种方法要用到页面模板的相关技巧。对页面模板一无所知？先去水煮鱼的使用WordPress静态模板那里充点电把！充过电别忘了回来，呵呵~利用页面模板我们甚至还可以将WordPress打造成一个轻量级的CMS。

新建一个blog.php的文件，放到所使用的模板目录中。此文件所包含的内容为：

<!--?php <br ?--> /*
Template Name: Blog
*/
?&gt;

<!--?php query_posts(’cat=-0′); //gets all posts<br ?--> load_template( TEMPLATEPATH . ‘/index.php’); //loads index
?&gt;

登陆后台，新建一个页面，命名为”blog”，并使用”blog”页面模板。切记一定要让此页面的缩略名、或者叫做数据域，更改为”blog”！

最后一步同样是更新页面结构，把页面结构更新为”/blog/xxx…”类型即可。