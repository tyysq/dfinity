# 注册 Canister 识别码

连接到本地开发 ICP 网络后，可以为项目注册一个网络中唯一的 Canister 识别码。

在[快速开始](../../yi-kuai-su-ru-men/)章节中，这一步会在 dfx deploy 命令中执行。这片教程演示如何独立执行这些命令。

在本地网络注册 Canister 识别码步骤：

进入项目根目录

运行下面的命令注册 Canister 识别码

**`dfx canister create --all`**

命令会显示定义在 dfx.json 配置文件里的 Canster 在本地网络唯一的 Canister 识别码。

```text
Creating canister "explore_hello"...
"explore_hello" canister created with canister id: "rwlgt-iiaaa-aaaaa-aaaaa-cai"
Creating canister "explore_hello_assets"...
"explore_hello_assets" canister created with canister id: "rrkah-fqaaa-aaaaa-aaaaq-cai"
```

如果你连接的是本地开发 ICP 网络，这些 Canister 识别码只在本地有效，并存储在项目的.dfx/local/canister\_ids.json 文件。

文件内容示例：

```text
{
  "explore_hello": {
    "local": "rwlgt-iiaaa-aaaaa-aaaaa-cai"
  },
  "explore_hello_assets": {
    "local": "rrkah-fqaaa-aaaaa-aaaaq-cai"
  }
}
```

