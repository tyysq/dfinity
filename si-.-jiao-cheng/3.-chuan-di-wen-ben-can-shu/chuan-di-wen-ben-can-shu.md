# 传递文本参数

现在，项目已经部署到本地ICP网络，并且可以使用dfx canister call命令进行测试。

测试部署的程序步骤如下

1. 运行下面命令来调用程序的location 方法并传递文本类型的city参数

**`dfx canister call location_hello location "San Francisco"`**

         由于参数San和Francisco之间包含一个空格，需要给参数加引号。命令输出如下

**`("Hello, San Francisco!")`**

         如果参数不包含空格，可以让Candid接口描述语言推断数据类型，例如

**`dfx canister call location_hello location Paris`**

 Candid推断Paris是一个文本类型，并返回相应输出

**`("Hello, Paris!")`**

    2. 运行下面命令来调用程序的location 方法并显式地使用Candid接口描述语言规则来传递文本类型的city参数

**`dfx canister call location_hello location '("San Francisco and Paris")'`**

命令输出如下

**`("Hello, San Francisco and Paris!")`**

由于程序只接收一个文本参数，给出多个字符串只会使用第一个参数

例如，如果运行下面的命令

**`dfx canister call location_hello location '("San Francisco","Paris","Rome")'`**

 只有第一个参数，也就是 **`（“Hello，San Francisco！”）`**返回了。

