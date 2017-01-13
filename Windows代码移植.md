# 代码移植

## 2016.12.21

- 安装OpenGL，修正`include<GL/glut.h>`包含错误

- `videoImage.c`文件`#include"jpeglib.h`改为`winrt-8_1-x86\jpeglib.h`

- `kpmMatching.cpp`文件`#include<jpeglib.h>`改为`#include "winrt-wp8_1-x86\jpeglib.h"`

- 下载了DSVL相关，在D:\OpenGL\AR\AR路径下，未配置

  > 配置方法:
  >
  > 1. 找到vs安装目录,.h文件放入 vs2013->VC->include
  >
  > 2. lib文件放入 vs2013->VC->lib
  > 3. dll文件放入C:\Windows\SysWOW64下
  > 4. vs2013配置中的链接器添加对应.lib文件

- 下载了Pthread库[ftp://sources.redhat.com/pub/pthreads-win32/pthreads-w32-2-7-0-release.exe](ftp://sources.redhat.com/pub/pthreads-win32/pthreads-w32-2-7-0-release.exe)

  下载路径:C:\Users\Administrator\Downloads

  将Pre-built.2中的`include`和`lib`配置好，vs链接器添加`pthreadVC2.lib;pthreadVSE2.lib`

  测试pthread库程序路径:E:\test\PthreadTest

- 解压ARToolKit-2.71.2，路径:`D:\OpenGL\AR\AR`

  得到libARvideod.dll，下载libARvideo.dll放到C:\Windows\SysWOW64下

- `glext.h`和`wglext.h`放到vs2013的include文件夹下

- AR2中将.c文件删除，添加现有项AR2下的所有.cpp文件;更改jpeg.cpp文件中`#include"jpeglib.h"`为`#include"winrt-w8_1-x86\jpeglib.h"`

- ARgsub_lite中的gsub_lite.c文件夹下`PFNGLGENBUFFERSPROC`无法识别，删除找不到的.c和.h文件添加对应目录下的文件即可。(后将OpenGL库替换，编译成功)

  - **ARUtil中错误 error C2664: “void *(THREAD_HANDLE_T *)”: 无法将参数 1 从“void *”转换为“THREAD_HANDLE_T *”**

- 找不到xxx文件错误:把文件删掉再到SRC文件夹下对应目录添加文件

- **ARVideo中无法打开文件`qedit.h`和`Movies.h`**

- 删除AR2中tracking.h文件，添加`include\AR2\tracking.hh`文件

- KPM中文件替换后生成成功

- **ARWrapper中无法打开文件`qedit.h`和`Movies.h`加一堆错误**

- **calib_camera中无法打开文件`qedit.h`、`Movies.h`和`opencv2/calib3d/calib3d.hpp`**

- **calib_cmera_old-v3无法打开文件`qedit.h`和`Movies.h`,无法打开输入文件`ARvideod.lib`**

- **calib_optical中无法打开文件`qedit.h`和`Movies.h`加一堆错误,无法打开输入文件`ARgsub_lited.lib`**

- **calib_stereo中无法打开文件`qedit.h`、`Movies.h`和`opencv2/calib3d/calib3d.hpp`**

- **calib_stereo_old-v3无法打开文件`qedit.h`和`Movies.h`,无法打开输入文件`ARvideod.lib`**

- **check_id无法打开文件`qedit.h`和`Movies.h`，无法打开输入文件`ARgsub_lited.lib`**

- **dispFeatureSet中16个未知错误**

- **dispImageSet中无法打开输入文件`libjpeg.lib`**

- **genMarkerSet中无法打开输入文件`libjpeg.lib`**

- **genTexData中23个未知错误**

- **mk_patt无法打开文件`qedit.h`和`Movies.h`,无法打开输入文件`ARvideod.lib` **

- **multi无法打开文件`qedit.h`和`Movies.h`,无法打开输入文件`ARvideod.lib`  **

- **multiCube无法打开文件`qedit.h`和`Movies.h`**

- **nftSimple无法打开文件`qedit.h`和`Movies.h`**

- **optical无法打开文件`qedit.h`和`Movies.h`**

- **opticalStereo无法打开文件`qedit.h`和`Movies.h`**

- **simple无法打开文件`qedit.h`和`Movies.h`,无法打开输入文件`ARvideod.lib`**

- **simpleMovie无法打开文件`qedit.h`和`Movies.h`**

- **simpleOSG无法打开文件`qedit.h`和`Movies.h`**

- **stereo无法打开文件`qedit.h`和`Movies.h`**

- 搜到qedit.h代码粘贴到文本文档，再放到vs2013中的include文件夹下

- videoQuickTime.c中添加`#include<windows.h>`

- DirectShow的安装和配置 http://blog.163.com/xueyulong1988@126/blog/static/55163238200910259426915

- Google搜索wglext.h头文件，发现和当前使用头文件不一致，当前头文件并没有定义PFNGLGENBUFFERSPROC等信息，于是再次查找OpenGL下载http://download.csdn.net/download/whucv/4441857，重新配置。博客OpenGL库的配置http://blog.csdn.net/archielau/article/details/7768682

- 新下载的OpenGL库路径：D:\OpenGL\opengl库文件\opengl库文件

- 替换新文件后ARgsub_lite编译成功

- ARUtil中注释了`(*(arg0->start_routine))(arg0->arg);`,编译成功

## 2016.12.22

- 下载了`Movies.h`等一系列文件，下载地址https://github.com/wdlindmeier/Big-Screens-Quicktime-Player/tree/master/Source

- 下载安装DirectShow SDK，参考:

  [DirectShow+VS2010+Win7配置说明](http://www.cnblogs.com/oucsheep/p/4822911.html)

  [Microsoft Visual Studio 2010 Service Pack 1 官方离线下载版（ISO） ](http://blog.csdn.net/feidewu/article/details/8105890)

  [fatal error C1083: 无法打开包括文件:“qedit.h”: No such file or directory](http://blog.csdn.net/wuxiaoyao12/article/details/7257891)

  [提示缺少Qedit.h问题](http://blog.csdn.net/joeblackzqq/article/details/10944005)

- [error C4430: 缺少类型说明符 - 假定为 int](http://blog.csdn.net/zyrr159487/article/details/6932229)

## 2016.12.23

- 命令行编译libjpeg.lib遇到的问题

  [用命令行编译libjpeg.lib](http://blog.csdn.net/shuixin536/article/details/5706820)

  [fatal error C1083: 无法打开包括文件:“stddef.h”: No such file or directory](http://www.cnblogs.com/VVingerfly/p/5456423.html)

  crtdefs.h、sal.h、ConcurrencySal.h、vadefs.h

  未解决

- error LNK2019: 无法解析的外部符号 ___glutInitWithExit@12，该符号在函数 _glutInit_ATEXIT_HACK@8 中被引用

  [【学习ARToolkit小记之五】 解决“error LNK2019: 无法解析的外部符号 ___glutCreateWindowWithExit@8”错误](http://www.lai18.com/content/9466196.html)

- [【学习ARToolkit小记之初】 ARToolkit在VS2010（Win7 64位）下的配置及第一个开发程序的编译与运行](http://www.voidcn.com/blog/qingyang8513/article/p-4314502.html)


## 2016.12.26

以下为ARToolkit2.72.1版本

- [error LNK2019: 无法解析的外部符号 _gluGetString@4，该符号在函数 _main 中被引用](http://blog.csdn.net/huanghuibai/article/details/9503261)

  **错误原因**： opengl的库文件(.lib)文件没有包含到工程中

  关于无法解析的外部符号问题，详见**一些问题12**

- 无法打开包括文件:"openvrml/browser.h"

  **错误原因：**OpenVRML文件夹没有放到工程目录下

- error C1041: 无法打开程序数据库“e:\artoolkit-2.72.1-bin-win32\artoolkit\lib\src\gl\debug\vc120.pdb”；如果要将多个 CL.EXE 写入同一个 .PDB 文件，请使用 /FS   libARgsubUtil项目中

  error LNK1104: 无法打开文件“E:\ARToolKit-2.72.1-bin-win32\ARToolKit\lib\libARgsubUtild.lib”

  [解决方案](http://home.eeworld.com.cn/my/space-uid-291513-blogid-239457.html) 在libARgsubUtil中的属性改，只改下边解决方案第一条即可。

  解决方案：修改项目属性 右击项目 --> "属性”

  1. “C/C++” --> "常规” -->”调试信息格式” 设置为 “C7 兼容(/Z7)”
  2. “C/C++” --> "代码生成” -->”启用字符串池” 设置为 “是(/GF)”
  3. “链接器” --> "调试” -->”生成调试信息” 设置为 “是(/DEBUG)” 

- simpleVRML中出现各种无法解析的外部符号错误，如:

  错误	214	error LNK2019: 无法解析的外部符号 "__declspec(dllimport) bool __cdecl std::operator==<char,struct std::char_traits<char>,class std::allocator<char> >(class std::basic_string<char,struct std::char_traits<char>,class std::allocator<char> > const &,char const *)" (__imp_??$?8DU?$char_traits@D@std@@V?$allocator@D@1@@std@@YA_NABV?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@0@PBD@Z)，该符号在函数 __ehhandler$??0sentry@?$basic_ostream@DU?$char_traits@D@std@@@std@@QAE@AAV12@@Z 中被引用	simpleVRML

  ​

- http://imbinwang.github.io/blog/simple-ar-diy


## 2016.12.27

[ Win7+VisualStudio2013编译ARToolKit5.3源码](http://blog.csdn.net/lshmusic/article/details/53180941)

- [ARToolKit5 windows SDK下载](https://artoolkit.org/download-artoolkit-sdk) 解压后在`E:\ARToolKit5`

- [ARToolKit5源码下载](https://github.com/artoolkit/artoolkit5) 解压后在`E:\artoolkit5-master`

- 摄像头采集模块1：DirectShow(下载Microsoft Platform SDK或者官方提供的dshow包)解压后在`C:\Program Files\Microsoft SDKs`

  摄像头采集模块2：QuickTime SDK  [QuickTime SDK for Windows](https://github.com/zhaozhongshu/quicktime-sdk-7.3-for-windows) 解压后在`C:\Program Files (x86)\QuickTime SDK`

  [dshow和QuickTime的相关资源和配置参考链接](https://artoolkit.org/documentation/doku.php?id=8_Advanced_Topics:windows_building_libarvideo)

- opencv2.4.10

- 视图->其他窗口->属性管理器，打开属性管理器中任意项目->Debug|Win32->Microsoft.Cpp.Win32.user,双击

  配置`include`路径和`lib`路径

![Aaron Swartz](http://img.blog.csdn.net/20161116003447881?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)
![Aaron Swartz](http://img.blog.csdn.net/20161116003612680?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)
  `CInclude\Processes.h`中注释掉`GetProcessInformation`声明

  `CInclude\fp.h`中注释了`typedef double float_t`


## 2016.12.28

- M_PI_4未声明的标识符错误，在ARWrapper中的`ARToolKitVideoSource.cpp`中添加

```
#define _USE_MATH_DEFINES
#include <cmath>

#define _USE_MATH_DEFINES
#include <math.h>
```

网上下载的`ARToolKit`程序除了`getMarkerSet`项目外跑通

- 重新解压`DeepAR_Algorithm`(`include`和`lib`路径都已配置好)

  1. 更新源文件。将某些`.c`源文件删除再添加对应文件夹中的`.cpp`文件

  2. `ARWrapper`中`ARController.cpp`中错误:`kpmCreateHandle`函数不接受1个参数

     第二个参数添加`m_videoSource0->getPixelFormat()`

     又出现一堆

     >  在文件范围内找到“{”(是否缺少函数头？)

     等错误

     将`trackingSub.c`改为`trackingSub.cpp`后出现一堆无法解析的外部符号错误

  3. `dispFeatureSet`中提示错误，将`dispFeatureSet.c`改为`dispFeatureSet.cpp`后编译成功

  4. `genMarkerSet`中无法解析的外部符号错误

  5. `genTexData`中提示错误，与`dispFeatureSet`中的错误类似，错误所在文件为`kpm.hh`、`detector.hh`

  6. `nftBook`、`nftSimple`中同上,可能原因`.c`文件调用`.cpp`文件中的东西

   [关于“在文件范围内找到“{”(是否缺少函数头？)"错误](http://blog.sina.com.cn/s/blog_8e1b844c0102w5cx.html) 将`.c`文件后缀改为`.cpp`即可，原因见链接


## 2016.12.29

`nftSimple.cpp`中定义了

```
ARTrackerManager arTrackerManager;
KPMDetector kpmDetector;
```

`ARTrackerManager`类在`tracking.hh`文件中定义

`KPMDetector`类在`kpm.hh`文件中定义

`trackingSub.cpp`文件`extern KPMDetector kpmDetector;`

`trackingSub.cpp`和`nftSimple.cpp`中都包含了`trackingSub.h`

`ARTrackerManager`类和`KPMDetector`类封装了`tracking.hh`文件和`kpm.hh`文件中的函数并改变了名字。

--------

`threadset.h`文件替换了`thread_sub`文件

其中函数名称的变化：

`namespace sx_ar_threadset`

`threadInit`--------->`Init`

`threadFree`--------->`Free`

`threadStartSignal`--------->`MasterStartWorker`

`threadGetStatus`--------->`MasterGetStatus`

`threadGetBusyStatus`--------->`GetBusyStatus`

`threadEndWait`--------->`MasterWaitWorkerEnd`

`threadWaitQuit`--------->`MasterQuitWorkerWait`

`threadStartWait`--------->`WorkerWait`

`threadEndSignal`--------->`WorkerEnd`

`threadGetID`--------->`GetID`

`threadGetArg`--------->`GetArg`

`threadGetCPU`--------->`GetCpu调用SXARGetCPU`

**`nftSimple`编译成功**

-----------

`nftBook`项目中的修改基本同`nftSimple`。

链接依赖项中去掉了`ARosgd.lib`，移除了`VirtualEnvironment.h`和`VirtualEnvironment.cpp`

并在代码中与`VirtualEnvironment.h`相关的函数外加上

```
#ifdef AROSG
#endif
```

**`nftBook`编译成功**

-----

`ARWrapper`项目中修改同上

**`ARWrapper`编译成功**