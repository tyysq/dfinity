# 创建一个最小的配置文件

接下来，您需要准备一个简单的配置文件，标识了能安装在Internet Computer上的reverse二进制包和一个build目录，以便您能使用dfx命令行接口来作为Canister安装并运行。

准备配置文件和构建目录：

1. 使用以下命令来创建一个带有canisters键的dfx.json文件

```text
echo '{"canisters":{"reverse":{"main":"reverse"}}}' > dfx.json
copy
```

    2. 使用以下命令创建一个build目录

**`mkdir build`**

    3. 运行以下命令创建一个reverse目录

**`mkdir build/reverse`**

    4. 运行以下命令拷贝WebAssembly模块到新的build/reverse目录

**`cp reverse.wasm build/reverse/`**

