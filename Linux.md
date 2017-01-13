# Linux

[Ubuntu下使用OpenGL图形库](http://ptbsare.org/2014/05/17/ubuntu%E4%B8%8B%E4%BD%BF%E7%94%A8opengl%E5%9B%BE%E5%BD%A2%E5%BA%93/)

**apt-get install无法定位软件包错误**

>  使用sudo apt-get updata

[E:无法修正错误,因为您要求某些软件包保持现状,就是它们破坏了软件包间的依赖关系](http://www.cnblogs.com/LeoGodfrey/p/3316834.html)

[E: 错误，pkgProblemResolver::Resolve 发生故障，这可能是有软件包被要求保持现状的缘故。 E: 无法更正依赖关系](http://blog.csdn.net/yan456jie/article/details/45869317)

卸载包 apt-get purge mentohust

更换源 gedit /etc/apt/sources.list

**chmod：command not found**

使用sudo

**vi保存文件时遇到的问题：E212: Can't open file for writing**  

ls -l /etc/sysctl.conf

chmod 666 sysct1.conf

**编译链接带有链接库的程序**

带有链接库的程序编译时需要增加链接选项,例如：gcc test.cpp  -lGL -lGLU -lglut

## 2017.1.4

**Linux下vim查找**

[在vim中使用查找命令查找指定字符串](http://sucre.blog.51cto.com/1084905/270556)

[vim中优雅的查找和替换](http://harttle.com/2016/08/08/vim-search-in-file.html)

`/word`从上到下查找word这个单词

`?word`从下到上查找word这个单词

按`n`，代表向当前方向继续寻找

按`N`，代表向相反方向继续寻找

**/bin/sh^M:bad interpreter: No such file or directory**

[ sh脚本异常：/bin/sh^M:bad interpreter: No such file or directory](http://www.cnblogs.com/0616--ataozhijia/p/4218044.html)

> vim filename
>
> :set ff / set fileformat  得到 fileformat=dos/fileformat=unix
>
> :set ff=unix 或 :set fileformat=unix 修改文件格式

**a.out : command not found**

[My program cannot run with “command not found” error](http://askubuntu.com/questions/110803/my-program-cannot-run-with-command-not-found-error)

a.out不是可执行文件，使用

> (sudo) chmod 777 a.out

**cannot execute binary file**

[linux下解决：cannot execute binary file](http://blog.csdn.net/kenctrl/article/details/11470757)

**使用./Makefile:-bash: '\r': command not found**

原因：Makefile文件中包含了DOS/Windows类型换行符(`\r\n`),将他改为适用于Unix的换行符(`\n`)

**CMake的下载和安装**

[CMake的下载和安装](https://cmake.org/install/)                  [下载地址](https://cmake.org/download/) 

解压下载文件:`tar xvf cmake-2.8.8.tar.gz`

[CMake安装和使用(中文)](http://blog.sina.com.cn/s/blog_5aee9eaf0100y36u.html)

**CMake的使用**

[CMake的使用(很详细)](http://hahack.com/codes/cmake/)

[CMake使用PDF文档](http://sewm.pku.edu.cn/src/paradise/reference/CMake%20Practice.pdf)

> 建立项目文件夹Demo1，新建`main.cc`文件并编写代码
>
> 新建`CMakeList.txt`，编写`CMake`
>
> 执行生成Makefile文件：cmake .
>
> make编译Makefile文件

**单个源文件**

```
# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)
# 项目信息
project (Demo1)
# 指定生成目标(Demo为生成的执行文件)
add_executable(Demo main.cc)
```

**多个源文件**

```
# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)
# 指定生成目标
add_executable(Demo ${DIR_SRCS})
```

**多个目录，多个源文件**

 [Linux环境下安装OpenCV](http://blog.csdn.net/luotuo44/article/details/8909258)

## 2017.1.5

[设备网络SDK下载](http://www1.hikvision.com/cn/download_61.html)

## 2017.1.9

[linux下解压命令大全](http://www.cnblogs.com/eoiioe/archive/2008/09/20/1294681.html)

[Linux下三种环境变量的配置](http://www.linuxeden.com/html/sysadmin/20080424/56879.html)

[Linux下安装OpenCV](http://blog.csdn.net/vintage_1/article/details/17383585)

`sudo apt-get install gstreamer-1.0`

**stackOverflow插入图片**

`Ctrl+G`

**查看Ubuntu版本号**

[如何查看ubuntu的内核版本和发行版本号？](http://blog.csdn.net/debug_cpp/article/details/2687067)

`sudo lsb_release -a`

make后出现以下错误

```
make[2]: Leaving directory `/workspace/SDKs/artoolkit5-master/lib/SRC/VideoDummy'
#(cd VideoLinuxV4L2;    make -f Makefile)
#(cd VideoLinuxV4L;     make -f Makefile)
#(cd VideoLinux1394Cam; make -f Makefile)
#(cd VideoLinuxDV;      make -f Makefile)
#(cd VideoQuickTime;    make -f Makefile)
#(cd VideoQuickTime7;   make -f Makefile)
(cd VideoGStreamer;    make -f Makefile)
make[2]: Entering directory `/workspace/SDKs/artoolkit5-master/lib/SRC/VideoGStreamer'
gcc -c -O3 -fPIC -march=core2 -DHAVE_NFT=1 -DUSE_GSTREAMER_1 -I../../../include videoGStreamer.c
videoGStreamer.c:44:18: fatal error: glib.h: No such file or directory
 #include <glib.h>
                  ^
compilation terminated.
make[2]: *** [../../libARvideo.a(videoGStreamer.o)] Error 1
make[2]: Leaving directory `/workspace/SDKs/artoolkit5-master/lib/SRC/VideoGStreamer'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/workspace/SDKs/artoolkit5-master/lib/SRC'
make: *** [all] Error 2
```

在`./Configure`一步中选择`nnnnynyn`

`make clean`后再`make`

**No rule to make target "../../../include/AR2/tracking.h", needed by" ../../libAR2.a(handle.o)".  Stop.**

[解决方案](http://stackoverflow.com/questions/834748/gcc-makefile-error-no-rule-to-make-target)

`ls ../../../include/AR2`发现`tracking.h`已更名为`tracking.hh`

在当前目录下的`Makefile`文件中更改`tracking.h`为`tracking.hh`

**fatal error: AR/ar.h: No such file or directory include <AR/ar.h>(未解决)**

[Linux中提示No such file or directory解决方法](http://www.111cn.net/sys/linux/43010.htm)

**dos文件转换为unix文件**

`vim`打开文件`:set ff`显示当前文件格式；`set ff=unix`将文件格式转换为`unix`

[dos2unix批量转换的一种方法](http://blog.csdn.net/rainnnbow/article/details/49094897) `find . -name "*" -exec dos2unix {} \;`

**commands commence before first target**

[Makefile错误：commands commence before first target.](http://blog.csdn.net/lopper/article/details/4345356)

原因：一行的开头不是`tab`键，结尾`\`后有空格

## 2017.1.10

**fatal error: AR/ar.h: No such file or directory include <AR/ar.h>**

问题：在`lib/SRC/AR2`文件夹下，`make`后出现该问题

```
gcc -c -o handle.cpp handle.o
fatal error: AR/ar.h: No such file or directory include <AR/ar.h>
```

可以看出是使用`gcc`在进行编译，而且没有任何链接选项。

原因：由于原来一些`.c`文件更改为了`.cpp`文件，而`Makefile`文件中依然是使用`gcc`

```
CC=gcc
CFLAGS=-O3 -fPIC -march=core2 -DHAVE_NFT=1 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml2 -I$(INC_DIR)/linux-x86_64 -I$(INC_DIR)
```

修改：增加以下代码

```
CXX=g++ -std=c++11
CXXFLAGS=-O3 -fPIC -march=core2 -DHAVE_NFT=1 -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml2 -I$(INC_DIR)/linux-x86_64 -I$(INC_DIR)
```

`SRC`文件夹下`make`通过

**genTexData**

`Makefile`中

```
genTexData.o: genTexData.c $(HEADDERS)
        ${CC} -c $(CFLAG) genTexData.c
```

改为

```
genTexData.o: genTexData.cpp $(HEADDERS)
        ${CC} -c $(CFLAG) genTexData.cpp
```

**genMarketSet**

在`windows`上编译时就出现过`无法解析的外部符号_arVideoLumaInit`等问题，在`Linux`上编译同样出现了该问题`undefined reference to arVideoLumaInit`

**在`windows`上**调试发现`arVideoLumaInit`函数在`include\AR\videoLuma.h`中声明,实现在`\lib\SRC\Video\videoLuma.c`中,但是在解决方案下`AR`项目中并没有包含这两个文件，所以把这两个文件添加进去即可。

**在`Linux`上**`lib/SRC/AR`下的`Makefile`中添加`videoLuma.h`路径以及生成`videoLuma.o`文件路径

**`HEADERS`=**下+`$(AR_HOME)/include/AR/videoLuma.h \`

**`OBJS`=**下+`../Video/videoLuma.o \`

**dispFeatureSet**

`Makefile`中将`dispFeatureSet.c`改为`dispFeatureSet.cpp`。

**Util**

`lib/SRC/Util/Makefile`文件添加

```
CXXFLAGS= -fPIC -march=core2 -DHAVE_NFT=1 -pthread -I/usr/include/gstreamer-0.10 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml2 -I$(INC_DIR)
```

```
INCLUDE=$(INC_DIR)/profile.h \
        $(INC_DIR)/threadset.h \
        thread_sub_winrt.h
        
LIBOBJS=${LIB}(profile.o) \
        ${LIB}(thread_sub.o) \
        ${LIB}(thread_sub_winrt.o)
```

## 2017.1.11

**Util**

**a storage class can only be specified for objects and functions**

[storage class error](http://blog.csdn.net/weibin_168/article/details/6669736)

"storage class"的修饰符用在了对象或者变量(`objects`)和函数(`functions`)外的其他地方。

`C++`规范中四种`storage class`修饰符：`auto`、`register`、`static`和`extern`

**错误原因：**在`threadset.cpp`文件中有`static enum`。

**解决：**去掉`static`即可

**Makefile文件**

部分更改，`CFLAG`改为了`CFLAGS`,去掉了`LIBOBJS=`后边变量前的`${LIB}`.此时编译通过，但是没有生成`.a`文件。

更改回来后成功生成`libARUtil.a`文件。

**`nftSimple`编译成功**

## 整理

[(官网)Building ARToolKit from Source](http://artoolkit.org/documentation/doku.php?id=8_Advanced_Topics:build_artoolkit)

[FFmpeg和Opencv安装](http://192.168.199.107:10080/w/opencv/read-from-rtmp/)

在`./Configure`一步中选择`nnnnynyn`

`make clean`后再`make`



