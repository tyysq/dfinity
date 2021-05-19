# 创建一个最小接口描述文件



在标准开发工作流程中，运行dfx build命令会在Canister的输出目录中创建多个文件，包括一个或多个Candid接口描述（.did）文件，这些文件处理与程序功能关联的数据类型的类型匹配。

有关用于不同数据类型的语法的详细信息，请参见Candid[规范](https://github.com/dfinity/candid/tree/master/spec)和[指导](https://sdk.dfinity.org/docs/candid-guide/candid-intro.html)。

为此程序创建一个Candid接口描述文件：

1. 在您为reverse.c程序源创建的build目录中打开一个终端
2. 创建一个名为reverse.did的新文本文件。
3. 添加go函数的描述。

例如：

```text
service : {
 "go": (text) -> (text);
}
```

    4. 保存并关闭文件

