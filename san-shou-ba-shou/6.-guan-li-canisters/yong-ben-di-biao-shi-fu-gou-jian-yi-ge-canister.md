# 用本地标识符构建一个Canister

为项目编写源代码后，需要将其编译为WebAssembly模块，然后才能将其作为Canister部署到网络中。

如果仅编译项目以进行本地调试，则可以为项目生成本地定义的标识符。

生成本地定义的标识符：

1. 创建一个满足需求的具有配置设置和程序逻辑的项目
2. 如有必要，启动Internet Computer网络

多数情况下，仅当您在本机运行Internet Computer网络，才需要执行该步骤

如果要编译Canister以在远程网络上运行，则应包括--network命令行选项，以在该网络上执行任务。

1. 通过运行以下命令，为dfx.json中定义的Canister生成硬编码的本地标识符：

**`dfx build --check`**

请注意，必须先注册唯一的Canister标识符来替换本地定义的标识符，然后才能在Internet Computer网络上部署项目。

