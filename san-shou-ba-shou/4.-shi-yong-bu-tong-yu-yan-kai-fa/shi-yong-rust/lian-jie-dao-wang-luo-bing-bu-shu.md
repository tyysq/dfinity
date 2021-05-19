# 连接到网络并部署



在您部署和测试程序之前，您有以下工作要做：

* 连接您开发环境Internet Computer网络本地运行或连接到您能访问的子网上远程运行
* 为您的应用注册一个网络特定标识符
* 编译带有WebAssembly输出目标的程序

因为您使用编译成WebAssembly的cargo build命令配置了自定义dfx.json文件，所以可以使用dfx命令行接口和标准工作流程来执行所有其余步骤。

本地生成和部署：

1. 如有必要，用pwd命令来检查您是否仍在项目目录下
2. 打开一个新的终端窗口或tab页并进入项目目录

例如，在macOS终端上执行以下任一操作：

* 单击Shell，在当前工作目录选择新选项卡以打开新的终端
* Click Shell and select New Window, then run cd ~/ic-projects/location\_hello in the new terminal if your location\_hello project is in the ic-projects working folder. 点击Shell，选择新窗口，在新终端运行cd ~/ic-projects/location\_hello（如果location\_hello项目在ic-projects工作目录）

您现在应该打开了两个已进入当前工作目录的终端

    3. 运行以下命令在本地计算机上启动Internet Computer网络

**`dfx start`**

根据您的平台和本地安全设置，您可能会看到一个警告。如果提示您允许或拒绝传入网络连接，请单点允许

    4. 离开网络操作显示信息的终端并切换到原来的终端

    5. 运行以下命令为应用注册一个唯一Canister标识符：

**`dfx canister create --all`**

    6. 运行以下命令生成程序：

**`dfx build`**

    7. 运行以下命令在本地部署程序：

**`dfx canister install --all`**

    8. 从命令行或浏览器测试功能

