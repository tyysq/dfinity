# 添加未授权的用户身份



现在，您已经看到了一个简单的示例，该示例创建具有特定角色和权限的用户。 下一步是创建未分配给角色或未授予任何特殊权限的用户身份。

1. 进入项目目录
2. 查看当前活动用户

```text
dfx identity whoami
```

    3. 通过运行以下命令来创建新的用户身份：

```text
dfx identity new bob_standard
```

输出类似以下内容：

```text
Creating identity: "bob_standard".
Created identity: "bob_standard".
```

    4. 通过运行以下命令，将bob\_standard用户的账户存储在环境变量中：

```text
BOB_ID=$(dfx --identity bob_standard canister --no-wallet call access_hello callerPrincipal | sed 's/[\\(\\)]//g')
```

    5. 尝试使用bob\_standard身份分配角色。

```text
dfx --identity bob_standard canister --no-wallet call access_hello assign_role "($BOB_ID, opt variant{authorized})"
```

此命令返回unauthorized的错误。

    6. 尝试通过运行以下命令使用默认用户身份为bob\_standard分配owner角色：

```text
dfx --identity default canister --no-wallet call access_hello assign_role "($BOB_ID, opt variant{owner})"
```

该命令失败，因为无法为用户分配owner角色。

    7. 通过运行以下命令，使用bob\_standard用户身份调用greet函数：

```text
dfx --identity bob_standard canister --no-wallet call access_hello greet "Bob"
```

输出类似以下内容：

**`("Greetings, Bob. Nice to meet you!")`**

