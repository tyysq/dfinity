# 4.自然数自增

在本章节中，将编写一个创建actor并提供几个函数来增加一个计数器的程序，同时会讲解如何维护一个值。

本章节中，actor被命名为Counter。程序使用 currentValue值来包含一个代表counter当前值的自然数。这个程序会支持下面的函数调用

* increment函数调用会将当前的值加1（无返回值）
* get函数会调用查询并返回当前的值
* set函数会将当前的值更新为用户输入的值

本章节提供一个简单的示例，展示如何在部署的Canister中调用函数来增加一个计数器。通过多次调用函数来增加值，可以验证变量状态和变量在调用之间的持续性。

