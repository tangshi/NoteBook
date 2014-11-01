# Xcode运行时添加参数或环境变量

一般在命令行下运行可执行文件时，可以在可执行文件后输入若干参数。比如以下命令是运行名为`test`的可执行文件，并且运行带有两个参数。

> ./test arg1 arg2


在`xcode`项目中，这个功能也是可以实现的，虽然比较麻烦，设置方式如下

1. 菜单栏选择`product -> Scheme -> Edit Scheme...`，或者使用快捷键`cmd + <`
2. 选中你希望带参数运行的Target
3. 在`Run -> Arguments -> Arguments Passed On Launch`下添加需要的运行参数
4. 在`Run -> Arguments -> Environment Variables`下添加需要的环境变量