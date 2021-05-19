# 删除Canister

如果要在Internet Computer网络上永久删除特定的Canister或特定项目的所有容器，可以通过运行dfx canister delete命令来执行。

删除Canister会从Internet Computer网络中删除Canister标识符，代码和状态。 但是，在删除之前，必须先停止Canister以清除所有未决的消息请求或应答。

删除本地Internet Computer网络上运行的一个项目的所有Canister：

1. 打开一个终端并进入项目目录
2. 如有必要，启动Internet Computer网络

多数情况下，仅当您在本机运行Internet Computer网络，才需要执行该步骤

如果要在远程网络上删除Canister，则应包括--network命令行选项，以在该网络上执行任务。

    3. 运行以下命令，检查项目Canister运行状态：

**`dfx canister status --all`**

    4. 运行以下命令停止项目所有Canister：

**`dfx canister stop --all`**

    5. 运行以下命令删除项目所有Canister：

**`dfx canister delete --all`**

