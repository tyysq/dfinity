# 默认配置



检查默认配置步骤如下

1. 打开命令行
2. 进入项目目录

**`cd explore_hello`**

    3. 在编辑器中，打开 dfx.json 配置文件

```text
{
  "canisters": {
    "explore_hello": {
      "main": "src/explore_hello/main.mo",
      "type": "motoko"
    },
    "explore_hello_assets": {
      "dependencies": [
        "explore_hello"
      ],
      "frontend": {
        "entrypoint": "src/explore_hello_assets/public/index.js"
      },
      "source": [
        "src/explore_hello_assets/assets",
        "dist/explore_hello_assets/"
      ],
      "type": "assets"
    }
  },
  "defaults": {
    "build": {
      "packtool": ""
    }
  },
  "dfx": "0.6.26",
  "networks": {
    "local": {
      "bind": "127.0.0.1:8000",
      "type": "ephemeral"
    }
  },
  "version": 1
}
```

默认配置

* canisters 字段指定项目的 WebAssembly 模块名称为 explore\_hello
* canisters.explore\_hello 中的 main 字段指定被编译的 main 程序文件路径，这里是 src/explore\_hello/main.mo，type 字段指定语言类型，这里是 motoko
* canisters.explore\_hello\_assets 字段指定项目的前端资源信息
* dfx 配置被用来指定创建项目的软件版本
* netowrks 字段指定连接的网络信息。默认配置会将 ICP 网络绑定到本地地址 127.0.0.1，端口 8000。

 如果可以访问其他 ICP 网络提供商，可以在 networks 字段中包含相关的 URL 来连接。

    4. 关闭 dfx.json 文件继续

