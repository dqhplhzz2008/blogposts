---
ID: 3507
post_title: >
  python处理csv文件，以锡特卡气温为例
post_name: 'python%e5%a4%84%e7%90%86csv%e6%96%87%e4%bb%b6%ef%bc%8c%e4%bb%a5%e9%94%a1%e7%89%b9%e5%8d%a1%e6%b0%94%e6%b8%a9%e4%b8%ba%e4%be%8b'
author: 小奥
post_date: 2017-10-22 19:59:21
layout: post
link: >
  http://www.yushuai.me/2017/10/22/3507.html
published: true
tags:
  - Python
  - python学习
categories:
  - Python
---
<p>high_low_mean.py</p><pre class="brush:python;toolbar:false">#&nbsp;-*-&nbsp;coding:&nbsp;utf-8&nbsp;-*-
&quot;&quot;&quot;
Created&nbsp;on&nbsp;Sun&nbsp;Oct&nbsp;22&nbsp;18:19:57&nbsp;2017
@author:&nbsp;dqhpl
&quot;&quot;&quot;
import&nbsp;csv
from&nbsp;matplotlib&nbsp;import&nbsp;pyplot&nbsp;as&nbsp;plt
from&nbsp;datetime&nbsp;import&nbsp;datetime#获取时间的包
filename&nbsp;=&nbsp;&#39;sitka_weather_2014.csv&#39;
with&nbsp;open(filename)&nbsp;as&nbsp;f:
&nbsp;&nbsp;&nbsp;&nbsp;reader&nbsp;=&nbsp;csv.reader(f)
&nbsp;&nbsp;&nbsp;&nbsp;header_row&nbsp;=&nbsp;next(reader)
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;highs,dates,&nbsp;lows,&nbsp;means&nbsp;=&nbsp;[],[],[],[]
&nbsp;&nbsp;&nbsp;&nbsp;for&nbsp;row&nbsp;in&nbsp;reader:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;try:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;current_date&nbsp;=&nbsp;datetime.strptime(row[0],&nbsp;&quot;%Y-%m-%d&quot;)#转换为日期形式，格式记住
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;low&nbsp;=&nbsp;int(row[3])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;high&nbsp;=&nbsp;int(row[1])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;mean&nbsp;=&nbsp;int(row[2])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;except&nbsp;ValueError:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(current_date,&nbsp;&#39;missing&nbsp;data&#39;)#如果有日期缺失数据提醒没有数据
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;else:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dates.append(current_date)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;lows.append(low)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;highs.append(high)#每一行第1列的数据加入（这个其实是第2列，真正的第1列是第0列）
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;means.append(mean)
fig&nbsp;=&nbsp;plt.figure(dpi&nbsp;=128,figsize=(10,5))
plt.plot(dates,&nbsp;highs,&nbsp;c=&#39;red&#39;,&nbsp;alpha&nbsp;=&nbsp;0.3)#alpha指定透明度，0是完全透明，1是完全不透明
plt.plot(dates,&nbsp;lows,&nbsp;c=&#39;blue&#39;,&nbsp;alpha&nbsp;=0.3)
plt.plot(dates,&nbsp;means,&nbsp;c=&#39;yellow&#39;)
plt.fill_between(dates,&nbsp;highs,&nbsp;lows,&nbsp;facecolor=&nbsp;&#39;blue&#39;,&nbsp;alpha=0.1)
#设置图像格式
plt.title(&quot;Daily&nbsp;high&nbsp;temperatures&nbsp;-&nbsp;2014&quot;,&nbsp;fontsize&nbsp;=&nbsp;14)
fig.autofmt_xdate()#绘制斜的日期标签
plt.ylabel(&quot;Temperature(F)&quot;,&nbsp;fontsize&nbsp;=10)
plt.savefig(&#39;temperature.png&#39;,&nbsp;&nbsp;bbox_inces&nbsp;=&nbsp;&#39;tight&#39;)
#plt.show()#plt.show()打开matplotlib查看器，并显示绘制的图形
#&nbsp;&nbsp;&nbsp;&nbsp;for&nbsp;index,column_header&nbsp;in&nbsp;enumerate(header_row):#enumerate()表示来获取每个元素的索引及其值
#&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(index,&nbsp;column_header)</pre><p><br/></p>