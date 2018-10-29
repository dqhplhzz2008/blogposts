---
ID: 3302
post_title: >
  如何将wavrecord()更改为audiorecorder()？
post_name: '%e5%a6%82%e4%bd%95%e5%b0%86wavrecord%e6%9b%b4%e6%94%b9%e4%b8%baaudiorecorder%ef%bc%9f'
author: 小奥
post_date: 2017-01-11 17:51:50
layout: post
link: >
  http://www.yushuai.me/2017/01/11/3302.html
published: true
tags: [ ]
categories:
  - 个人作品
---
在matlab2014之后，wavirecord函数被audiorecorder函数取代，要实现替换，可以做以下操作：
<pre><span style="background-color: #666699;"> x=wavrecord(Fs,Fs);</span></pre>
with the following
<pre><span style="background-color: #33cccc;"> % create the recorder
 recorder=audiorecorder(Fs,8,1);</span></pre>
<pre><span style="background-color: #33cccc;"> % record one second of data
 record(recorder,1);</span></pre>
<pre><span style="background-color: #33cccc;"> % get the samples
 x = getaudiodata(recorder);

<span style="background-color: #ffffff;">转载自https://cn.mathworks.com/matlabcentral/answers/165279-how-to-change-wavrecord-to-audiorecorder?</span></span></pre>