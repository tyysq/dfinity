# 使用insert函数添加名字和数字

现在，项目已经部署到本地ICP网络，并且可以使用dfx canister call命令进行测试。

测试部署的程序步骤如下

1. 运行下面命令来调用程序的phonebook canister的insert 方法并传递名称和电话号码参数

```text
dfx canister call phonebook insert '("Chris Lynn", "01 415 792 1333")'
```

    2. 运行下面的命令添加第二个名称和号码对

```text
dfx canister call phonebook insert '("Maya Garcia", "01 408 395 7276")'
```

    3. 运行下面的命令调用lookup函数并传入“CHris Lynn”参数验证

```text
dfx canister call phonebook lookup '("Chris Lynn")'
m
```

命令输出

```text
(opt "01 415 792 1333")
```

    4. 运行下面的命令调用lookup函数并传入“Maya Garcia”参数验证

```text
dfx canister call phonebook lookup '("01 408 395 7276")'
```

 注意这个命令返回null因为电话号码不是“Maya Garcia”的name键

    5. 尝试运行下面的命令再次调用lookup函数并传入“Maya Garcia”和“Chris Lynn”参数验证

由于程序只接受一个值，命令会返回第一个值对应的信息，在这里会返回“Maya Garcia”对应的电话号码

