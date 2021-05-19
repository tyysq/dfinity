# 查询Canister

现在，项目已经部署到本地ICP网络，并且可以使用dfx canister call命令进行测试。

测试部署的程序步骤如下

1. 使用dfx canister call命令调用hello函数

```text
dfx canister call actor_hello hello
```

    2. 验证hello函数在本地网络进程中输出了相应的检查消息

例如，程序会输出类似以下内容

```text
[Canister rrkah-fqaaa-aaaaa-aaaaq-cai] Hello, World from DFINITY
```

注意"Hello, World from DFINITY" 只会出现在显示本地ICP网络活动的命令行中。

