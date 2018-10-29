---
ID: 4003
post_title: >
  在 Linux 下使用 CMake
  构建应用程序
post_name: '%e5%9c%a8-linux-%e4%b8%8b%e4%bd%bf%e7%94%a8-cmake-%e6%9e%84%e5%bb%ba%e5%ba%94%e7%94%a8%e7%a8%8b%e5%ba%8f'
author: 小奥
post_date: 2018-10-11 22:02:19
layout: post
link: >
  http://www.yushuai.me/2018/10/11/4003.html
published: true
tags:
  - cmake
  - linux
categories:
  - Linux
---
<h2 id="1CMake简介outline" class="ibm-h2">CMake 简介</h2>
CMake 是一个跨平台的自动化建构系统,它使用一个名为 CMakeLists.txt 的文件来描述构建过程,可以产生标准的构建文件,如 Unix 的 Makefile 或Windows Visual C++ 的 projects/workspaces 。文件 CMakeLists.txt 需要手工编写,也可以通过编写脚本进行半自动的生成。CMake 提供了比 autoconfig 更简洁的语法。在 linux 平台下使用 CMake 生成 Makefile 并编译的流程如下：
<blockquote>1.编写 CmakeLists.txt。
2.执行命令“cmake PATH”或者“ccmake PATH”生成 Makefile ( PATH 是 CMakeLists.txt 所在的目录 )。
3.使用 make 命令进行编译。</blockquote>
<h2>第一个工程</h2>
现假设我们的项目中只有一个源文件 main.cpp

<strong>清单 1 源文件 main.cpp</strong>
<blockquote>#include&lt;iostream&gt;
using namespace std;
int main()
{
cout&lt;&lt;"Hello word!"&lt;&lt;std::endl;
return 0;
}</blockquote>
为了构建该项目,我们需要编写文件 CMakeLists.txt 并将其与 main.cpp 放在 同一个目录下:

<strong>清单 2 CMakeLists.txt</strong>
<blockquote>PROJECT(main)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
AUX_SOURCE_DIRECTORY(. DIR_SRCS)
ADD_EXECUTABLE(main ${DIR_SRCS})</blockquote>
&nbsp;

CMakeLists.txt 的语法比较简单,由命令、注释和空格组成,其中命令是不区分大小写的,符号"#"后面的内容被认为是注释。命令由命令名称、小括号和参数组成,参数之间使用空格进行间隔。例如对于清单2的 CMakeLists.txt 文件:第一行是一条命令,名称是 PROJECT ,参数是 main ,该命令表示项目的名称是 main 。第二行的命令限定了 CMake 的版本。第三行使用命令 AUX_SOURCE_DIRECTORY 将当前目录中的源文件名称赋值给变量 DIR_SRCS 。 CMake 手册中对命令 AUX_SOURCE_DIRECTORY 的描述如下:
<blockquote>aux_source_directory(&lt;dir&gt; &lt;variable&gt;)</blockquote>
该命令会把参数 &lt;dir&gt; 中所有的源文件名称赋值给参数 &lt;variable&gt; 。 第四行使用命令 ADD_EXECUTABLE 指示变量 DIR_SRCS 中的源文件需要编译 成一个名称为 main 的可执行文件。

完成了文件 CMakeLists.txt 的编写后需要使用 cmake 或 ccmake 命令生成Makefile 。 ccmake 与命令 cmake 的不同之处在于 ccmake 提供了一个图形化的操作界面。cmake 命令的执行方式如下:
<blockquote>cmake [options] &lt;path-to-source&gt;</blockquote>
这里我们进入了 main.cpp 所在的目录后执行 “<strong>cmake .</strong>” 后就可以得到 Makefile 并使用 <strong>make</strong> 进行编译,如下图所示。

<img class="aligncenter size-large" src="https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/images/simple.JPG" width="469" height="278" />
<h2>处理多源文件目录的方法</h2>
CMake 处理源代码分布在不同目录中的情况也十分简单。现假设我们的源代码分布情况如下:

<strong>图 2. 源代码分布情况</strong>

<img class="size-large aligncenter" src="https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/images/step2-files.JPG" width="276" height="203" />

其中 src 目录下的文件要编译成一个链接库。

<strong>第一步，项目主目录中的 CMakeLists.txt</strong>
在目录 step2 中创建文件 CMakeLists.txt 。文件内容如下:
<h5 id="N100EA" class="ibm-h5">清单 3 目录 step2 中的 CMakeLists.txt</h5>
<blockquote>PROJECT(main)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
ADD_SUBDIRECTORY( src )
AUX_SOURCE_DIRECTORY(. DIR_SRCS)
ADD_EXECUTABLE(main ${DIR_SRCS} )
TARGET_LINK_LIBRARIES( main Test )</blockquote>
相对于清单 2，该文件添加了下面的内容: 第三行，使用命令 ADD_SUBDIRECTORY 指明本项目包含一个子目录 src 。第六行，使用命令 TARGET_LINK_LIBRARIES 指明可执行文件 main 需要连接一个名为Test的链接库 。

<strong>第二步，子目录中的 CmakeLists.txt</strong>

在子目录 src 中创建 CmakeLists.txt。文件内容如下:

<strong>清单 4. 目录 src 中的 CmakeLists.txt</strong>
<blockquote>AUX_SOURCE_DIRECTORY(. DIR_TEST1_SRCS)
ADD_LIBRARY ( Test ${DIR_TEST1_SRCS})</blockquote>
在该文件中使用命令 ADD_LIBRARY 将 src 目录中的源文件编译为共享库。

<strong>第三步，执行 cmake</strong>
至此我们完成了项目中所有 CMakeLists.txt 文件的编写,进入目录 step2 中依次执行命令 “<strong>cmake .</strong>” 和 “<strong>make</strong>” 得到结果如下:

<img class="aligncenter size-large" src="https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/images/step2.JPG" width="474" height="285" />

在执行 cmake 的过程中,首先解析目录 step2 中的 CMakeLists.txt ,当程序执行命令 ADD_SUBDIRECTORY( src ) 时进入目录 src 对其中的 CMakeLists.txt 进行解析。
<h2>在工程中查找并使用其他程序库的方法</h2>
在开发软件的时候我们会用到一些函数库,这些函数库在不同的系统中安装的位置可能不同,编译的时候需要首先找到这些软件包的头文件以及链接库所在的目录以便生成编译选项。例如一个需要使用博克利数据库项目,需要头文件db_cxx.h 和链接库 libdb_cxx.so ,现在该项目中有一个源代码文件 main.cpp ，放在项目的根目录中。

<strong>第一步，程序库说明文件</strong>

在项目的根目录中创建目录 cmake/modules/ ，在 cmake/modules/ 下创建文件 Findlibdb_cxx.cmake ，内容如下：

<strong>清单 5. 文件 Findlibdb_cxx.cmake</strong>
<blockquote>MESSAGE(STATUS "Using bundled Findlibdb.cmake...")
FIND_PATH(
LIBDB_CXX_INCLUDE_DIR
db_cxx.h
/usr/include/
/usr/local/include/
)
FIND_LIBRARY(
LIBDB_CXX_LIBRARIES NAMES db_cxx
PATHS /usr/lib/ /usr/local/lib/
)</blockquote>
文件 Findlibdb_cxx.cmake 的命名要符合规范: FindlibNAME.cmake ,其中NAME 是函数库的名称。Findlibdb_cxx.cmake 的语法与 CMakeLists.txt 相同。这里使用了三个命令： MESSAGE ， FIND_PATH 和 FIND_LIBRARY 。

命令 MESSAGE 会将参数的内容输出到终端。

命令 FIND_PATH 指明头文件查找的路径，原型如下：

find_path(&lt;VAR&gt; name1 [path1 path2 ...]) 该命令在参数 path* 指示的目录中查找文件 name1 并将查找到的路径保存在变量 VAR 中。清单5第3－8行的意思是在 /usr/include/ 和 /usr/local/include/ 中查找文件db_cxx.h ,并将db_cxx.h 所在的路径保存在 LIBDB_CXX_INCLUDE_DIR中。

命令 FIND_LIBRARY 同 FIND_PATH 类似,用于查找链接库并将结果保存在变量中。清单5第10－13行的意思是在目录 /usr/lib/ 和 /usr/local/lib/ 中寻找名称为 db_cxx 的链接库,并将结果保存在 LIBDB_CXX_LIBRARIES。

<strong>第二步, 项目的根目录中的 CmakeList.txt</strong>

在项目的根目录中创建 CmakeList.txt ：

清单 6. 可以查找链接库的 CMakeList.txt
<blockquote>PROJECT(main)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
SET(CMAKE_SOURCE_DIR .)
SET(CMAKE_MODULE_PATH ${CMAKE_ROOT}/Modules ${CMAKE_SOURCE_DIR}/cmake/modules)
AUX_SOURCE_DIRECTORY(. DIR_SRCS)
ADD_EXECUTABLE(main ${DIR_SRCS})
FIND_PACKAGE( libdb_cxx REQUIRED)
MARK_AS_ADVANCED(
LIBDB_CXX_INCLUDE_DIR
LIBDB_CXX_LIBRARIES
)
IF (LIBDB_CXX_INCLUDE_DIR AND LIBDB_CXX_LIBRARIES)
MESSAGE(STATUS "Found libdb libraries")
INCLUDE_DIRECTORIES(${LIBDB_CXX_INCLUDE_DIR})
MESSAGE( ${LIBDB_CXX_LIBRARIES} )
TARGET_LINK_LIBRARIES(main ${LIBDB_CXX_LIBRARIES}18 )
ENDIF (LIBDB_CXX_INCLUDE_DIR AND LIBDB_CXX_LIBRARIES)</blockquote>
在该文件中第4行表示到目录 ./cmake/modules 中查找 Findlibdb_cxx.cmake ,8-19 行表示查找链接库和头文件的过程。第8行使用命令 FIND_PACKAGE 进行查找,这条命令执行后 CMake 会到变量 CMAKE_MODULE_PATH 指示的目录中查找文件 Findlibdb_cxx.cmake 并执行。第13-19行是条件判断语句,表示如果 LIBDB_CXX_INCLUDE_DIR 和 LIBDB_CXX_LIBRARIES 都已经被赋值,则设置编译时到 LIBDB_CXX_INCLUDE_DIR 寻找头文件并且设置可执行文件 main 需要与链接库 LIBDB_CXX_LIBRARIES 进行连接。

<strong>第三步，执行 cmake</strong>

完成 Findlibdb_cxx.cmake 和 CMakeList.txt 的编写后在项目的根目录依次执行 “<strong>cmake .</strong> ” 和 “<strong>make</strong> ” 可以进行编译,结果如下图所示：

图 4. 使用其他程序库时 cmake 的执行结果

<img class="aligncenter size-large" src="https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/images/step3.JPG" width="476" height="305" />
<h2>使用 cmake 生成 debug 版和 release 版的程序</h2>
在 Visual Studio 中我们可以生成 debug 版和 release 版的程序,使用 CMake 我们也可以达到上述效果。debug 版的项目生成的可执行文件需要有调试信息并且不需要进行优化,而 release 版的不需要调试信息但需要优化。这些特性在 gcc/g++ 中是通过编译时的参数来决定的,如果将优化程度调到最高需要设置参数-O3,最低是 -O0 即不做优化;添加调试信息的参数是 -g -ggdb ,如果不添加这个参数,调试信息就不会被包含在生成的二进制文件中。

CMake 中有一个变量 CMAKE_BUILD_TYPE ,可以的取值是 Debug Release RelWithDebInfo 和 MinSizeRel。当这个变量值为 Debug 的时候,CMake 会使用变量 CMAKE_CXX_FLAGS_DEBUG 和 CMAKE_C_FLAGS_DEBUG 中的字符串作为编译选项生成 Makefile ,当这个变量值为 Release 的时候,工程会使用变量 CMAKE_CXX_FLAGS_RELEASE 和 CMAKE_C_FLAGS_RELEASE 选项生成 Makefile。

现假设项目中只有一个文件 main.cpp ,下面是一个可以选择生成 debug 版和 release 版的程序的 CMakeList.txt ：

清单 7
<blockquote>PROJECT(main)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
SET(CMAKE_SOURCE_DIR .)
SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb")
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")
AUX_SOURCE_DIRECTORY(. DIR_SRCS)
ADD_EXECUTABLE(main ${DIR_SRCS})</blockquote>
第 5 和 6 行设置了两个变量 CMAKE_CXX_FLAGS_DEBUG 和 CMAKE_CXX_FLAGS_RELEASE, 这两个变量是分别用于 debug 和 release 的编译选项。 编辑 CMakeList.txt 后需要执行 ccmake 命令生成 Makefile 。在进入项目的根目录,输入 "ccmake ." 进入一个图形化界面,如下图所示：

图 5. ccmake 的界面

<img class="size-large aligncenter" src="https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/images/step41.JPG" width="454" height="306" />

按照界面中的提示进行操作,按 "c" 进行 configure ,这时界面中显示出了配置变量 CMAKE_BUILD_TYPE 的条目。如下图所示：

图 6. 执行了 configure 以后 ccmake 的界面

<img class="aligncenter size-large" src="https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/images/step42.JPG" width="454" height="306" />

下面我们首先生成 Debug 版的 Makefile ：将变量 CMAKE_BUILD_TYPE 设置为 Debug ,按 "c" 进行 configure ，按 "g" 生成 Makefile 并退出。这时执行命令 find * | xargs grep "O0" 后结果如下:

清单 8 find * | xargs grep "O0"的执行结果
<blockquote>CMakeFiles/main.dir/flags.make:CXX_FLAGS = -O0 -Wall -g -ggdb
CMakeFiles/main.dir/link.txt:/usr/bin/c++ -O0 -Wall -g -ggdb
CMakeFiles/main.dir/main.cpp.o -o main -rdynamic
CMakeLists.txt:SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb")</blockquote>
下面我们将生成 Release 版的 Makefile ：再次执行命令 "ccmake ." 将变量CMAKE_BUILD_TYPE 设置为 Release ,生成 Makefile 并退出。执行命令 find * | xargs grep "O0" 后结果如下：

清单 9 find * | xargs grep "O0"的执行结果
<blockquote>CMakeLists.txt:SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb")</blockquote>
而执行命令 find * | xargs grep "O3" 后结果如下:

清单 10. find * | xargs grep "O3"的执行结果
<blockquote>CMakeCache.txt:CMAKE_CXX_FLAGS_RELEASE:STRING=-O3 -DNDEBUG
CMakeCache.txt:CMAKE_C_FLAGS_RELEASE:STRING=-O3 -DNDEBUG
CMakeFiles/main.dir/flags.make:CXX_FLAGS = -O3 -Wall
CMakeFiles/main.dir/link.txt:/usr/bin/c++ -O3 -Wall
CMakeFiles/main.dir/main.cpp.o -o main -rdynamic
CMakeLists.txt:SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")</blockquote>
这两个结果说明生成的 Makefile 中使用了变量 CMAKE_CXX_FLAGS_RELEASE 作为编译时的参数。

原贴地址：<a href="https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/" target="_blank" rel="noopener">https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/</a>