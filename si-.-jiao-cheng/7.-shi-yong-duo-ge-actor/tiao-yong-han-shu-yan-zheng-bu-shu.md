# 调用函数验证部署



现在你已经在本地网络部署了三个canister并且可以通过dfx canister call命令分别测试

测试步骤

1. 使用dfx canister call命令调用assistant canister，使用addTodo函数并传递要添加的任务

```text
dfx canister call assistant addTodo '("Schedule monthly demos")'
```

1. 使用showTodos函数验证命令返回的to-do list

```text
dfx canister call assistant showTodos
```

 命令输出

```text
("
___TO-DOs___
(1) Schedule monthly demos")
```

1. 使用dfx canister call命令调用rock\_paper\_scissors canister，使用contest函数

```text
dfx canister call rock_paper_scissors contest
```

 命令输出

```text
("Bob won")
```

1. 使用dfx canister call命令调用daemon canister，使用launch函数

```text
dfx canister call daemon launch
```

1. 验证launch模拟函数返回“The daemon process is running”信息

```text
(""The daemon process is running"")
```

