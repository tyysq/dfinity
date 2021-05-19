# 创建新用户

要开始测试我们程序中的访问控制，让我们创建一些新的用户身份并将这些用户分配给不同的角色。

1. 进入项目目录
2. 通过运行以下命令来创建新的管理用户身份：

```text
dfx identity new ic_admin
```

输出类似以下内容：

```text
Creating identity: "ic_admin".
Created identity: "ic_admin".
```

    3. 调用my\_role函数以查看您的新用户身份尚未分配的任何角色。

```text
dfx --identity ic_admin canister call access_hello my_role
```

输出类似以下内容：

```text
Creating a wallet canister on the local network.
The wallet canister on the "local" network for user "ic_admin" is "ryjl3-tyaaa-aaaaa-aaaba-cai"
(null)
```

    4. 通过运行以下命令，将当前活动用户切换为使用新的ic\_admin用户身份，并显示与ic\_admin用户关联的账户：

```text
dfx identity use ic_admin && dfx identity get-principal
```

输出类似以下内容：

```text
Using identity: "ic_admin".
c5wa6-3irl7-tuxuo-4vtyw-xsnhw-rv2a6-vcmdz-bzkca-vejmd-327zo-wae
```

    5. 通过运行以下命令，检查用于调用access\_hello Canister的账户：

```text
dfx canister call access_hello callerPrincipal
```

输出类似以下内容：

```text
(principal "ryjl3-tyaaa-aaaaa-aaaba-cai")
```

默认情况下，Cycles钱包标识符是用于调用access\_hello canister中的方法的账户。 但是，为了说明访问控制，我们要使用与用户关联的账户，而不是Cycles钱包。 不过，在进行此步骤之前，让我们为ic\_admin用户分配一个角色。 为此，我们需要切换到具有所有者角色的默认用户身份。

