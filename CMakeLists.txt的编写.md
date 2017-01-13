# CMakeLists.txt的编写

[在 linux 下使用 CMake 构建应用程序](https://www.ibm.com/developerworks/cn/linux/l-cn-cmake/)

 [cmake使用示例与整理总结](http://blog.csdn.net/wzzfeitian/article/details/40963457)

[CMake使用总结](https://www.mawenbao.com/note/cmake.html)

## 主目录(main)中的CMakeLists.txt

```
PROJECT(main) //主目录main
CMAKE_MINIMUM_REQUIRED(VERSION 2.6) //限定CMake版本
ADD_SUBDIRECTORY( src ) //添加子目录
AUX_SOURCE_DIRECTORY(. DIR_SRCS) //将目录中源文件名称赋值给DIR_SRCS
ADD_EXECUTABLE(main ${DIR_SRCS}) //将源文件编译为main可执行文件
TARGET_LINK_LIBRARIES(main Test) //链接一个名为Test的链接库(Test链接库为子目录中的CmakeLists.txt生成的)
```

## 子目录(src)中的CmakeLists.txt

```
AUX_SOURCE_DIRECTORY(. DIR_TEST1_SRCS)
ADD_LIBRARY(Test ${DIR_TEST_SRCS}) //将src目录中的源文件编译为共享库
```

## 执行过程

当程序执行`ADD_SUBDIRECTORY(src)`时进入目录`src`对其中的`CMakeLists.txt`进行解析。

## 在工程中查找并使用其他程序库

### 程序库说明文件

项目根目录中创建目录`cmake/modules/`，在`cmake/modules/`下创建文件`Findlibdb_cxx.cmake`

```
MESSAGE(STATUS "Using bundled Findlibdb.cmake...") //控制台输出状态信息
FIND_PATH( //在下边路径中查找db_cxx.h头文件并将其所在路径保存下来
	LIBDB_CXX_INCLUDE_DIR //保存.h文件的路径变量
	db_cxx.h //查找db_cxx.h
	/usr/include/
	/usr/local/include/
)
FIND_LIBRARY(
	LIBDB_CXX_LIBRARIES 
	NAMES db_cxx
	PATHS /usr/lib/ /usr/local/lib/
)
```

### 根目录中的CMakeLists.txt

```
PROJECT(main)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
SET(CMAKE_SOURCE_DIR .)
//在./cmake/modules中查找Findlibdb_cxx.cmake
SET(CMAKE_MODULE_PATH ${CMAKE_ROOT}/Modules ${CMAKE_SOURCE_DIR}/cmake/modules)
AUX_SOURCE_DIRECTORY(. DIR_SRCS)
ADD_EXECUTABLE(main ${DIR_SRCS})
FIND_PACKAGE(libdb_cxx REQUIRED)
MARK_AS_ADVANCED(
	LIBDB_CXX_INCLUDE_DIR
	LIBDB_CXX_LIBRARIES
)
IF(LIBDB_CXX_INCLUDE_DIR AND LIBDB_CXX_LIBRARIES)
	INCLUDE_DIRECTORIES{$(LIBDB_CXX_INCLUDE_DIR})
	MESSAGE(${LIBDB_CXX_LIBRARIES})
	TARGET_LINK_LIBRARIES(main ${LIBDB_CXX_LIBRARIES})
ENDIF(LIBDB_CXX_INCLUDE_DIR AND LIBDB_CXX_LIBRARIES)
```

如果 LIBDB_CXX_INCLUDE_DIR 和 LIBDB_CXX_LIBRARIES 都已经被赋值,则设置编译时到 LIBDB_CXX_INCLUDE_DIR 寻找头文件并且设置可执行文件 main 需要与链接库 LIBDB_CXX_LIBRARIES 进行连接。

## 使用 cmake 生成 debug 版和 release 版的程序

## 使用第三方库(opencv举例)

```
cmake_minimum_required(VERSION 2.8)
project( DisplayImage )
find_package( OpenCV REQUIRED )
add_executable( DisplayImage DisplayImage.cpp )
target_link_libraries( DisplayImage ${OpenCV_LIBS} )
```

[find_package的使用方法](http://www.voidcn.com/blog/bytxl/article/p-5011522.html)

## 使用已有的.so库

```
set(PROJECT_SOURCE_DIR .)
include_directories(${PROJECT_SOURCE_DIR}/include)
link_directories(${PROJECT_SOURCE_DIR}/lib)
```

