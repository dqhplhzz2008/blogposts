---
ID: 3105
post_title: >
  altium
  designer常用元件电气符号和封装形式（转）
post_name: 'altium-designer%e5%b8%b8%e7%94%a8%e5%85%83%e4%bb%b6%e7%94%b5%e6%b0%94%e7%ac%a6%e5%8f%b7%e5%92%8c%e5%b0%81%e8%a3%85%e5%bd%a2%e5%bc%8f%ef%bc%88%e8%bd%ac%ef%bc%89'
author: 小奥
post_date: 2015-09-22 15:26:13
layout: post
link: >
  http://www.yushuai.me/2015/09/22/3105.html
published: true
tags:
  - Altium Designer，PCB
categories:
  - 工作与学习
---
<span style="font-size: large;">1. 标准电阻：RES1、RES2；封装：AXIAL-0.3到AXIAL-1.0


两端口可变电阻：RES3、RES4；封装：AXIAL-0.3到AXIAL-1.0
三端口可变电阻：RESISTOR TAPPED，POT1，POT2；封装：VR1-VR5
2.电容：CAP（无极性电容）、ELECTRO1或ELECTRO2（极性电容）、可变电容CAPVAR


封装：无极性电容为RAD-0.1到RAD-0.4，有极性电容为RB.2/.4到RB.5/1.0.


3.二极管：DIODE（普通二极管）、DIODE SCHOTTKY（肖特基二极管）、DUIDE TUNNEL（隧道二极管）DIODE VARCTOR（变容二极管）ZENER1~3（稳压二极管）


封装：DIODE0.4和DIODE 0.7;（上面已经说了，注意做PCB时别忘了将封装DIODE的端口改为A、K）


4.三极管：NPN，NPN1和PNP，PNP1；引脚封装：TO18、TO92A（普通三极管）TO220H（大功率三极管）TO3（大功率达林顿管）


以上的封装为三角形结构。T0-226为直线形，我们常用的9013、9014管脚排列是直线型的，所以一般三极管都采用TO-126啦！


5、效应管：JFETN（N沟道结型场效应管），JFETP（P沟道结型场效应管）MOSFETN（N沟道增强型管）MOSFETP（P沟道增强型管）


引脚封装形式与三极管同。


6、电感：INDUCTOR、INDUCTOR1、INDUCTOR2（普通电感），INDUCTOR VAR、INDUCTOR3、INDUCTOR4（可变电感）


8.整流桥原理图中常用的名称为BRIDGE1和BRIDGE2，引脚封装形式为D系列，如D-44，D-37，D-46等。


9.单排多针插座原理图中常用的名称为CON系列，从CON1到CON60，引脚封装形式为SIP系列，从SIP-2到SIP-20。


10.双列直插元件原理图中常用的名称为根据功能的不同而不同，引脚封装形式DIP系列，


不如40管脚的单片机封装为DIP40。


11.串并口类原理图中常用的名称为DB系列，引脚封装形式为DB和MD系列。


12、晶体振荡器：CRYSTAL；封装：XTAL1


13、发光二极管：LED；封装可以才用电容的封装。（RAD0.1-0.4）


14、发光数码管：DPY；至于封装嘛，建议自己做！


15、拨动开关：SW DIP；封装就需要自己量一下管脚距离来做！


16、按键开关：SW-PB：封装同上，也需要自己做。


17、变压器：TRANS1——TRANS5；</span> <!--more-->