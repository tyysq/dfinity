# 注册构建并部署应用



连接到本地开发环境的Internet Computer网络后，可以在本地注册，构建和部署应用程序。

1. 进入项目根目录
2. 通过运行以下命令来注册，构建和部署您的应用程序：

```text
dfx deploy --argument '(360000000000)'
```

本示例将Canister的容量设置为360,000,000,000个Cycles。 dfx deploy命令输出显示有关其执行的操作的信息，包括与为此本地项目创建的钱包Canister关联的标识以及钱包Canister标识符。

例如：

```text
Deploying all canisters.
Creating canisters...
Creating canister "cycles_hello"...
Creating the canister using the wallet canister...
Creating a wallet canister on the local network.
The wallet canister on the "local" network for user "default" is "rwlgt-iiaaa-aaaaa-aaaaa-cai"
"cycles_hello" canister created with canister id: "rrkah-fqaaa-aaaaa-aaaaq-cai"
Creating canister "cycles_hello_assets"...
Creating the canister using the wallet canister...
"cycles_hello_assets" canister created with canister id: "ryjl3-tyaaa-aaaaa-aaaba-cai"
Building canisters...
Building frontend...
Installing canisters...
Installing code for canister cycles_hello, with canister_id rrkah-fqaaa-aaaaa-aaaaq-cai
Installing code for canister cycles_hello_assets, with canister_id ryjl3-tyaaa-aaaaa-aaaba-cai
Authorizing our identity (default) to the asset canister...
Uploading assets to asset canister...
Deployed canisters.
```

