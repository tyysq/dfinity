# 注册构建并部署应用



在开发环境中连接到本地ICP网络后，就可以在本地注册构建部署应用了。

部署应用步骤

1. 检查是否在项目根目录
2. 注册构建并部署应用命令

dfx deploy

如果你可以访问远程ICP网络，你可以使用--netowrk选项和dfx.json文件中定义的网络配置指定要部署的网络。例如，如果你连接到了ic指定的网络，可以运行下面的命令：

**`dfx deploy --network ic`**

dfx deploy命令会输出执行的操作信息，例如：

```text
Deploying all canisters.
Creating canisters...
Creating canister "assistant"...
"assistant" canister created with canister id: "75hes-oqbaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q"
Creating canister "daemon"...
"daemon" canister created with canister id: "cxeji-wacaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q"
Creating canister "rock_paper_scissors"...
"rock_paper_scissors" canister created with canister id: "7kncf-oidaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q"
```

