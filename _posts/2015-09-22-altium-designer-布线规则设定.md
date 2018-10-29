---
ID: 3102
post_title: Altium Designer 布线规则设定
post_name: 'altium-designer-%e5%b8%83%e7%ba%bf%e8%a7%84%e5%88%99%e8%ae%be%e5%ae%9a'
author: 小奥
post_date: 2015-09-22 15:24:43
layout: post
link: >
  http://www.yushuai.me/2015/09/22/3102.html
published: true
tags:
  - Altium Designer，PCB
  - 电路设计
categories:
  - 个人作品
---
<strong>对于 PCB 的设计， Altium Designer  .0提供了详尽的 10 种不同的设计规则，这些设计规则则包括导线放置、导线布线方法、元件放置、布线规则、元件移动和信号完整性等规则。根据这些规则， Protel DXP 进行自动布局和自动布线。很大程度上，布线是否成功和布线的质量的高低取决于设计规则的合理性，也依赖于用户的设计经验。
对于具体的电路可以采用不同的设计规则，如果是设计双面板，很多规则可以采用系统默认值，系统默认值就是对双面板进行布线的设置。
本章将对 Altium Designer  .0的布线规则进行讲解。</strong><!--more-->

.1 设计规则设置
进入设计规则设置对话框的方法是在 PCB 电路板编辑环境下，从 Protel DXP 的主菜单中执行菜单命令 Desing/Rules ……，系统将弹出如图   — 1 所示的 PCB Rules and Constraints Editor(PCB 设计规则和约束 ) 对话框。
该对话框左侧显示的是设计规则的类型，共分 10 类。左边列出的是 Desing Rules( 设计规则 ) ，其中包括 Electrical （电气类型）、 Routing （布线类型）、 SMT （表面粘着元件类型）规则等等，右边则显示对应设计规则的设置属性。
该对话框左下角有按钮 Priorities ，单击该按钮，可以对同时存在的多个设计规则设置优先权的大小。
对这些设计规则的基本操作有：新建规则、删除规则、导出和导入规则等。可以在左边任一类规则上右击鼠标，将会弹出如图   — 2 所示的菜单。
在该设计规则菜单中， New Rule 是新建规则； Delete Rule 是删除规则； Export Rules 是将规则导出，将以 .rul 为后缀名导出到文件中； Import Rules 是从文件中导入规则； Report ……选项，将当前规则以报告文件的方式给出。 图   — 2 设计规则菜单
下面，将分别介绍各类设计规则的设置和使用方法。
.2 电气设计规则
Electrical （电气设计）规则是设置电路板在布线时必须遵守，包括安全距离、短路允许等 4 个小方面设置。
1 ． Clearance （安全距离）选项区域设置
安全距离设置的是 PCB 电路板在布置铜膜导线时，元件焊盘和焊盘之间、焊盘和导线之间、导线和导线之间的最小的距离。
下面以新建一个安全规则为例，简单介绍安全距离的设置方法。
（ 1 ）在 Clearance 上右击鼠标，从弹出的快捷菜单中选择 New Rule ……选项。
系统将自动当前设计规则为准，生成名为 Clearance_1 的新设计规则。
（ 2 ）在 Where the First object matches 选项区域中选定一种电气类型。在这里选定 Net 单选项，同时在下拉菜单中选择在设定的任一网络名。在右边 Full Query 中出现 InNet （ ）字样，其中括号里也会出现对应的网络名。
（ 3 ）同样的在 where the Second object matches 选项区域中也选定 Net 单选项，从下拉菜单中选择另外一个网络名。
（ 4 ）在 Constraints 选项区域中的 Minimum Clearance 文本框里输入 8mil 。这里 Mil 为英制单位， 1mil=10 -3 inch, linch= 2.54cm 。文中其他位置的 mil 也代表同样的长度单位。
（ 5 ）单击 Close 按钮，将退出设置，系统自动保存更改。
2 ． Short Circuit （短路）选项区域设置
短路设置就是否允许电路中有导线交叉短路。设置方法同上，系统默认不允许短路，即取消 Allow Short Circuit 复选项的选定3 ． Un-Routed Net （未布线网络）选项区域设置
可以指定网络、检查网络布线是否成功，如果不成功，将保持用飞线连接。
4 ． Un-connected Pin （未连接管脚）选项区域设置
对指定的网络检查是否所有元件管脚都连线了。
.3 布线设计规则
Routing （布线设计）规则主要有如下几种。
1 ． Width （导线宽度）选项区域设置
导线的宽度有三个值可以供设置，分别为 Max width （最大宽度）、 Preferred Width （最佳宽度）、 Min width （最小宽度）三个值，。系统对导线宽度的默认值为 10mil ，单击每个项直接输入数值进行更改。这里采用系统默认值 10mil 设置导线宽度。
2. Routing Topology （布线拓扑）选项区域设置
拓扑规则定义是采用的布线的拓扑逻辑约束。 Protel DXP 中常用的布线约束为统计最短逻辑规则，用户可以根据具体设计选择不同的布线拓扑规则。 Protel DXP 提供了以下几种布线拓扑规则。
◆ Shortest ( 最短 ) 规则设置
最短规则设置，从 Topology 下拉菜单中选择 Shortest 选项，该选项的定义是在布线时连接所有节点的连线最短规则。
◆ Horizontal （水平）规则设置
水平规则设置，从 Topoogy 下拉菜单中选择 Horizontal 选基。它采用连接节点的水平连线最短规则。
◆ Vertical （垂直）规则设置
垂直规则设置，从 Tolpoogy 下拉菜单中选择 Vertical 选项。它采和是连接所有节点，在垂直方向连线最短规则。
◆ Daisy Simple （简单雏菊）规则设置
简单雏菊规则设置，从 Tolpoogy 下拉菜单中选择 Daisy simple 选项。它采用的是使用链式连通法则，从一点到另一点连通所有的节点，并使连线最短。
◆ Daisy-MidDriven （雏菊中点）规则设置
雏菊中点规则设置，从 Tolpoogy 下拉菜单中选择 Daisy_MidDiven 选项。该规则选择一个 Source （源点），以它为中心向左右连通所有的节点，并使连线最短。
◆ Daisy Balanced （雏菊平衡）规则设置
雏菊平衡规则设置，从 Tolpoogy 下拉菜单中选择 Daisy Balanced 选项。它也选择一个源点，将所有的中间节点数目平均分成组，所有的组都连接在源点上，并使连线最短。
◆ Star Burst （星形）规则设置
星形规则设置，从 Tolpoogy 下拉菜单中选择 Star Burst 选项。该规则也是采用选择一个源点，以星形方式去连接别的节点，并使连线最短。
3. Routing Rriority （布线优先级别）选项区域设置
该规则用于设置布线的优先次序，设置的范围从 0~100 ，数值越大，优先级越高。
4. Routing Layers （布线图）选殴区域设置
该规则设置布线板导的导线走线方法。包括顶层和底层布线层，共有 32 个布线层可以设置。
图   — 1  布线层设置
由于设计的是双层板，故 Mid-Layer 1 到 Mid-Layer30 都不存在的，该选项为灰色不能使用，只能使用 Top Layer 和 Bottom Layer 两层。每层对应的右边为该层的布线走法。
Prote DXP 提供了 11 种布线走法。
各种布线方法为： Not Used 该层不进行布线； Horizontal 该层按水平方向布线 ;Vertical 该层为垂直方向布线； Any 该层可以任意方向布线； Clock 该层为按一点钟方向布线； Clock 该层为按两点钟方向布线； Clock 该层为按四点钟方向布线； Clock 该层为按五点钟方向布线； 45Up 该层为向上 45 °方向布线、 45Down 该层为向下 45 °方法布线； Fan Out 该层以扇形方式布线。
对于系统默认的双面板情况，一面布线采用 Horizontal 方式另一面采用 Vertical 方式。
5 ． Routing Corners （拐角）选项区域设置

布线的拐角可以有 45 °拐角、 90 °拐角和圆形拐角三种。
从 Style 上拉菜单栏中可以选择拐角的类型。etback 文本框用于设定拐角的长度。 To 文本框用于设置拐角的大小。
． Routing Via Style （导孔）选项区域设置
该规则设置用于设置布线中导孔的尺寸。

可以调协的参数有导孔的直径 via Diameter 和导孔中的通孔直径 Via Hole Size ，包括 Maximum （最大值）、 Minimum （最小值）和 Preferred （最佳值）。设置时需注意导孔直径和通孔直径的差值不宜过小，否则将不宜于制板加工。合适的差值在 10mil 以上。
.4 阻焊层设计规则
Mask （阻焊层设计）规则用于设置焊盘到阻焊层的距离，有如下几种规则。
1 ． Solder Mask Expansion （阻焊层延伸量）选项区域设置
该规则用于设计从焊盘到阻碍焊层之间的延伸距离。在电路板的制作时，阻焊层要预留一部分空间给焊盘。这个延伸量就是防止阻焊层和焊盘相重叠，如图   — 22 所示系统默认值为 4mil,Expansion 设置预为设置延伸量的大小。
图   — 22 阻焊层延伸量设置
2 ． Paste Mask Expansion （表面粘着元件延伸量）选项区域设置
该规则设置表面粘着元件的焊盘和焊锡层孔之间的距离，如图   — 23 所示，图中的 Expansion 设置项为设置延伸量的大小。
图   — 23 表面粘着元件延伸量设置
.5 内层设计规则
Plane （内层设计）规则用于多层板设计中，有如下几种设置规则。
1 ． Power Plane Connect Style （电源层连接方式）选项区域设置
电源层连接方式规则用于设置导孔到电源层的连接。
有 5 项设置项，分别是：
● Conner Style 下拉列表：用于设置电源层和导孔的连接风格。下拉列表中有 3 个选项可以选择： Relief Connect （发散状连接）、 Direct connect （直接连接）和 No Connect （不连接）。工程制板中多采用发散状连接风格。
● Condctor Width 文本框：用于设置导通的导线宽度。
● Conductors 复选项：用于选择连通的导线的数目，可以有 2 条或者 4 条导线供选择。
● Air-Gap 文本框：用于设置空隙的间隔的宽度。
● Expansion 文本框：用于设置从导孔到空隙的间隔之间的距离。
2. Power Plane Clearance （电源层安全距离）选项区域设置
该规则用于设置电源层与穿过它的导孔之间的安全距离，即防止导线短路的最小距离，系统默认值 20mil 。
3 ． Polygon Connect style （敷铜连接方式）选项区域设置
该规则用于设置多边形敷铜与焊盘之间的连接方式。
该设置对话框中 Connect Style 、 Conductors 和 Conductor width 的设置与 Power Plane Connect Style 选项设置意义相同，在此不同志赘述。
最后可以设定敷铜与焊盘之间的连接角度，有 90angle(90 ° ) 和 45Angle （ 45 °）角两种方式可选。
.  测试点设计规则
Testpiont （测试点设计）规则用于设计测试点的形状、用法等，有如下几项设置。
1 ． Testpoint Style （测试点风格）选项区域设置
该规则中可以指定测试点的大小和格点大小等。
该设置对话框有如下选项：
● Size 文本框为测试点的大小， Hole Size 文本框为测试点的导孔的大小，可以指定 Min （最小值）、 Max （最大值）和 Preferred （最优值）。
● Grid Size 文本框：用于设置测试点的网格大小。系统默认为 1mil 大小。
● Allow testpoint under component 复选项：用于选择是否允许将测试点放置在元件下面。复选项 Top 、 Bottom 等选择可以将测试点放置在哪些层面上。
右边多项复选项设置所允许的测试点的放置层和放置次序。系统默认为所有规则都选中。
2 ． Testpoint Usage （测试点用法）选项区域设置
置对话框有如下选项：
● Allow multiple testpoints on same net 复选项：用于设置是否可以在同一网络上允许多个测试点存在。
● Testpoint 选项区域中的单选项选择对测试点的处理，可以是 Required ( 必须处理 ) 、 Invalid （无效的测试点）和 Don't care （可忽略的测试点）。
.7 电路板制板规则
Manufacturing （电路板制板）规则用于对电路板制板的设置，有如下几类设置：
1. Minimum annular Ring （最小焊盘环宽）选项区域设置
电路板制作时的最小焊盘宽度，即焊盘外直径和导孔直径之间的有效期值，系统默认值为 10 mil 。
2 ． Acute Angle （导线夹角设置）选项区域设置
对于两条铜膜导线的交角，不小于 90 °。
3 ． Hole size （导孔直径设置）选项区域设置
该规则用于设置导孔的内直径大小。可以指定导孔的内直径的最大值和最小值。
Measurement Method 下拉列表中有两种选项： Absolute 以绝对尺寸来设计， Percent 以相对的比例来设计。采用绝对尺寸的导孔直径设置对话框（以 mil 为单位）。
4 ． Layers Pais （使用板层对）选项区域设置
在设计多层板时，如果使用了盲导孔，就要在这里对板层对进行设置。对话框中的复选取项用于选择是否允许使用板层对（ layers pairs ）设置。
小结
本章中，对 Protel DXP 提供的 10 种布线规则进行了介绍，在设计规则中介绍了每条规则的功能和设置方法。
这些规则的设置属于电路设计中的较高级的技巧，它设计到很多算法的知识。掌握这些规则的设置，就能设计出高质量的 PCB 电路。