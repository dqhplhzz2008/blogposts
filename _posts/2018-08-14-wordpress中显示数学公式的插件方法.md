---
ID: 3868
post_title: >
  WordPress中显示数学公式的插件方法
post_name: 'wordpress%e4%b8%ad%e6%98%be%e7%a4%ba%e6%95%b0%e5%ad%a6%e5%85%ac%e5%bc%8f%e7%9a%84%e6%8f%92%e4%bb%b6%e6%96%b9%e6%b3%95'
author: 小奥
post_date: 2018-08-14 11:01:53
layout: post
link: >
  http://www.yushuai.me/2018/08/14/3868.html
published: true
tags: [ ]
categories:
  - Wordpress
---
<p>&nbsp; 在日常生活中，我们写博客文章倒是很少遇到数学公式，但是在写学术性博客文章的时候，数学公式是很常用的。Wordpress默认的编辑器是无法正常输入公式的，为此我们可以利用插件MathJax-LaTeX来实现。</p><p>&nbsp; &nbsp; 如果在国外环境下，下载该插件即可使用，无需另外设置。但是由于其服务器经常被国内墙，所以在国内使用的话，需要将许多文件转移到本地来运行。</p><p>&nbsp; &nbsp; 在这里，我分享一下国内的安装方法，如果是在国外访问的，那么只需要执行第一步即可。</p><p>1.首先在wordpress中下载该插件，然后安装。</p><p>2.下载MathJax，下载地址为https://github.com/mathjax/MathJax/archive/master.zip</p><p>3.解压该文件，并上传至该插件的目录下。</p><p>4.测试 MathJax 是否安装成功。访问 http://yourdomainname/wp-content/plugins/mathjax-latex/MathJax/test/</p><p>5.然后在wordpress后台settings目录中的找到MathJax-LaTeX，在这里面中关掉使用CDN加速，然后设置本地js的位置。由于步骤2中下载到的文件夹的目录为MathJax-master，而我改为了mathjax，所以我设置的地址为：/wp-content/plugins/mathjax-latex/MathJax/MathJax.js。然后点击Save changes。完成。</p><p>6.在文章中输入：</p><p>{latex}E=MC^2[/latex]</p><p>（记得将<strong>{}</strong>换为<strong>[]</strong>）</p><p><br/></p><p>那么，文章访问时效果图如下图所示：</p><p><br/>[latex]E=mc^2[/latex]</p><p>最后，欢迎关注我的个人微信公众号，在这里我会分享个人的学习笔记和个人收获等。</p><p style="text-align: center"><img src="https://dqhplhzz2008-1251830035.cos.ap-guangzhou.myqcloud.com/wp-content/uploads/2018/05/qrcode_for_gh_1fc8fb002414_258.jpg"/></p>