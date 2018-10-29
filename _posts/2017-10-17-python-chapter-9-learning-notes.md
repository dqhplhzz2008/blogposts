---
ID: 3485
post_title: Python chapter 9 learning notes
post_name: python-chapter-9-learning-notes
author: 小奥
post_date: 2017-10-17 23:30:39
layout: post
link: >
  http://www.yushuai.me/2017/10/17/3485.html
published: true
tags:
  - Python
  - python学习
categories:
  - Python
---
<p style="margin-left:63px;vertical-align:middle"><span style="font-size:13px;font-family:Symbol">·</span><span style="font-size:15px;font-family:&#39;Times New Roman&#39;,serif">CLASS</span></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif">For example,</span></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><em><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif"></span></em></p><pre class="brush:python;toolbar:false">class&nbsp;Restaurant():
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;__init__(self,&nbsp;restaurant_name,&nbsp;cuisine_type):#DO&nbsp;NOT&nbsp;FORGET&nbsp;__init__
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.name&nbsp;=&nbsp;restaurant_name
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.type&nbsp;=&nbsp;cuisine_type
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;describe_restaurant(self):#DO&nbsp;NOT&nbsp;FORGET&nbsp;self
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;This&nbsp;restaurant&#39;s&nbsp;name&nbsp;is&nbsp;&quot;&nbsp;+&nbsp;self.name&nbsp;+&nbsp;&quot;.&quot;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;This&nbsp;restaurant&#39;s&nbsp;cuisine&nbsp;type&nbsp;is&quot;&nbsp;+&nbsp;self.type&nbsp;+&nbsp;&quot;.&quot;)
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;open_restaurant(self):#DO&nbsp;NOT&nbsp;FORGET&nbsp;self
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;This&nbsp;restaurant&nbsp;is&nbsp;opening.&quot;)
&nbsp;
op_rest&nbsp;=&nbsp;Restaurant(&quot;Chinese&nbsp;Restaurant&quot;,&nbsp;&quot;LUCAI&quot;)
op_rest.describe_restaurant()
op_rest.open_restaurant()</pre><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><em><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif"></span></em><br/></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif">&nbsp;</span></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif">This is a good example to show how to use CLASS in python.</span></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif">Just add some sentences as followed, that shows some ways to modify elements.</span></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><em><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif"></span></em></p><pre class="brush:python;toolbar:false">class&nbsp;Car():
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;__init__(self,&nbsp;make,&nbsp;model,&nbsp;year):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;初始化描述汽车的属性&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.make&nbsp;=&nbsp;make
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.model&nbsp;=&nbsp;model
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.year&nbsp;=&nbsp;year
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.odometer_reading&nbsp;=&nbsp;100
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;get_descriptive_name(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;long_name&nbsp;=&nbsp;str(self.year)&nbsp;+&nbsp;&#39;&nbsp;&#39;&nbsp;+&nbsp;self.make&nbsp;+&nbsp;&#39;&nbsp;&#39;&nbsp;+&nbsp;self.model
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return&nbsp;long_name.title()
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;read_odometer(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;This&nbsp;car&nbsp;has&nbsp;&quot;&nbsp;+&nbsp;str(self.odometer_reading)&nbsp;+&nbsp;&quot;&nbsp;miles&nbsp;on&nbsp;it.&quot;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;update_odometer(self,&nbsp;mileage):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;mileage&nbsp;&gt;=&nbsp;self.odometer_reading:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.odometer_reading&nbsp;=&nbsp;mileage
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;else:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;Forrbideen&quot;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;increment_odometer(self,&nbsp;miles):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.odometer_reading&nbsp;+=&nbsp;miles
&nbsp;&nbsp;&nbsp;&nbsp;
my_car&nbsp;=&nbsp;Car(&#39;Toyota&#39;,&nbsp;&#39;GO9&#39;,&nbsp;2017)
print(my_car.get_descriptive_name())
#my_car.odometer_reading&nbsp;=&nbsp;100&nbsp;#Direct&nbsp;assignment
you&nbsp;=&nbsp;input(&quot;Please&nbsp;input&nbsp;the&nbsp;miles.\n&quot;)
you&nbsp;=&nbsp;int(you)
#my_car.update_odometer(you)&nbsp;#Modify&nbsp;value&nbsp;by&nbsp;method
my_car.increment_odometer(you)&nbsp;#Adding&nbsp;by&nbsp;method
my_car.read_odometer()</pre><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><em><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif"></span></em><br/></p><p style="margin-left:63px;vertical-align:middle"><span style="font-size:13px;font-family:Symbol">·<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span style="font-size:15px;font-family:&#39;Times New Roman&#39;,serif">Inheritance</span></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><em><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif"></span></em></p><pre class="brush:python;toolbar:false">class&nbsp;Car():
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;__init__(self,&nbsp;make,&nbsp;model,&nbsp;year):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;初始化描述汽车的属性&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.make&nbsp;=&nbsp;make
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.model&nbsp;=&nbsp;model
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.year&nbsp;=&nbsp;year
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;get_descriptive_name(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;long_name&nbsp;=&nbsp;str(self.year)&nbsp;+&nbsp;&#39;&nbsp;&#39;&nbsp;+&nbsp;self.make&nbsp;+&nbsp;&#39;&nbsp;&#39;&nbsp;+&nbsp;self.model
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return&nbsp;long_name.title()
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;fill_gas_tank(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;ONLY&nbsp;ONE&quot;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
class&nbsp;ElectricCar(Car):&nbsp;#Define&nbsp;Inheritance
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;电动汽车的独特之处&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;__init__(self,&nbsp;make,&nbsp;model,&nbsp;year):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;super().__init__(make,&nbsp;model,&nbsp;year)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.battery_size&nbsp;=&nbsp;70&nbsp;#Adding&nbsp;a&nbsp;property
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;describe_battery(self):&nbsp;#Adding&nbsp;a&nbsp;method
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;打印一条描述电瓶容量的信息&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;This&nbsp;car&nbsp;has&nbsp;a&nbsp;&quot;&nbsp;+&nbsp;str(self.battery_size)&nbsp;+&nbsp;&quot;-KWh&nbsp;battery.&quot;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;fill_gas_tank(self):#If&nbsp;the&nbsp;parent&nbsp;class&nbsp;has&nbsp;something&nbsp;that&nbsp;it&nbsp;do&nbsp;not&nbsp;need,&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;#just&nbsp;define&nbsp;a&nbsp;method&nbsp;and&nbsp;overwriting.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;This&nbsp;car&nbsp;doesn&#39;t&nbsp;need&nbsp;a&nbsp;gas&nbsp;tank!&quot;)
&nbsp;
my_tesla&nbsp;=&nbsp;ElectricCar(&#39;tesla&#39;,&nbsp;&#39;model&nbsp;s&#39;,&nbsp;2017)
print(my_tesla.get_descriptive_name())
my_tesla.describe_battery()
my_tesla.fill_gas_tank()</pre><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:63px;margin-bottom:0"><em><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif"></span></em><br/></p><p style="margin-left:99px;vertical-align:middle"><span style="font-size:13px;font-family:&#39;Courier New&#39;">o<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp;&nbsp; </span></span><span style="font-size:15px;font-family:&#39;Times New Roman&#39;,serif">In order to make codes more beautiful,put some properties that only electricCar has into a new class.</span></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:99px;margin-bottom:0"><em><span style="font-size:15px;font-family: &#39;Times New Roman&#39;,serif"></span></em></p><pre class="brush:python;toolbar:false">class&nbsp;Car():
--snip--
&nbsp;
class&nbsp;Battery():&nbsp;#A&nbsp;new&nbsp;class,&nbsp;and&nbsp;not&nbsp;belong&nbsp;to&nbsp;class&nbsp;Car.
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;一次模拟电动汽车电瓶的简单尝试&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;__init__(self,&nbsp;battery_size=70):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;初始化电瓶的属性&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.battery_size&nbsp;=&nbsp;battery_size
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;describe_battery(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;打印一条描述电瓶容量的消息&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;This&nbsp;car&nbsp;has&nbsp;a&nbsp;&quot;&nbsp;+&nbsp;str(self.battery_size)&nbsp;+&nbsp;&quot;-kWh&nbsp;battery.&quot;)
&nbsp;
class&nbsp;ElectricCar(Car):
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;电动汽车的独特之处&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;__init__(self,&nbsp;make,&nbsp;model,&nbsp;year):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;初始化父类的属性，再初始化电动汽车特有的属性
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;super().__init__(make,&nbsp;model,&nbsp;year)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.battery&nbsp;=&nbsp;Battery()
&nbsp;
my_tesla&nbsp;=&nbsp;ElectricCar(&#39;tesla&#39;,&nbsp;&#39;model&nbsp;s&#39;,&nbsp;2016)
print(my_tesla.get_descriptive_name())
my_tesla.battery.describe_battery()#可以直接用my_tesla.来调用battery（）里面的方法</pre><ul style="margin-left:.375in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:&#39;Times New Roman&#39;;font-size:15px">Import Class:</span></p></li><ul style="list-style-type: square;" class=" list-paddingleft-2"><li><p><span style="font-family:&#39;Times New Roman&#39;;font-size:15px">Import &nbsp; &nbsp; &nbsp; single class</span></p></li></ul></ul><p style=";margin-left:.75in;font-size:15px"><span style="font-style:italic;font-family:&#39;Times New Roman&#39;"></span></p><pre class="brush:python;toolbar:false">#外面有一个car.py文件，里面有一个Car类
from&nbsp;car&nbsp;import&nbsp;Car
&nbsp;
my_new_car&nbsp;=&nbsp;Car(&#39;audi&#39;,&nbsp;&#39;a4&#39;,&nbsp;2016)
print(my_new_car.get_descriptive_name())
my_new_car.odometer_reading&nbsp;=&nbsp;23
my_new_car.read_odometer()</pre><ul style="margin-left:.75in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:&#39;Times New Roman&#39;;font-size:15px">Import M</span><span style="font-family:&#39;Times New Roman&#39;;font-size:15px">any class in one module</span></p></li></ul><p style=";margin-left:.75in;font-family:微软雅黑;font-size:15px"><span style="font-style:italic"></span></p><pre class="brush:python;toolbar:false">#外面有一个car.py文件，里面有多个类，Car类，ElectricCar类
from&nbsp;car&nbsp;import&nbsp;ElectricCar
&nbsp;
my_tesla&nbsp;=&nbsp;ElectricCar(&#39;tesla&#39;,&nbsp;&#39;model&nbsp;s&#39;,&nbsp;2016)
print(my_tesla.get_descriptive_name())
my_tesla.battery.describe_battery()
my_tesla.battery.get_range()</pre><p style=";margin-left:.75in;font-family:&#39;Times New Roman&#39;;font-size:15px"><span style="font-style:italic"></span><br/></p><ul style="margin-left:.75in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:&#39;Times New Roman&#39;;font-size:15px">Import many class &nbsp; &nbsp; &nbsp;from only one module</span></p></li></ul><p style=";margin-left:.75in;font-family:&#39;Times New Roman&#39;;font-size:15px"><span style="font-style:italic"></span></p><pre class="brush:python;toolbar:false">from&nbsp;car&nbsp;import&nbsp;Car,&nbsp;ElectricCar
&nbsp;
my_beetle&nbsp;=&nbsp;Car(&#39;volkswagen&#39;,&nbsp;&#39;beetle&#39;,&nbsp;2016)
print(my_beetle.get_descriptive_name())
my_tesla&nbsp;=&nbsp;ElectricCar(&#39;tesla&#39;,&nbsp;&#39;roadster&#39;,&nbsp;2016)
print(my_tesla.get_descriptive_name())</pre><p style=";margin-left:.75in;font-family:&#39;Times New Roman&#39;;font-size:15px"><span style="font-style:italic"></span><br/></p><ul style="margin-left:.75in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:&#39;Times New Roman&#39;;font-size:15px">Import all &nbsp; &nbsp; &nbsp;module<span style="font-family: &quot;Times New Roman&quot;; font-size: 15px; color: #FF0000;"><strong>[RECOMMEND]</strong></span></span></p></li></ul><p style=";margin-left:.75in;font-family:微软雅黑;font-size:15px"><span style="font-style:italic"></span></p><pre class="brush:python;toolbar:false">#外面有一个car.py文件，里面有多个类
import&nbsp;car
&nbsp;
my_beetle&nbsp;=&nbsp;car.Car(&#39;volkswagen&#39;,&nbsp;&#39;beetle&#39;,&nbsp;2016)
print(my_beetle.get_descriptive_name())
my_tesla&nbsp;=&nbsp;car.ElectricCar(&#39;tesla&#39;,&nbsp;&#39;roadster&#39;,&nbsp;2016)
print(my_tesla.get_descriptive_name())</pre><p style=";margin-left:.75in;font-family:&#39;Times New Roman&#39;;font-size:15px"><span style="font-style:italic"></span><br/></p><ul style="margin-left:.75in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:&#39;Times New Roman&#39;;font-size:15px">Import all class &nbsp; &nbsp; &nbsp;from module<strong>[NOT RECOMMEND]</strong></span></p></li></ul><pre class="brush:python;toolbar:false">from&nbsp;module_name&nbsp;import&nbsp;*</pre><p style=";margin-left:.75in;font-family:&#39;Times New Roman&#39;;font-size:15px"><span style="font-style:italic"></span><br/></p><p style=";margin-left:.75in;font-family:&#39;Times New Roman&#39;;font-size:15px"><span style="font-style:italic"></span><br/></p><p style="margin-top:0;margin-right:0;margin-bottom:0;margin-left:99px;margin-bottom:0"><br/></p>