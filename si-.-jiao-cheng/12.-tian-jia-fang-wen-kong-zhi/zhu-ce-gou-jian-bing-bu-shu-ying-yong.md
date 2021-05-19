# 注册构建并部署应用



连接到本地开发环境的Internet Computer网络后，可以通过运行dfx deploy命令在一个步骤中注册，构建和部署应用程序。 您还可以使用单独的dfx canister create，dfx build和dfx canister install命令独立执行每个步骤。

本地部署：

1. 检查是否在项目根目录
2. 通过运行以下命令来注册，构建和部署access\_hello后端程序：

dfx deploy access\_hello

```text
Creating a wallet canister on the local network.
The wallet canister on the "local" network for user "default" is "rwlgt-iiaaa-aaaaa-aaaaa-cai"
Deploying: access_hello
Creating canisters...
Creating canister "access_hello"...
"access_hello" canister created with canister id: "rrkah-fqaaa-aaaaa-aaaaq-cai"
Building canisters...
Installing canisters...
Installing code for canister access_hello, with canister_id rrkah-fqaaa-aaaaa-aaaaq-cai
Deployed canisters.
```

