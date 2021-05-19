# 查找Canister标识符

所有Canister都具有唯一的，特定网络的标识符。 您通常需要使用这些标识符与Canister进行交互。 例如，如果要访问应用程序的前端Canister或使用Candid Web接口与服务进行交互，则必须指定适当的Canister标识符。

由于标识符是特定于网络的，因此用于存储信息的文件位于不同的目录中。 例如，本地部署的Canister的标识符位于项目的.dfx/local/canister\_ids.json文件中。

您可以通过运行dfx canister id命令来查找任何特定Canister的标识符。 例如，要查找部署在本地网络上的名为lookup的Canister标识符，可以运行以下命令：

**`dfx canister id lookup`**

要查找由IC别名指定的网络上部署的同一Canister的标识符，请运行以下命令：

**`dfx canister --network=ic id lookup`**

