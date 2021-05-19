# 6.库模块导入



本章节中，将会编写一个可以存储并查询电话号码的简单程序。这个教程讲解了如何导入和使用一些基本的Motoko库函数。

这篇教程中，Motoko基本库函数定义在List和AssocList模块中，允许你将list作为链接的键值对使用。这片例子中，键是name， 值是绑定name的phone文本字符串

这个程序支持下面的函数调用

* insert函数接受name和phone键值对作为输入参数并存储在book变量中
* lookup函数是一个query函数，使用name作为输入来查询相关的电话号码

