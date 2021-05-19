# 测试应用



在本地Internet Computer网络上部署该应用程序之后，您可以使用dfx canister call命令尝试钱包功能并测试程序。

1. 通过运行以下命令，检查账户以获取默认用户身份：

dfx canister call cycles\_hello owner

该命令针对当前身份显示类似于以下内容的输出：

```text
(principal "g3jww-sbmtm-gxsag-4mecu-72yc4-kef5v-euixq-og2kd-sav2v-p2sb3-pae")
```

如果您尚未更改用于运行dfx deploy命令的身份，则应通过运行dfx identity get-principal命令获得相同的账户。 这很重要，因为您必须是钱包Canister的所有者才能执行某些任务，例如Cycles周期或授予其他保管者身份发送Cycles的权限。

    2. 通过运行以下命令检查初始钱包Cycles余额：

```text
dfx canister call cycles_hello wallet_balance
```

您尚未向Canister发送任何Cycles，因此该命令显示以下余额：

**`(0)`**

    3. 通过运行类似以下命令，从默认的钱包Canister发送到cycles\_hello：

```text
dfx canister call rwlgt-iiaaa-aaaaa-aaaaa-cai wallet_send '(record { canister = principal "rrkah-fqaaa-aaaaa-aaaaq-cai"; amount = (256000000000:nat64); } )'
```

    4. 调用wallet\_balance函数，以查看cycles\_hello Canister具有的Cycles数量

```text
dfx canister call cycles_hello wallet_balance
```

该命令显示的输出类似以下内容：

**`(256_000_000_000)`**

    5. 通过运行类似于以下命令，调用wallet\_balance函数以查看默认钱包中的Cycles数：

dfx canister call rwlgt-iiaaa-aaaaa-aaaaa-cai wallet\_balance

该命令使用Candid格式返回钱包Canister的余额记录。 例如，该命令可能显示一条记录，其中包含金额字段（由哈希3\_573\_748\_184表示），余额为97,738,624,621,042个Cycles，如下所示：

**`(record { 3_573_748_184 = 97_738_624_621_042 })`**

对于这个简单的教程，Cycles仅从默认钱包Canister中的余额中消耗，而不是从cycles\_hello Canister中消耗。

    6. 通过运行类似于以下命令的命令来调用greet函数：

```text
dfx canister call cycles_hello greet '("from DFINITY")'
```

    7. 重新调用wallet\_balance函数，以查看从默认钱包中扣除的Cycles数：

```text
dfx canister call rwlgt-iiaaa-aaaaa-aaaaa-cai wallet_balance
```

例如，您可能会得到类似以下的结果：

**`(record { 3_573_748_184 = 97_638_622_179_500 })`**

