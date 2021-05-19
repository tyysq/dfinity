# 如何使用

如前面的讨论那样，Candid提供了一种与语言无关的方式来与Canister进行交互。 无论您是使用dfx命令行界面，通过Web浏览器还是使用JavaScript，Motoko，Rust或其他语言编写的程序从终端与Internet Computer进行交互，通过使用Candid，您可以指定输入参数值和显示Canister的method的返回值。 既然您熟悉了Candid是什么以及它如何工作，那么本节提供了有关在某些常见情况下如何使用它的说明。

举一个具体的例子，我们假设已经在网络上部署了带有以下Candid接口的叫做Counter的Canister：

```text
service Counter : {
 inc : (step: nat) -> (nat);
}
```

现在，让我们在Candid的帮助下，探索如何在不同情况下与该容器进行交互。

**与终端中的service（服务）进行交互**

与Canister和InternetComputer交互的最常见方法之一是使用DFINITY容器SDK dfx命令行界面。

dfx工具提供了dfx Canister call的调用命令，以调用特定的已部署的Canister-本质上是在Internet计算机上运行的service服务-以及该服务的方法（如果适用）。

运行dfx Canister call调用命令时，可以通过将参数指定为Candid文本值的方式，来将参数传递给method（方法）。

在命令行上传递Candid文本值时，可以指定多个参数值，这些参数值之间用逗号（，）分隔并括在括号内。 例如，指定（42，true）表示两个参数值，其中第一个参数是数字42，第二个参数是布尔值true。

以下示例说明了如何使用dfx canister call调用命令，来调用叫做Counter的Canister service（服务）并传递inc方法的参数：

**`$ dfx canister call counter inc '(42)'`**

**`(43)`**



您也可以省略参数并让dfx生成与method（方法）的类型匹配的随机值。 例如：

**`$ dfx canister call counter inc`**

**`Unspecified argument, sending the following random argument:`**

**`(1_543_454_453)`**

**`(1_543_454_454)`**

有关使用dfx和dfx Canister call调用命令的更多信息，请参阅'命令行参考'和'dfx Canister'文档。

**与浏览器中的service（服务）进行交互**

Candid接口描述语言提供了一种通用语言，用于指定Canister的service（服务）的签名。 基于该服务的类型签名，Candid提供了一个Web界面-Candid UI-使您可以从Web浏览器中调用Canister的函数进行测试和调试，而无需编写任何前端代码。

要使用Candid的web接口来测试\`counter' Canister：

1. 使用dfx Canister id counter的ID计数器命令找到与Candid的counter关联的Canister标识符。
2. 打开浏览器并导航到dfx.json配置文件中指定的地址和端口号。 默认情况下，局域网绑定到127.0.0.1:8000地址和端口号。
3. 添加candid端点以访问Candid Web界面，后跟必需的canister ID参数和Canister标识符。例如，完整的URL应该类似于以下内容，但带有由dfx canister id命令返回的canister\_identifier：

```text
http://127.0.0.1:8000/candid?canisterId=<YOUR-CANISTER-IDENTIFIER>
```

    4. 查看程序中定义的函数调用和类型列表。

    5. 为函数键入适当类型的值或单击\`\`Random随机''生成一个值，然后单击\`\`Call调用''或\`\`query查询''以查看结果。

有关从任何Canister的Candid 接口创建Web接口的工具的详细信息，请参阅“ [Candid UI](https://github.com/dfinity/candid/tree/master/tools/ui)”存储库。

**与Motoko的Canister中的service服务进行交互**

如果你用Motoko编写一个service（服务），则Motoko编译器会自动将Canister的顶级actor或actor类的签名转换为Candid描述，并且dfx build命令可确保在需要的地方正确引用了服务描述。

例如，你要用Motoko来编写一个叫hello 的Canister来调用叫做Counter的 Canister：

```text
import Counter "canister:Counter";
import Nat "mo:base/Nat";
actor {
 public func greet() : async Text {
 let result = await Counter.inc(1);
 "The current counter is " # Nat.toText(result)
 };
}
```

在这个示例子中，当dfx build命令处理这个Counter Canister的附属信息时-impoot Counterd''canister：Counter''声明，dfx build命令确保将Counter Canister标识符和Candid描述正确地传递给Motoko 编译器。 然后，Motoko编译器会将Candid的类型转换为对应的Motoko的原生类型。 通过这种转换，即使这个Counter Canister是用其他语言编写的，即使您没有导入Canister的源代码，也可以像Motoko的函数一样调用inc method（方法）。 有关Candid和Motoko之间的类型映射的其他信息，您可以查阅“Supported types支持的类型”参考部分。

Motoko编译器和dfx build命令还会自动生成hello Canister的Candid描述，以允许其他Canister或工具与hello Canister无缝交互。 生成的Candid描述位于项目构建目录中的.dfx / local / canisters / hello / hello.did中。

**与用Rust编写的Canister 中的服service进行交互**

如果您用Rust编写Canister，则dfx build命令可确保在需要的地方正确引用了servixe（服务）描述。 但是，您需要遵循''Candid规范''中规定的描述来手动编写Candid服务描述。

例如，你要用Rust语言编写一个hello Canister来调用这个叫做counter的Canister：

```text
use ic_cdk_macros::*;
#[import(canister = "counter")]
struct Counter;
#[update]
async fn greet() -> String {
 let result = Counter::inc(1.into()).await;
 format!("The current counter is {}", result)
}
```

当导入的counter canister上的宏由dfx build命令处理时-即（＃\[import（canister =“ counter”）\]\]声明），dfx build命令会确保Counter canister的标识符和Candid描述正确地传递给Rust CDK。 然后，Rust CDK将Candid的类型转换为适对应的Rust的类型。 通过这种转换，即使Counter canister是用其他语言编写的，即使您没有导入canister的源代码，也可以像调用Rust函数一样直接调用inc方法。 有关Candid和Rust之间的类型映射的其他信息，您可以查阅\`\`Supported types支持的类型''。

要使其他Canister和工具与Hello canister交互，您需要手动创建一个.did文件：

```text
service : {
 greet : () -> (text);
}
```

还有一个实验功能可以自动生成Candid的service的描述，请参阅这个'测试案例'作为示例。

有关可帮助您在Rust中创建Candid service或canister的其他信息和库，请参阅\`\`Candid  crate''，\`\`Rust CDK示例''和'Rust教程'的文档。

**与用JavaScript编写的service的交互**

dfinity / agent npm软件包包括支持使用Candid导入canister的功能。

例如，如果要调用counter canister，则可以编写以下JavaScript程序：

```text
import counter from 'ic:canisters/counter';
import BigNumber from 'bignumber.js';
(async () => {
 const result = await counter.inc(new BigNumber(42));
 console.log("The current counter is " + result.toString());
})();
```

当使用dfx build命令和webpack配置处理导入counter canistee的附属信息时，改处理可确保将canister标识和Candid描述正确传递给JavaScript程序。 在后台，通过dfx构建将Candid服务描述转换为JavaScript模块，位于.dfx / local / canister / counter / counter.did.js。 然后，dfinity / agent程序包将Candid的类型转换为JavaScript值，并使您可以本地调用inc方法（就像是JavaScript函数一样），即使countee canister是用其他语言编写的，即使您没有 导入的canister的源代码。 有关Candid和JavaScript之间的类型映射的其他信息，您可以查阅“支持的类型”参考部分。

**创建一个新的Candid**

除了可以用Motoko，Rust和JavaScript编写Candid之外，还有社区支持的Candid库，适用于以下host语言：

* [Haskell](https://hackage.haskell.org/package/candid)
* [Elm](https://github.com/chenyan2002/ic-elm/)
* [Kotlin](https://github.com/seniorjoinu/candid-kt)
* [AssemblyScript](https://github.com/rckprtr/cdk-as/tree/master/packages/cdk/assembly/candid)

如果你想要创建运行一个Candid来支持当前无法直接支持的语言或工具，则应查阅[Candid规范](https://github.com/dfinity/candid/blob/master/spec/Candid.md)。

如果你已经创建运行了一个Candid来支持新的语言或工具，则可以使用官方的[Candid测试数据](https://github.com/dfinity/candid/tree/master/test)来测试并验证您的程序是否与Candid兼容，即使在有些模糊的情况下也是如此。

