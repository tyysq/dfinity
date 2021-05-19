# 查看默认的前端

如果开发环境安装了 node.js，那么项目中会包含一个简单的前端示例，示例中的JavaScript模板脚本index.js会在浏览器中对接explore\_hello程序。

前端模板部署步骤

1. 打开命令行，进入项目目录
2. 打开src/explore\_hello\_assets/public/index.js文件，查看代码

```text
import explore_hello from 'ic:canisters/explore_hello';
explore_hello.greet(window.prompt("Enter your name:")).then(greeting => {
  window.alert(greeting);
});
```

模板文件index.js使用DOM描述Web文档的结构和内容

示例文件倒入创建的Canister并在一个提示框中调用greet函数。

    3. 关闭index.js文件继续

    4. 查看自动创建的前端资源文件

**`ls -l .dfx/local/canisters/explore_hello_assets/`**

 命令输出示例

```text
drwxr-xr-x  9 pubs  staff     288 Apr  6 14:25 assets
-r--r--r--  1 pubs  staff    2931 Dec 31  1969 assetstorage.did
-r--r--r--  1 pubs  staff  265823 Dec 31  1969 assetstorage.wasm
-rw-r--r--  1 pubs  staff    3651 Apr  6 14:25 explore_hello_assets.d.ts
-rw-rw-rw-  1 pubs  staff    2931 Dec 31  1969 explore_hello_assets.did
-rw-r--r--  1 pubs  staff    4236 Apr  6 14:25 explore_hello_assets.did.js
-rw-r--r--  1 pubs  staff     149 Apr  6 14:25 explore_hello_assets.js
-rw-rw-rw-  1 pubs  staff  265823 Dec 31  1969 explore_hello_assets.wasm
```

这些文件是使用node模块和index.js文件由 dfx build命令自动生成的

    5. 打开浏览器，进入在dfx.json中配置的网址127.0.0.1:8000

按下面到格式添加canisterId 参数和explore\_hello\_assets 容器识别码到URL

**`?canisterId=<YOUR-CANISTER-IDENTIFIER>`**

完整路径示例

**`http://127.0.0.1:8000/?canisterId=rrkah-fqaaa-aaaaa-aaaaq-cai`**

    6. 查看HTML页面

![](../../.gitbook/assets/image%20%289%29.png)

    7. 点击Click Me来调用greeting函数

![](../../.gitbook/assets/image%20%2822%29.png)

