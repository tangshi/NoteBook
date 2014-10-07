# 在Mac OS上编译Ogre1.9

1. 下载并安装跨平台编译系统[CMake](http://www.cmake.org/download/)
2. 下载并安装[NVIDIA Cg](https://developer.nvidia.com/cg-toolkit-download)
3. 下载Ogre源代码。一般在[官网下载页面](http://www.ogre3d.org/download/source)下载，也可到源码托管网站([Bitbucket](https://bitbucket.org))下载[Ogre源代码](https://bitbucket.org/sinbad/ogre/downloads)，下载的内容更为丰富。
4. 下载Ogre依赖库。Ogre提供了[依赖库压缩包链接](http://www.ogre3d.org/download/source)，其真实地址在[这里](http://sourceforge.net/projects/ogre/files/ogre-dependencies-mac/)，解压依赖库到Ogre源代码根目录下名为`Dependencies`的文件夹内。(也可自行安装各个依赖库的官方版，使用homebrew可以很方便地安装`boost`、`freetype`、`zzip`、`freeimage`、`Doxygen`等大部分依赖库)。
5. 新建一个`build`文件夹用于编译(一般新建在Ogre源代码根目录下)。
6. 运行CMake。设置`Where is the source code`为Ogre源代码路径，设置`Where to build the binaries`为上一步新建的`build`文件夹。点击`configure`，选择生成工具为`Xcode`，编译器选择默认，完成配置。接下来CMake会自动根据配置搜集编译的环境信息，最后出现一个罗列了编译选项的面板，可以根据自己的喜好勾选这些选项，一般不需要改变，默认即可(注意，看到那些选项是醒目的红色不要紧张，那是CMake将发现的新变量显示为红色，因为是首次配置，所以所有的变量都是红色的)。选定编译选项之后，再点击一次`configure`并点击`Generate`。CMake将生成编译Ogre所需的编译系统。
7. 回到`build`文件夹，你会发现CMake已经将整个编译系统生成在这个文件夹内，双击工程文件`OGRE.xcodeproj`打开Ogre工程。
8. 必须将该工程的`standard library`与`c++ dialect`设置为与Ogre项目相同，故选中工程，有以下修改：
	* 修改`build settings > Apple LLVM 6.0-Language-C++ > C++ Standard Library`为`libc++(LLVM C++ standard library with C++11 support)`，
	* 修改`build settings > Apple LLVM 6.0-Language-C++ > C++ Language Dialect`为`C++11 [-std=c++11]`。
	
	否则可能会出现大量如下错误：
	
		Undefined symbols for architecture armv7:
		"std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, unsigned long, std::allocator<char> const&)", referenced from:
		...
	该方法参考自[Ogre官网论坛某问答](http://www.ogre3d.org/forums/viewtopic.php?f=21&t=79199)
		 
9. 将`ALL_BUILD`、`install`这两个目标(Target)的配置改为`Release`(`Product > Scheme > Edit Scheme > Run > Buidl Configuration > Release`)。
10. 选中`ALL_BUILD`，编译(快捷键cmd+B)。
11. 编译成功后再选中`install`，编译。该目标编译完成后将会把编译完成的Ogre的所有内容复制到`build`文件夹下一个名为`sdk`的文件夹内，方便我们使用Ogre。
12. 如果依赖库没有编译到系统中，则还需要将`Dependencies`文件夹也拷贝到`sdk`的文件夹内。
13. 建议将第11步的`sdk`文件夹的内容转移到其他地方(如`~/Developer`)，并将`sdk`重命名为更加清楚的名字(如`OgreSDK`)，这样使用Ogre会更加方便。
14. 结束。


# 在Xcode上使用Ogre

1. 下载Ogre的[Xcode 模板](http://www.ogre3d.org/download/tools)并安装。
2. 重启Xcode，新建项目，发现新增了创建Ogre项目的选项，创建一个Ogre项目，创建时一定要勾选使用libc++，否则会导致大量莫名其妙的错误(libc++是LLVM项目针对c++11编写的c++实现标准库)。
3. Xcode可能会出现Frameworks找不到的情况，若出现这种情况，则需要重新添加这些Frameworks。
4. 选中整个项目，添加自定义变量`OGRE_SDK_ROOT`，其值即`OgreSDK`文件夹。(`Editor > add build setting > add user-defined setting`)
5. 注意根据`OgreSDK`和依赖库的实际情况调整`Framework Search Paths`、`Header Search Paths`、`Library Search Paths`。(`Recursive`是递归查找的意思，慎用！`Boost`库的头文件路径不可以用`Recursive`。)
6. 编译，运行，结束。
