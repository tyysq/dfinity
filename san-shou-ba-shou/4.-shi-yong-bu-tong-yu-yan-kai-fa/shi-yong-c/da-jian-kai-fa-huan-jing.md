# 搭建开发环境

要将reverse.c程序编译为WebAssembly，需要安装clang编译器和标准库。 您可以通过运行以下命令来检查本地计算机上是否已安装clang：

**`clang --version`**

如果安装了clang，该命令将显示类似于以下内容的信息：

```text
clang version 10.0.0
Target: x86_64-apple-darwin19.5.0
Thread model: posix
InstalledDir: /usr/local/opt/llvm/bin
```

如果该命令未返回版本信息，请在继续之前安装clang。 根据您所使用的操作系统，安装clang的步骤会有所不同。 例如，在Debian Linux上，运行以下命令：

**`sudo apt-get install clang lld gcc-multilib`**

在macOS上，您可以通过安装开发人员命令行工具或使用Homebrew安装LLVM来安装clang。 例如，如果未安装clang，请运行以下命令：

**`brew install llvm`**

