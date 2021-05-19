# 使用C

因为Internet Computer支持应用编译到标准的WebAssembly模块，您能用象C, C++, Objective-C和Objective-C++语言标准编译器和工具和Clang编译器来生成应用程序。

为了说明如何迁移用C编写的程序以在Internet Computer上运行，让我们看一下[示例库](https://github.com/dfinity/examples/tree/master/c)中的简单reverse.c程序。reverse.c程序包含一个名为go的函数，该函数可以反转字符串。

