# 部署项目



`dfx build --check` 命令不会部署到任何ICP网络。如果要部署本项目，需要做以下步骤

* 连接ICP网络
* 注册网络Canister识别码
* 部署Canister

在部署项目前，必须了解到本地运行或远程的ICP网络。连接到ICP网络后，必须生成一个独一无二，网络绑定的Canister识别码来替换本地定义的识别码。

本地部署步骤

1. 打开命令行，进入项目目录
2. 启动本地ICP网络

```text
dfx start --background
```

 本教程中，使用--background 选项启动在后台启动ICP网络。使用这个选项后，你可以继续输入命令无需打开另一个命令行窗口。

    3. 使用下面的命令为项目在本地ICP网络生成一个新的Canister识别码

```text
dfx canister create actor_hello
```

 输出下面的内容

```text
Creating a wallet canister on the local network.
The wallet canister on the "local" network for user "pubs-id" is "rwlgt-iiaaa-aaaaa-aaaaa-cai"
Creating canister "actor_hello"...
"actor_hello" canister created with canister id: "rrkah-fqaaa-aaaaa-aaaaq-cai"
```

dfx canister create 命令会存储网络绑定的canister识别码到.dfx/local目录下的

canister\_ids.json文件

例如

```text
{
  "actor_hello": {
    "local": "rrkah-fqaaa-aaaaa-aaaaq-cai"
  }
}
```

    4. 使用下面的命令在本地ICP网络部署actor\_hello 项目

```text
dfx canister install actor_hello
```

 命令输出

```text
Installing code for canister actor_hello, with canister_id rrkah-fqaaa-aaaaa-aaaaq-cai
```

