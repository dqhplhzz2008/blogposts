---
ID: 4059
post_title: >
  C++ Primer
  Plus（第五版）第6章编程题答案
post_name: 'c-primer-plus%ef%bc%88%e7%ac%ac%e4%ba%94%e7%89%88%ef%bc%89%e7%ac%ac6%e7%ab%a0%e7%bc%96%e7%a8%8b%e9%a2%98%e7%ad%94%e6%a1%88'
author: 小奥
post_date: 2018-10-26 17:14:52
layout: post
link: >
  http://www.yushuai.me/2018/10/26/4059.html
published: true
tags:
  - C++
  - 代码
categories:
  - C/C++
---
第1题：
<pre class="lang:c++ decode:true " title="cppchapter51">//C++ Primer Plus Edition 5
//Chapter 6 Homework 1
#include&lt;iostream&gt;
#include&lt;cctype&gt;
using namespace std;
int main() {
	cout &lt;&lt; "Enter text for analysis and type @"
		"to terminate input.\n";
	char ch;
	cin.get(ch);
	while (ch != '@') {
		if (!isdigit(ch))
		{
			if (islower(ch))
				ch = toupper(ch);
			else if (isupper(ch))
				ch = tolower(ch);
			cout &lt;&lt; ch;

		}
		cin.get(ch);
	}

	system("pause");
	return 0;
}
//错误代码，判断如果是数字执行continue的话就会循环判断字符是不是等于@，第一个字符就无限循环。
//else同样。
//while (ch != '@') {
//	if (isdigit(ch))
//		continue;
//	else if (isalpha(ch))
//	{
//		cout &lt;&lt; ch &lt;&lt; endl;
//		if (islower(ch))
//			ch = toupper(ch);
//		else if (isupper(ch))
//			ch = tolower(ch);
//		cout &lt;&lt; ch;
//	}
//	else
//		continue;
//}</pre>
第2题：
<pre class="lang:c++ decode:true " title="cppchapter52">//C++ Primer Plus Edition 5
//Chapter 6 Homework 2
#include&lt;iostream&gt;
#include&lt;cctype&gt;
const int SIZE = 10;
using namespace std;
int main() {
	double donation[10];
	double average;
	int countbig = 0;
	int count=0;
	double sum = 0.0;
	cout &lt;&lt; "Enter 10 numbers.If you want to quit, just input @:" &lt;&lt; endl;
	for (int i = 0; i &lt; SIZE; i++) {
		cin &gt;&gt; donation[i];
		if (cin.fail())
			break;
		else {
			sum += donation[i];
			++count;
		}
	}
	average = sum / count;
	cout &lt;&lt; "The average number is: " &lt;&lt; average &lt;&lt; endl;
	for (int i = 0; i &lt; count; i++) {
		if (donation[i] &gt; average)
			++countbig;
	}
	cout &lt;&lt; countbig &lt;&lt; " numbers bigger than average.\n";
	
	system("pause");
	return 0;
}</pre>
第3题：
<pre class="lang:c++ decode:true " title="cppchapter53">//C++ Primer Plus Edition 5
//Chapter 6 Homework 3
#include&lt;iostream&gt;
#include&lt;cctype&gt;
using namespace std;
void showmenu();
int main() {
	showmenu();
	char choice;
	cin.get(choice);
	while ((choice != 'c') &amp;&amp; (choice != 'p') &amp;&amp; (choice != 't') &amp;&amp; (choice != 'g'))
	{
		cout &lt;&lt; "Please enter a c,p,t,g: ";
		//cin.get(choice);
		cin.ignore();
	}
	switch (choice)
	{
	case 'c':
		cout &lt;&lt; "This is carnivore's answer.\n";
		break;
	case 'p':
		cout &lt;&lt; "This is pianist's answer.\n";
		break;
	case 't':
		cout &lt;&lt; "A maple is a tree.\n";
		break;
	case 'g':
		cout &lt;&lt; "This is game's answer.\n";
		break;
	default:
		break;
	}
	system("pause");
	return 0;
}

void showmenu() {
	cout &lt;&lt; "Please enter one of the following choices.\n"
		"c)carnivore            p)pianist\n"
		"t)tree                 g)game\n";
}</pre>
第4题：
<pre class="lang:c++ decode:true " title="cppchapter54">//C++ Primer Plus Edition 5
//Chapter 6 Homework 4
#include&lt;iostream&gt;
#include&lt;cctype&gt;
using namespace std;
//函数
void showmenu();
void dis_by_name();
void dis_by_title();
void dis_by_bop();
void dis_by_pre();
//定义常量
const int strsize = 30;
const int NUM = 5;
//定义结构体
struct bop {
	char fullname[strsize];
	char title[strsize];
	char bopname[strsize];
	int preference;//0=fullname,1=title,2=bopname
};
bop people[5] = {
	{
		"Wimp Macho",
		"BOSS",
		"WM",
		0
	},
	{
		"Raki Rhodes",
		"Manager",
		"Junior Programmer",
		2
	},
	{
		"Celia Laiter",
		"MIPS",
		"CL",
		1
	},
	{
		"Hoppy Hipman",
		"Analyst Trainee",
		"AT",
		1
	},
	{
		"Pat Hand",
		"Student",
		"LOOPY",
		2
	}
};
char ch;
//开始主函数
int main() {
	showmenu();
	cin &gt;&gt; ch;
	while ((ch != 'a') &amp;&amp; (ch != 'b') &amp;&amp; (ch != 'c') &amp;&amp; (ch != 'd') &amp;&amp; (ch != 'q'))
	{
		showmenu();
		//cin.get(choice);
		cin.ignore();
	}
	while (ch != 'q') {
		switch (ch)
		{
		case 'a':
			dis_by_name();
			break;
		case 'b':
			dis_by_title();
			break;
		case 'c':
			dis_by_bop();
			break;
		case 'd':
			dis_by_pre();
			break;
		default:
			break;
		}
		cout &lt;&lt; "Next choice:" &lt;&lt; endl;
		cin &gt;&gt; ch;
		while ((ch != 'a') &amp;&amp; (ch != 'b') &amp;&amp; (ch != 'c') &amp;&amp; (ch != 'd') &amp;&amp; (ch != 'q'))
		{
			showmenu();
			//cin.get(choice);
			cin.ignore();
		}

	}
	cout &lt;&lt; "Bye!" &lt;&lt; endl;
	system("pause");
	return 0;
}

void showmenu() {
	cout &lt;&lt; "Please enter one of the following choices.\n"
		"a)display by name				b)display by title\n"
		"c)display by bopname			d)display by preference\n"
		"q)game\n";
}
void dis_by_name() {
	for (int i = 0; i &lt; NUM; ++i)
	{
		cout &lt;&lt; people[i].fullname &lt;&lt; endl;
	}
}
void dis_by_title() {
	for (int i = 0; i &lt; NUM; ++i)
	{
		cout &lt;&lt; people[i].title &lt;&lt; endl;
	}
}
void dis_by_bop() {
	for (int i = 0; i &lt; NUM; ++i)
	{
		cout &lt;&lt; people[i].bopname &lt;&lt; endl;
	}
}
void dis_by_pre() {
	for (int i = 0; i &lt; NUM; ++i) {
		if(people[i].preference==0)
			cout &lt;&lt; people[i].fullname &lt;&lt; endl;
		else if(people[i].preference==1)
			cout&lt;&lt; people[i].title &lt;&lt; endl;
		else
			cout &lt;&lt; people[i].bopname &lt;&lt; endl;
	}
}</pre>
第5题：
<pre class="lang:c++ decode:true " title="cppchapter55">//C++ Primer Plus Edition 5
//Chapter 6 Homework 5
#include&lt;iostream&gt;
const double level1 = 0.1;
const double level2 = 0.15;
const double level3 = 0.2;
using namespace std;
int main() {
	double tvarp;
	double cus;
	cout &lt;&lt; "Please input your money: ";
	cin &gt;&gt; tvarp;
	while (cin.good() &amp;&amp; (tvarp &gt; 0))
	{
		if (tvarp &lt;= 5000)
			cus = 0.0;
		else if (tvarp &gt; 5000 &amp;&amp; tvarp &lt;= 15000)
			cus = (tvarp - 5000)*level1;
		else if (tvarp &gt; 15000 &amp;&amp; tvarp &lt;= 35000)
			cus = 10000 * level1 + (tvarp - 15000)*level2;
		else if (tvarp &gt; 35000)
			cus = 10000 * level1 + 20000 * level2 + (tvarp - 35000)*level3;
		cout &lt;&lt; "您需要交税" &lt;&lt; cus &lt;&lt; " tvarp.\n";
		cout &lt;&lt; "Please input your money: ";
		cin &gt;&gt; tvarp;
	}
	cout &lt;&lt; "Bye\n";

	system("pause");
	return 0;
}</pre>
第6题：
<pre class="lang:c++ decode:true " title="cppchapter56">//C++ Primer Plus Edition 5
//Chapter 6 Homework 6
#include&lt;iostream&gt;
#include&lt;cctype&gt;
#include&lt;string&gt;
using namespace std;
struct donation
{
	string name;
	double money;

};
int main() {
	int num;
	int count = 0;
	cout &lt;&lt; "Please input the number of donationer: ";
	cin &gt;&gt; num;
	cin.get();//吃掉换行符
	donation *donaer = new donation[num];
	for (int i = 0; i &lt; num; i++)
	{
		cout &lt;&lt; "Enter the name: ";
		getline(cin, donaer[i].name);
		cout &lt;&lt; "Enter money: ";
		cin &gt;&gt; donaer[i].money;
		cin.get();//吃掉换行符
	}
	cout &lt;&lt; "****************************" &lt;&lt; endl;
	cout &lt;&lt; "Grand Patrons" &lt;&lt; endl;
	cout &lt;&lt; "****************************" &lt;&lt; endl;
	for (int i = 0; i &lt; num; i++) {
		if (donaer[i].money &gt; 10000) {
			++count;
			cout &lt;&lt; "Name: " &lt;&lt; donaer[i].name &lt;&lt; endl;
			cout &lt;&lt; "Donate Money: " &lt;&lt; donaer[i].money &lt;&lt; endl;
			cout &lt;&lt; endl;
		}
	}
	if (count == 0)
	{
		cout &lt;&lt; "None" &lt;&lt; endl;
	}
	count = 0;
	cout &lt;&lt; "****************************" &lt;&lt; endl;
	cout &lt;&lt; "Patrons" &lt;&lt; endl;
	cout &lt;&lt; "****************************" &lt;&lt; endl;
	for (int i = 0; i &lt; num; i++) {
		if (donaer[i].money &lt;= 10000) {
			++count;
			cout &lt;&lt; "Name: " &lt;&lt; donaer[i].name &lt;&lt; endl;
			cout &lt;&lt; "Donate Money: " &lt;&lt; donaer[i].money &lt;&lt; endl;
			cout &lt;&lt; endl;
		}
	}
	if (count == 0)
	{
		cout &lt;&lt; "None" &lt;&lt; endl;
	}
	delete[] donaer;
	system("pause");
	return 0;
}</pre>
第7题：
<pre class="lang:c++ decode:true " title="cppchapter57">//C++ Primer Plus Edition 5
//Chapter 6 Homework 7
#include&lt;iostream&gt;
#include&lt;cctype&gt;
#include&lt;string&gt;
using namespace std;
int main() {
	string word;
	char ch;
	int yuan = 0;
	int fu = 0;
	int others = 0;
	cin &gt;&gt; word;
	while (word != "q") {
		ch = word[0];
		if (isalpha(ch))
		{
			if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u'
				|| ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U')
				++yuan;
			else
				++fu;
		}
		else
			++others;
		cin &gt;&gt; word;
	}
	cout &lt;&lt; yuan &lt;&lt; " words beginning with vowels." &lt;&lt; endl;
	cout &lt;&lt; fu &lt;&lt; " words beginning with consonants." &lt;&lt; endl;
	cout &lt;&lt; others &lt;&lt; " others." &lt;&lt; endl;

	system("pause");
	return 0;
}</pre>
第8题：
<pre class="lang:c++ decode:true " title="cppchapter58">//C++ Primer Plus Edition 5
//Chapter 6 Homework 8
#include&lt;iostream&gt;
#include&lt;fstream&gt;
#include&lt;cstdlib&gt;
using namespace std;
const int MAXSIZE = 50;
int main() {
	char filename[MAXSIZE];
	ifstream inFile;
	cout &lt;&lt; "Please enter the file's name: ";
	cin.getline(filename, MAXSIZE);
	inFile.open(filename);
	if (!inFile.is_open()) {
		cout &lt;&lt; "Open this file error."&lt;&lt;endl;
		exit(EXIT_FAILURE);
	}
	char ch;
	int count = 0;
	inFile &gt;&gt; ch;
	while (inFile.good()) {
		++count;
		inFile &gt;&gt; ch;
	}
	if (inFile.eof()) {
		cout &lt;&lt; "Have reached end of this file.\n";
	}
	else if (inFile.fail()) {
		cout &lt;&lt; "Input terminated by data mismatch.\n";
	}
	else
		cout &lt;&lt; "unknown reason to stop.\n";
	if (count == 0) {
		cout &lt;&lt; "No data in this file.\n";
	}
	else {
		cout &lt;&lt; "There are " &lt;&lt; count &lt;&lt; " characters in this file.\n";
	}
	inFile.close();
	system("pause");
	return 0;
}</pre>
第9题：
<pre class="lang:c++ decode:true " title="cppchapter59">//C++ Primer Plus Edition 5
//Chapter 6 Homework 9
#include&lt;iostream&gt;
#include&lt;cctype&gt;
#include&lt;string&gt;
#include&lt;fstream&gt;
using namespace std;
const int MAXSIZE = 50;
struct donation
{
	string name;
	double money;

};
int main() {
	char filename[MAXSIZE];
	ifstream inFile;
	cout &lt;&lt; "Please enter the file's name: ";
	cin.getline(filename, MAXSIZE);
	inFile.open(filename);
	if (!inFile.is_open()) {
		cout &lt;&lt; "Open this file error." &lt;&lt; endl;
		exit(EXIT_FAILURE);
	}
	int num;
	int count = 0;
	inFile &gt;&gt; num;
	inFile.get();//吃掉换行符
	donation *donaer = new donation[num];
	for (int i = 0; i &lt; num; i++)
	{
		getline(inFile, donaer[i].name);
		inFile &gt;&gt; donaer[i].money;
		inFile.get();//吃掉换行符
	}
	cout &lt;&lt; "****************************" &lt;&lt; endl;
	cout &lt;&lt; "Grand Patrons" &lt;&lt; endl;
	cout &lt;&lt; "****************************" &lt;&lt; endl;
	for (int i = 0; i &lt; num; i++) {
		if (donaer[i].money &gt; 10000) {
			++count;
			cout &lt;&lt; "Name: " &lt;&lt; donaer[i].name &lt;&lt; endl;
			cout &lt;&lt; "Donate Money: " &lt;&lt; donaer[i].money &lt;&lt; endl;
			cout &lt;&lt; endl;
		}
	}
	if (count == 0)
	{
		cout &lt;&lt; "None" &lt;&lt; endl;
	}
	count = 0;
	cout &lt;&lt; "****************************" &lt;&lt; endl;
	cout &lt;&lt; "Patrons" &lt;&lt; endl;
	cout &lt;&lt; "****************************" &lt;&lt; endl;
	for (int i = 0; i &lt; num; i++) {
		if (donaer[i].money &lt;= 10000) {
			++count;
			cout &lt;&lt; "Name: " &lt;&lt; donaer[i].name &lt;&lt; endl;
			cout &lt;&lt; "Donate Money: " &lt;&lt; donaer[i].money &lt;&lt; endl;
			cout &lt;&lt; endl;
		}
	}
	if (count == 0)
	{
		cout &lt;&lt; "None" &lt;&lt; endl;
	}
	delete[] donaer;
	inFile.close();
	system("pause");
	return 0;
}</pre>
&nbsp;