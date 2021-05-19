# 管理Canister运行状态

在Internet Computer上部署Canister之后，它可以开始接收和处理来自用户和其他Canister的请求。 可用于发送请求和接收回复的Canister被视为处于运行状态。

尽管默认情况下通常通常将Canister置于运行状态，但在某些情况下，您可能希望暂时或永久停止它。 例如，您可能要在升级之前停止。 停止Canister有助于对正在处理的，需要运行至完成或回滚的所有消息进行合适的处理。 您可能还想停止Canister以干净地清除其消息队列，这是删除Canister的先决条件。

您可以通过运行dfx canister status命令来检查所有或指定Canister的当前状态。 例如，要查看在本地Internet Computer网络上运行的所有Canister的状态，可以运行以下命令：

**`dfx canister status --all`**

如果Canister当前正在运行，返回的输出类似于以下内容：

```text
Canister status_check's status is Running.
Canister status_check_assets's status is Running.
```

您可以通过运行dfx canister stop命令来停止当前正在运行的Canister。

**`dfx canister stop --all`**

返回的输出类似于以下内容：

```text
Stopping code for canister status_check, 
with canister_id 75hes-oqbaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
Stopping code for canister status_check_assets, 
with canister_id cxeji-wacaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
```

如果要重新运行dfx canister status命令，则可能会看到“已停止”状态，表明没有待处理的消息，或者“正在停止”状态，表明有正在处理的消息需要处理。

要重新启动Canister（例如，在成功升级之后），您可以运行dfx canister start命令。 例如，要重新启动在本地Internet Computer网络上运行的所有Canister，运行以下命令：

**`dfx canister start --all`**

返回的输出类似于以下内容：

```text
Starting code for canister status_check, 
with canister_id 75hes-oqbaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
Starting code for canister status_check_assets, 
with canister_id cxeji-wacaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
```

