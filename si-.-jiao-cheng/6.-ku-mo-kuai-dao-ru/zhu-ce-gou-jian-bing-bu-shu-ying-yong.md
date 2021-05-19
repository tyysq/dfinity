# 注册构建并部署应用

在开发环境中连接到本地ICP网络后，就可以在本地注册构建部署应用了。

部署应用步骤

1. 检查是否在项目根目录
2. 注册构建并部署应用命令

```text
dfx deploy phonebook
```

dfx.json文件提供创建应用前端入口的默认配置和asset canister

在前面的章节中，我们删除了asset canister项因为我们不需要应用前端。删除用不到的文件可以让项目目录保持简介。虽然不需要做这些，但是在dfx.json文件中保留asset canister也没什么坏处。例如，你之后可能想添加前端资源。

这个教程中，可以使用dfx deploy phonebook目录来只部署后台canister，因为项目是一个基于命令行的程序不需要前端资源

虽然这个教程描述了如何跳过前端canister编译，但是你可以之后为应用添加一个简单的用户界面，相关内容可以查看[exmaples](https://github.com/dfinity/examples)代码库中的[phone-book](https://github.com/dfinity/examples/tree/master/motoko/phone-book)项目

