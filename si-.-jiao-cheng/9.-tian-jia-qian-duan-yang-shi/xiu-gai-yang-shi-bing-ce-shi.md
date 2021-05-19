# 修改样式并测试

查看完联系人应用后，你也许想做一些修改

修改样式属性

1. 编辑器中打开src/contacts\_assets/public/mycontacts.css文件并修改样式配置

例如，你可能想要修改背景颜色或者输入表单样式

    2. 运行下面的命令重新构建项目

```text
dfx build
```

    3. 运行下面的命令部署项目

```text
dfx canister install --all --mode upgrade
```

    4. 浏览器中刷新页面查看结果

