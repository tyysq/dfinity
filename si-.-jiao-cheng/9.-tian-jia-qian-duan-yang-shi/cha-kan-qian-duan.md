# 查看前端

现在可以通过输入资源canister识别码访问默认程序的新的前端。

查看自定义前端步骤

1. 打开浏览器，导航到dfx.json配置文件中定义的地址和端口

例如，如果你使用的是默认的网络配置，可以导航到127.0.0.1:8000。

要指定想查看的canister，用下面的格式添加canisterId参数和custom\_greeting\_assets canister识别码到URL

```text
?canisterId=<YOUR-ASSET-CANISTER-IDENTIFIER>
```

完整的URL示例如下

```text
http://127.0.0.1:8000/?canisterId=cxeji-wacaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
```

    2. 验证你可以看到一个 My Contacts表单

例如

![](../../.gitbook/assets/image%20%283%29.png)

    3. 通过输入名称，地址和邮箱文本以及电话数字创建一个或多个记录，然后点击添加联系

    4. 清除表单内容并在查询名称中输入联系名称，然后点击Lookup查看保存的联系信息

记住你输入的Lookup名称必须完全匹配你输入的名称

