# Win 写文件时自动将换行符从LF转换为CRLF

### 问题描述
之前在Windows系统上写文本文件时，发现Win总是自作聪明地把换行符'\n'(即LF)，转换为“\r\n”(即CRLF)，我很生气！

### 解决方法
问题的根源在于打开文件的方式，只有以二进制文件的方式打开文件，写入的时候才不会自作主张地对换行符做转换，示例如下：

```cpp
// C语言风格
FILE* outfile = fopen( "filename", "wb" );

// C++风格
std::ofstream outfile( "filename", std::ios_base::binary | std::ios_base::out );
```

解决方法参考自：[StackOverflow: C++ change newline from CR+LF to LF](http://stackoverflow.com/a/1536010)
