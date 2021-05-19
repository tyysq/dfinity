# 升级Canister

与保留Canister标识符但不保留状态的替换不同，Canister升级使您能够保留已部署Canister的状态并更改代码。

例如，假设您有一个管理专业资料和社交关系的应用程序。 如果要向应用程序添加新功能，则需要能够更新Canister代码而不丢失任何先前存储的数据。 Canister升级使您可以通过程序更改来更新现有标识符，而不会丢失程序状态。

请注意，要在升级用Motoko编写的Canister时保留状态，请确保使用stable关键字来标识要保留的变量。有关在Motoko中保留变量状态的更多信息，请参阅[稳定变量和升级方法](https://sdk.dfinity.org/docs/language-guide/upgrades.html)。如果要升级用Rust编写的Canister，则应使用[Rust CDK示例](https://github.com/dfinity/cdk-rs/blob/master/examples/asset_storage/src/asset_storage_rs/lib.rs)中所示的pre\_upgrade和post\_upgrade函数，以确保在Canister升级后可以正确保留数据。

在Internet Computer网络上升级Canister：

1. 打开一个终端并进入项目目录
2. 如有必要，启动Internet Computer网络

多数情况下，仅当您在本机运行Internet Computer网络，才需要执行该步骤

如果要在远程网络上升级Canister，则应包括--network命令行选项，以在该网络上执行任务。

    3. 确认您具有要升级的所有Canister的标识符。

请注意，您的程序必须使用变量声明中的stable关键字来标识要为其维护状态的变量。

有关声明稳定变量的更多信息，请参见《 Motoko编程语言指南》。

    4. 运行以下命令升级所有Canister：

**`dfx canister install --all --mode upgrade`**

