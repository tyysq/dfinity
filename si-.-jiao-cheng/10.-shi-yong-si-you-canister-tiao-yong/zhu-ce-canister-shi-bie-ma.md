# 注册canister识别码

连接到本地ICP 网络后，你可以为你的项目在这个网络注册生成canister识别码。

在本地网络注册canister识别码步骤

1. 检查你当前是否在项目目录
2. 运行下面的命令注册canister识别码

```text
dfx canister create --all
```

 这个命令会为dfx.json配置文件中配置的canister输出网络绑定的canister识别码

```text
"connectd" canister created with canister id: "75hes-oqbaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q"
"linkedup" canister created with canister id: "cxeji-wacaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q"
"linkedup_assets" canister created with canister id: "7kncf-oidaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q"
```

记住由于你在本地运行ICP网络，这些识别码只在本地网络有效。为了在远程网络部署canister，你必须使用--network命令选项和一个特定的网络名称或地址来在相应网络注册识别码

