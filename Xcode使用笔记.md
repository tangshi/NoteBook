#### 调试笔记

**错误信息：**
> dyld: Library not loaded: @executable_path...  
> ...  
> image not found

**错误原因：**

引用的第三方Framework编译时没有被正确添加到App包中，运行时找不到这个Framework。出错原因是编译时运行的脚本里将路径写错。

---

#### 调试笔记

**错误信息：**

> unknown type name "uint32_t" (uint64_t等)

**错误原因：** 

可能的原因目前已知有两种:

1. 诸如`uint32_t`等变量类型是c++11的特性(c++11其实是引用了c99标准中的`inttypes.h`头文件)，所以需要将编译器改为支持c++11特性的编译器。
2. c++标准不同产生的混乱。Xcode兼容LLVM的`libc++`和GCC的`libstdc++`标准库，二者有差别，可能会造成该错误，一般建议Xcode上使用苹果自家支持的`libc++`比较好。

如我在Xcode上使用Ogre时，就产生了这个错误，若创建项目时勾选`use libc++`就不会有这种错误了。

---

#### 小技巧

** 查看依赖库类型 **

经常会使用一些`Framework`、`Dynamic Lib`或者`Static Lib`，但是使用它们的时候可能需要考虑它们编译的目标平台，一般需要共享的依赖库需要编译成`Universal`类型兼容32位和64位机器，查看这些依赖库的编译目标平台很简单，只需要在终端使用以下命令即可：

```
# 对于 fw.Framework
> cd Path/to/fw.Framework
> file ./Versions/current/fw

# 对于静态链接库  sl.a 
> cd Path/to/sl.a
> file sl.a
 
# 对于动态链接库  dl.dynlib
> cd Path/to/dl.dynlib
> file dl.dynlib
```

以fw.Framework的结果为例，其输出为：

> fw.Framework/Versions/current/fw:  Mach-O universal binary with 2 architectures

> fw.Framework/Versions/current/fw: (for architecture x86_64): Mach-O 64-bit dynamically linked shared library x86_64

> fw.Framework/Versions/current/fw: (for architecture i386): Mach-O dynamically linked shared library i386 

