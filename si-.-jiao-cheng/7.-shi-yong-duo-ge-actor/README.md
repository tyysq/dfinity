# 7.使用多个actor

在本章节中，将会创建一个由多个actor的项目。到目前为止，我们只在一个Motoko文件中定义一个actor，并且一个actor会编译到一个canister。我们也可以创建一个由多个actor的项目并且从一个dfx.json构建多个canister。

在本章节中，你将在同一个项目中创建单独的程序文件，并包含3个actor。这个项目定义了以下不相关的actor。

* assistant actor提供to-do list的添加和查看任务的函数

为了简单，本教程的示例代码只包含添加to-do list任务和查看已添加任务的功能。本程序更完整的版本-有更多功能比如标记任务完成和从to-do list删除任务-可以在[examples](https://github.com/dfinity/examples/)代码库的[Simple to-do checklist](https://github.com/dfinity/examples/tree/master/motoko/simple-to-do)查看。

* rock\_paper\_scissors actor 提供硬编码的rock-paper-scissors比赛中决定赢家的函数。

这个示例代码描述了在Motoko中switch和case的用法

* daemon actor提供了启动和结束后台的模拟函数。

这个示例代码会简单地赋值一个变量并打印演示信息。

