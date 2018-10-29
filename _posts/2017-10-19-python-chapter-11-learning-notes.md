---
ID: 3501
post_title: Python chapter 11 learning notes
post_name: python-chapter-11-learning-notes
author: 小奥
post_date: 2017-10-19 22:50:02
layout: post
link: >
  http://www.yushuai.me/2017/10/19/3501.html
published: true
tags:
  - Python
  - python学习
categories:
  - Python
---
<ul style="margin-left:.375in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:微软雅黑;font-size:15px">测试</span></p></li><ul style="list-style-type: square;" class=" list-paddingleft-2"><li><p><span style="font-family:微软雅黑;font-size:15px">单元测试和测试用例</span></p></li></ul></ul><p style=";margin-left:.75in;font-family:微软雅黑;font-size:15px">单元测试：核实函数的某个方面没有问题；</p><p style=";margin-left:.75in;font-family:微软雅黑;font-size:15px">测试用例：一组单元测试，这些单元测试一起核实函数在各种情形下的行为都符合要求；</p><p style=";margin-left:.75in;font-family:微软雅黑;font-size:15px">全覆盖式测试用例包含一整套单元测试，涵盖了各种可能的函数使用方式。</p><ul style="margin-left:.75in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:微软雅黑;font-size:15px">可通过的测试</span></p></li></ul><p style=";margin-left:.75in;font-family:微软雅黑;font-size:15px">要为函数编写测试用例，可先导入模块unittest一级要测试的函数，再创建一个集成unittest.TestCase的类，并编写一系列方法对函数行为的不同方面进行测试。例如，</p><p style=";margin-left:.75in;font-family:&#39;Times New Roman&#39;;font-size:15px"><span style="font-style:italic"></span></p><pre class="brush:python;toolbar:false">import&nbsp;unittest
from&nbsp;name_function&nbsp;import&nbsp;get_formatted_name
&nbsp;
class&nbsp;NamesTestCase(unittest.TestCase):
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;测试name_function.py&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;test_first_last_name(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;formatted_name&nbsp;=&nbsp;get_formatted_name(&#39;janis&#39;,&nbsp;&#39;joplin&#39;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.assertEqual(formatted_name,&nbsp;&#39;Janis&nbsp;Joplin&#39;)
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;test_first_middle_last_name(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;能够正确处理像wolfgang&nbsp;amadeus&nbsp;mozart这样的名字吗&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;formatted_name&nbsp;=&nbsp;get_formatted_name(&#39;wolfgang&#39;,&#39;mozart&#39;,&#39;amadeus&#39;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.assertEqual(formatted_name,&nbsp;&#39;Wolfgang&nbsp;Amadeus&nbsp;Mozart&#39;)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
unittest.main()</pre><p style=";margin-left:.75in;font-family:&#39;Times New Roman&#39;;font-size:15px"><span style="font-style:italic"></span><br/></p><ul style="margin-left:.375in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:微软雅黑;font-size:15px">测试类</span></p></li><ul style="list-style-type: square;" class=" list-paddingleft-2"><li><p><span style="font-family:微软雅黑;font-size:15px">各种断言方法</span></p></li></ul></ul><table valign="top"><tbody><tr class="firstRow"><td style="border-color: rgb(163, 163, 163); border-width: 1px; background-color: black; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px;color:white"><span style="font-weight:bold">方法</span></p></td><td style="border-color: rgb(163, 163, 163); border-width: 1px; background-color: black; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px;color:white"><span style="font-weight:bold">用途</span></p></td></tr><tr><td style="border-color: rgb(163, 163, 163); border-width: 1px; background-color: white; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px"><span style="font-weight:bold">assertEqual(a,b)</span></p></td><td style="border-color: rgb(163, 163, 163); border-width: 1px; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px">判断a，b是否相等</p></td></tr><tr><td style="border-color: rgb(163, 163, 163); border-width: 1px; background-color: white; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px"><span style="font-weight:bold">assertNotEqual(a,b)</span></p></td><td style="border-color: rgb(163, 163, 163); border-width: 1px; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px">判断a，b是否不相等</p></td></tr><tr><td style="border-color: rgb(163, 163, 163); border-width: 1px; background-color: white; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px"><span style="font-weight:bold">assertTure(x)</span></p></td><td style="border-color: rgb(163, 163, 163); border-width: 1px; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px">判断x为真</p></td></tr><tr><td style="border-color: rgb(163, 163, 163); border-width: 1px; background-color: white; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px"><span style="font-weight:bold">assertFalse(x)</span></p></td><td style="border-color: rgb(163, 163, 163); border-width: 1px; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px">判断x为假</p></td></tr><tr><td style="border-color: rgb(163, 163, 163); border-width: 1px; background-color: white; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px"><span style="font-weight:bold">assertIn(item, list)</span></p></td><td style="border-color: rgb(163, 163, 163); border-width: 1px; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px">判断item在list里面</p></td></tr><tr><td style="border-color: rgb(163, 163, 163); border-width: 1px; background-color: white; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px"><span style="font-weight:bold">assertNotIn(item,list)</span></p></td><td style="border-color: rgb(163, 163, 163); border-width: 1px; vertical-align: top; padding: 5px;" width="1"><p style=";font-family:等线;font-size:14px">判断item不在list里面</p></td></tr></tbody></table><ul style="margin-left:.75in;direction:ltr;unicode-bidi:embed" class=" list-paddingleft-2"><li><p><span style="font-family:微软雅黑;font-size:15px">使用</span><span style="font-family:微软雅黑;font-size:15px">setUp()</span></p></li></ul><pre class="brush:python;toolbar:false">import&nbsp;unittest
from&nbsp;survey&nbsp;import&nbsp;AnonymousSurvey
&nbsp;
class&nbsp;TestAnonmyousSurvey(unittest.TestCase):
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;针对类的测试&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;setUp(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;创建一个调查对象和一组答案，供使用的测试方法使用&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;question&nbsp;=&nbsp;&quot;What&nbsp;language&nbsp;did&nbsp;you&nbsp;first&nbsp;learn&nbsp;to&nbsp;speak?&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.my_survey&nbsp;=&nbsp;AnonymousSurvey(question)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.responses&nbsp;=&nbsp;[&#39;English&#39;,&nbsp;&#39;Chinese&#39;,&nbsp;&#39;Japanese&#39;]
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;test_store_single_respose(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.my_survey.store_response(self.responses[0])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.assertIn(self.responses[0],&nbsp;self.my_survey.responses)
&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;def&nbsp;test_store_three_respose(self):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for&nbsp;response&nbsp;in&nbsp;self.responses:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.my_survey.store_response(response)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for&nbsp;response&nbsp;in&nbsp;self.responses:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.assertIn(response,&nbsp;self.my_survey.responses)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
unittest.main()</pre><p><br/></p>