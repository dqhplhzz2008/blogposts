---
ID: 3109
post_title: >
  Altium
  Designer学习的一点总结（转）
post_name: 'altium-designer%e5%ad%a6%e4%b9%a0%e7%9a%84%e4%b8%80%e7%82%b9%e6%80%bb%e7%bb%93%ef%bc%88%e8%bd%ac%ef%bc%89'
author: 小奥
post_date: 2015-09-22 15:28:35
layout: post
link: >
  http://www.yushuai.me/2015/09/22/3109.html
published: true
tags:
  - Altium Designer
  - PCB
categories:
  - 工作与学习
---
Altium Designer 10 原理图中选中一个元件要怎么跳转到PCB中相应的位置呢？
第一步：将窗口调成平铺，让原理图和PCB图能在同一个窗口显示。
第二部：点窗口左下角PCB，再点PCB  Ispector
此时就可以使原理图与PCB图相互对应了。

如何将Altium Designer原理图转化为pdf文档?<!--more-->


点击file，下拉点击smart pdf
或者generate PDF


用Altium Designer 怎么由电路图导出器件清单？


在菜单 Report(报告）下拉点Bill of Materials可生成Excel格式的清单


在Altium designer 中画pcb布局时，怎样快速找到封装对应的原理图器件
经过我测试方法有下面几种：
1》在原理图文件中框选需要查找的封装元件，然后选择TOOLS-&gt;Select PCB Components，就可以找到PCB文件中对应的封装。
2》在altium design的Window菜单中选择tile vertically。然后在原理图文件中直接按T（或者在菜单选项中选择Tools),在出现的对话框中选择Cross Probe(鞭炮的形状，俗称鞭炮)，鼠标变成十字交叉状，选择某一元件即可。这样也可以找到PCB文件中对应的封装。




对应英文翻译
1. Column=Libref 元件名称
2. Column=Comment注释  规则说明
3. Column=Value 数量
4. Column=Quantity需求量
5. Column=Footprint封装
6. Column=Designator元件位置
7. Column=Description 类型

转自http://blog.csdn.net/kobesdu/article/details/12028567