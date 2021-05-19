# 重启本地Internet Computer网络

在某些情况下，由于复制状态错误，在本地启动Internet Computer网络失败。如果在运行dfx start时遇到问题：

1. 在显示网络操作的终端中，按Control-C中断本地网络进程。
2. 运行以下命令停止本地Internet Computer网络：

**`dfx stop`**

    3. 运行以下命令，以纯净状态重新启动Internet Computer：

**`dfx start --clean`**

--clean选项从项目的缓存中删除检查点和过时的状态信息，以便您可以在纯净状态下重新启动Internet Computer副本和Web服务器进程。

但是请记住，如果通过运行dfx start --clean重置状态信息，那么现有Canister也将被删除。

运行dfx start --clean之后，运行以下命令来重新创建Canister：

**`dfx canister create --all`**

**`dfx build`**

**`dfx canister install --all`**

