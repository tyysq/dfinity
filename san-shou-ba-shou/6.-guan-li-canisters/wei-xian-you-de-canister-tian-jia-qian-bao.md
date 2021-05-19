# 为现有的Canister添加钱包

当您本地开发创建新项目时会同时自动创建一个默认钱包，如果想为原来创建的Canister添加一个钱包，您可强制用dfx通过手动步骤来生成。

为现有Canister添加钱包：

1. 打开一个终端并进入项目目录
2. 如有必要，运行以下命令来停止Internet Computer网络

**`dfx stop`**

     3. 删除.dfx目录

    4. 使用以下命令启动Internet Computer网络

**`dfx start --clean`**

