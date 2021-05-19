# 修改默认程序

在[探索默认项目](../1.-tan-suo-mo-ren-xiang-mu/)章节，已经介绍了创建新项目会创建一个默认的src目录，并包含一个main.mo程序模板文件。在本章节中，可以修改模板代码创建一个简单的使用actor的"Hello, World!"程序

源码修改步骤

1. 进入项目目录

**`cd src/actor_hello`**

    2. 编辑器中打开main.mo文件

         接下来会编写一个可以输出"Hello, World!"的示例程序。为了编译后的程序在ICP上运行，程序必须包含一个有public函数的actor对象。

复制粘贴以下示例代码到main.mo文件

```text
import Debug "mo:base/Debug";
actor HelloActor {
 public query func hello() : async () {
 Debug.print ("Hello, World from DFINITY \n");
 }
};
```

代码解析

* 程序导入Debug模块来提供print功能
* 程序使用public query func来定义一个查询方法，在这个方法中，actor\_hello程序不会对canister状态进行修改或执行更新数据的操作。

要获取有关查询调用的信息，请查看[Canisters include both program and state](../../er-ji-ben-gai-nian/4.canister-cheng-xu-guan-he-dai-ma.md)的[query calls](../../er-ji-ben-gai-nian/4.canister-cheng-xu-guan-he-dai-ma.md)章节

