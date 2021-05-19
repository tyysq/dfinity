# 项目构建

在了解了默认配置和代码并启动好本地 ICP 网络后，接下来学习如何把示例程序编译为可执行的 WebAssembly 模块

构建步骤：

1. 在命令行中进入 explore\_hello 项目目录。
2. 运行下面的命令

**`dfx build`**

输出信息如下

```text
Building canisters...
Building frontend...
```

**`dfx build`** 命令会在项目的.dfx/local/目录下添加 canisters 目录

    3. 运行下面的命令检查 dfx build 命令创建的 .dfx/local/canisters/explore\_hello 目录包含 WebAssembly 和相关应用文件。

**`ls -l .dfx/local/canisters/explore_hello/`**

 命令输出

```text
-rw-r--r--  1 pubs  staff     43 Jul 21 12:18 explore_hello.did
-rw-r--r--  1 pubs  staff    103 Jul 21 12:18 explore_hello.did.js
-rw-r--r--  1 pubs  staff    174 Jul 21 12:18 explore_hello.js
-rw-r--r--  1 pubs  staff  95905 Jul 21 12:18 explore_hello.wasm
```

canisters/explore\_hello 目录包含如下关键文件：

* explore\_hello.did 文件包含 main 程序的接口描述
* The explore\_hello.did.js 文件包含用 JavaScript 描述的程序 Canister 函数接口
* The explore\_hello.js 文件包含用 JavaScript 描述的程序 Canister 接口
* The explore\_hello.wasm 包含编译后的 WebAssembly   canisters/explore\_hello\_assets 目录包含相似的文件，用于描述项目的前端资源。 

除了这些目录，dfx build 命令还会创建 idl 目录。

