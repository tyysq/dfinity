# 重新安装Canister

在开发周期中，您可能会安装，然后随着调试和改进的需要替换程序。

在这种情况下，您可能希望保留已注册的Canister标识符，但不保留任何Canister的代码或状态。例如，您的Canister可能只包含您不想保留的测试数据，或者您可能决定完全更改程序，但想在先前安装的Canister标识符下重新安装。

在Internet Computer网络上重新安装：

1. 打开一个终端并进入项目目录
2. 如有必要，启动Internet Computer网络

多数情况下，仅当您在本机运行Internet Computer网络，才需要执行该步骤

如果Canister重新安装在远程网络上，则应包括--network命令行选项，以在该网络上执行任务。

    3. 验证您具有要重新部署的所有Canister的标识符。

    4. 运行以下命令以重新部署所有Canister

**`dfx canister install --all --mode reinstall`**

请注意，无论Canister是否具有与之关联的代码或状态，都可以使用重新安装模式来替换

