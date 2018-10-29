---
ID: 3481
post_title: 安装package control的几种方法
post_name: '%e5%ae%89%e8%a3%85package-control%e7%9a%84%e5%87%a0%e7%a7%8d%e6%96%b9%e6%b3%95'
author: 小奥
post_date: 2017-10-16 23:57:05
layout: post
link: >
  http://www.yushuai.me/2017/10/16/3481.html
published: true
tags:
  - Python
  - python学习
categories:
  - Python
---
<ol class=" list-paddingleft-2" style="list-style-type: decimal;"><li><p>在线安装：</p><p>import urllib.request,os,hashlib; h = &#39;6f4c264a24d933ce70df5dedcf1dcaee&#39; + &#39;ebe013ee18cced0ef93d5f746d80ef60&#39;; pf = &#39;Package Control.sublime-package&#39;; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( &#39;http://packagecontrol.io/&#39; + pf.replace(&#39; &#39;, &#39;%20&#39;)).read(); dh = hashlib.sha256(by).hexdigest(); print(&#39;Error validating download (got %s instead of %s), please try manual install&#39; % (dh, h)) if dh != h else open(os.path.join( ipp, pf), &#39;wb&#39; ).write(by)<br/></p></li><li><p>如果无法安装可以执行离线安装：</p><p><br/></p><p>1.Click the&nbsp;<span class="menu" style="border-radius: 2px; background-color: #F3F3F3; padding: 1px 4px; text-shadow: #FFFFFF 0px 1px 0px;">Preferences&nbsp;<span style="opacity: 0.5;">&gt;</span>&nbsp;Browse Packages…</span>&nbsp;menu</p><p>2.Browse up a folder and then into the&nbsp;<tt>Installed Packages/</tt>&nbsp;folder</p><p>3.<a href="https://packagecontrol.io/installation" target="_self">Download</a> &nbsp;copy it into the&nbsp;<tt>Installed Packages/</tt>&nbsp;directory</p><p>4.Restart Sublime Text</p></li></ol>