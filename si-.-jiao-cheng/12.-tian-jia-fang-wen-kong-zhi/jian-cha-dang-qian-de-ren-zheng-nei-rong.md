# 检查当前的认证内容



在创建任何其他身份之前，让我们查看与您的默认身份相关联的账户标识符以及该默认身份的cycles钱包。 在Internet Computer上，账户是用户，Canister，节点或子网的内部代表。 账户的文本表示形式是使用账户数据类型显示的外部标识符。

要查看您当前的身份和账户：

1. 通过运行以下命令来验证当前活动身份：

dfx identity whoami

该命令显示的输出类似于以下内容：

```text
default
```

    2. 通过运行以下命令，检查账户以获取默认用户身份：

```text
dfx identity get-principal
```

输出类似以下内容：

**`zen7w-sjxmx-jcslx-ey4hf-rfxdq-l4soz-7ie3o-hti3o-nyoma-nrkwa-cqe`**

    3. 通过运行以下命令来检查与默认用户关联的角色：

```text
dfx canister call access_hello my_role

```

输出类似以下内容：

**`(opt variant { owner })`**

