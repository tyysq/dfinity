# 本地项目部署

部署程序到 ICP 网络需要 WebAssembly 模块和 canister\_manifest.json 文件

部署步骤：

1. 进入项目目录
2. 运行命令

**`dfx canister install --all`**

 命令输出

```text
Installing code for canister explore_hello, with canister_id rwlgt-iiaaa-aaaaa-aaaaa-cai
Installing code for canister explore_hello_assets, with canister_id rrkah-fqaaa-aaaaa-aaaaq-cai
```

运行下面的命令调用程序相关函数

**`dfx canister call explore_hello greet everyone`**

命令参数

* explore\_hello 调用的 Canister 名称或应用服务
* greet 调用的方法
* everyone 传给 greet 函数的参数
* 命令会显示 greet 函数的输出

**`("Hello, everyone!")`**

