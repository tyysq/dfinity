# 默认程序代码



新项目会包含一个 main.mo 模板源码文件。通过编辑这个文件包含你的代码来加速开发。

接下来以 main.mo 模版文件为例来学习使用 Motoko 编程语言。

1. 在项目目录下运行命令

**`pwd`**

    2. 编辑器中打开 src/explore\_hello/main.mo 文件查看模板代码

```text
actor {
    public func greet(name : Text) : async Text {
        return "Hello, " # name # "!";
    };
};
```

这段程序有几个元素

* 示例代码定义了 actor 而不是常见的 main 函数，对于 Motoko，main 函数已经隐式地包含在文件里了。
* 虽然常见的“Hello，World！”程序描述了如何使用 print 或 println 函数打印字符串，但是一般的程序无法展示 Motoko 在 ICP 上如何使用。
* 这段示例代码定义了一个 actor，包含一个公共的 greet 函数，greet 函数接收一个 Text 类型的 name 参数。
* 程序使用 async 关键字指定程序返回一个异步文本消息，该消息通过\#操作符拼接，由 “Hello，”，name 参数和“！”组成。

之后会深入介绍如何使用 actor 对象和异步消息处理。

    3. 关闭 main.mo 继续

