# 部署和测试程序

在部署和测试程序之前，您需要执行以下操作：

* 连接到Internet Computer网络，该网络可以在您的开发环境中本地运行，也可以在您可以访问的子网中远程运行。
* 为应用注册一个特定网络标识

在本地部署和测试：

1. 在本地计算机上打开一个新的终端窗口或选项卡。

例如，如果在macOS上运行Terminal，请单击Shell，然后选择New Tab在当前工作目录中打开一个新终端。

    2. 通过运行以下命令，在第二个终端中的本地计算机上启动Internet Computer网络：

**`dfx start`**

    3. 通过运行以下命令，为reverse应用程序注册唯一的容器标识符

**`dfx canister create --all`**

    4. 通过运行以下命令在本地网络上部署默认程序：

**`dfx canister install --all`**

    5. 通过运行以下命令在程序中调用go函数：

```text
dfx canister call reverse go reward
("drawer")
```

您可以在[示例库](https://github.com/dfinity/examples/tree/master/c)中找到C程序的其他示例。

