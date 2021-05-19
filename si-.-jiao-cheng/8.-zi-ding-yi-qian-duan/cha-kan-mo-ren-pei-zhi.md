# 查看默认配置



在修改代码前，让我们看一下dfx.json中默认的前端配置。

查看dfx.json配置步骤

1. 编辑器中打开dfx.json
2. 注意到canister下包含了custom\_greeting的配置

```text
{
  "canisters": {
    ...


    "custom_greeting_assets": {
      "dependencies": [
        "custom_greeting"
      ],
      "frontend": {
        "entrypoint": "src/custom_greeting_assets/src/index.html"
      },
      "source": [
        "src/custom_greeting_assets/assets",
        "dist/custom_greeting_assets/"
      ],
      "type": "assets"
    }
  }
}
```

配置项解析

* 项目的前端资源会编译到自己的canister，在这里被称为custom\_greeting\_assets
* 资源canister默认以来项目的主要canister
* frontend.entrypoint指定了一个文件的路径-这里是index.html文件-作为项目入口使用。如果你希望有一个不同的入口文件-例如，自定义的first-page.html文件-你可以修改这一项。
* source设置制定了src和dist目录。src指定了构建项目时会包含到资源canister的静态资源目录。如果你有CSS或JavaScript文件，你可以把这些文件放在这个目录。构建完项目后，项目资源会保留在dist项指定的目录
* type配置指定了custom\_greeting\_assets是一个资源canister而不是程序canister

这篇教程中，我们会在一个index.jsx文件中添加React JavaScript，无需对dfx.json文件进行修改。

    3. 关闭dfx.json文件继续

