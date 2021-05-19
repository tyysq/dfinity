# 在Internet Computer网络上部署Canister



编译程序后，可以将编译后的代码安装在本地运行的Internet Computer网络上，也可以安装在远程网络上。

预先创建的Canister标识符或在构建过程中创建的Canister标识符决定了在部署过程中代码的安装位置。

首次在Internet Computer网络上进行部署：

1. 打开一个终端并进入项目目录
2. 如有必要，启动Internet Computer网络

多数情况下，仅当您在本机运行Internet Computer网络，才需要执行该步骤

如果Canister安装在远程网络上，则应包括--network命令行选项，以在该网络上执行任务。

    3. 验证您具有要部署的所有Canister的标识符。

    4. 运行以下命令部署所有Canister

**`dfx canister install --all`**

