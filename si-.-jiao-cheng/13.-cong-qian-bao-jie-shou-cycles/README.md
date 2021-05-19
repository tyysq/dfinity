# 13.从钱包接受cycles



在进行本地开发时，可以使用项目中的默认钱包发送Cycles并检查余额。 但是关于需要接收和燃烧这些Cycles以执行功能并向用户提供服务是如何工作的呢？ 本教程提供了一个简单的示例，以说明如何添加功能以接收Cycles并检查余额。

此示例包括以下内容：

* wallet\_balance函数使您可以检查Canister的当前Cycles余额。
* wallet\_receive函数使程序能够接受发送到Canister的Cycles。
* greet函数接受文本参数，并在终端中显示问候语。
* owner函数返回消息调用者使用的账户。

