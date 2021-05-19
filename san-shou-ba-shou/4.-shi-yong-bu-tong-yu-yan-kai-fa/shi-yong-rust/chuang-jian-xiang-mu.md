# 创建项目

因为大部分的Rust程序员使用Cargo来处理创建和包管理任务（储如下载和编译依赖库），首先使用Cargo命令行接口来创建一个新的Rust项目。

或者，您可以使用DFINITY Canister软件开发包\(SDK\)来代替Cargo创建新的项目，但是使用Cargo来创建新项目代表了Rust项目的典型工作流程。

创建一个新项目：

1. 在本地计算机上打开终端
2. 运行以下命令以验证Cargo是否安装:

**`cargo --version`**

    3.更改到您的Internet Computer或Rust示例项目的目录。

    4.运行类似以下命令来创建新项目：

**`cargo new my_rust_program`**

该命令创建一个新的my\_rust\_program目录，包含了默认的Cargo.toml文件和带有默认main.rs文件的src目录。

    5.运行下列命令进入到项目目录：

**`cd my_rust_program`**

如果您显示该目录内容，您将看到目录下仅包含Cargo.toml文件和src目录。为了编译项目以使能在Internet Computer上运行，您还需要一些其他文件。

