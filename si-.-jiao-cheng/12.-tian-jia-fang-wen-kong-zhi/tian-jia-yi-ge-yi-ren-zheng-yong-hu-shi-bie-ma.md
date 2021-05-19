# 添加授权用户身份



此时，您具有owner角色的默认用户身份和具有admin角色的ic\_admin用户身份。 让我们添加另一个用户身份，并将其分配给authorized角色。 但是，在此示例中，我们将使用环境变量来存储用户的账户。

要添加新的authorized用户身份：

1. 进入项目目录
2. 通过运行以下命令来创建新的authorized用户身份：

```text
dfx identity new alice_auth
```

输出类似以下内容：

```text
Creating identity: "alice_auth".
Created identity: "alice_auth".
```

    3. 通过运行以下命令，将当前活动的身份切换为新的alice\_auth用户身份：

```text
dfx identity use alice_auth
```

    4. 通过运行以下命令，将alice\_auth用户的账户存储在环境变量中：

**`ALICE_ID=$(dfx canister --no-wallet call access_hello callerPrincipal | sed 's/[\\(\\)]//g')`**

您可以通过运行以下命令来验证存储的账户：

```text
echo $ALICE_ID
```

输出类似以下内容：

```text
principal "b5quc-npdph-l6qp4-kur4u-oxljq-7uddl-vfdo6-x2uo5-6y4a6-4pt6v-7qe"
```

    5. 通过运行以下命令，使用ic\_admin身份将授权角色分配给alice\_auth：

```text
dfx --identity ic_admin canister --no-wallet call access_hello assign_role "($ALICE_ID, opt variant{authorized})"
```

    6. 调用my\_role函数以验证角色分配。

```text
dfx --identity alice_auth canister --no-wallet call access_hello my_role
```

 输出类似以下内容：

```text
(opt variant { authorized })
```

    7. 通过运行以下命令，使用刚刚分配了authorized角色的alice\_auth用户身份调用greet函数：

```text
dfx canister --no-wallet call access_hello greet "Alice"
```

输出类似以下内容：

```text
(
  "Welcome, Alice. You have an authorized account. Would you like to play a game?",
)
```

