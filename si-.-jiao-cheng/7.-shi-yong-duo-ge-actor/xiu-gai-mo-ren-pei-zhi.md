# 修改默认配置



在探索默认项目章节，已经介绍了创建新项目会添加一个dfx.json配置文件到项目目录。在本章节中，需要修改一些默认配置指定定义actor的程序位置。

dfx.json配置修改步骤

1. 在编辑器中，打开 dfx.json 配置文件，然后修改默认的multiple\_actors canister名称和源码目录为assistant

例如，在canisters键：

```text
"assistant": {
 "main": "src/assistant/main.mo",
 "type": "motoko"
 },
```

由于你已经在配置文件中添加了这个canisters的设置，你必须要在大括号后面添加一个逗号来包裹assistant的配置。

    2. 删除文件中的multiple\_actors\_assets键

    3. 为rock\_paper\_scissors和daemon程序添加新的canister名称，源码位置和类型。

修改后的配置文件如下

```text
{
  "canisters": {
    "assistant": {
      "main": "src/assistant/main.mo",
      "type": "motoko"
    },
    "rock_paper_scissors": {
      "main": "src/rock_paper_scissors/main.mo",
      "type": "motoko"
    },
    "daemon": {
      "main": "src/daemon/main.mo",
      "type": "motoko"
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

    4. 保存并关闭配置文件继续

    5. 运行下面的命令修改默认源码文件名称匹配dfx.json文件中的配置

```text
cp -r src/multiple_actors/ src/assistant/
```

    6. 运行下面的命令复制assistant源码文件目录为rock\_paper\_scissors acotr创建主程序文件

```text
cp -r src/assistant/ src/rock_paper_scissors/
```

    7. 运行下面的命令复制assistant源码文件目录为daemon创建主程序文件

```text
cp -r src/assistant/ src/daemon/
```

