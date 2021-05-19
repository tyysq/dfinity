# 什么是Candid？

Candid是一种接口描述语言。它的主要目的是来描述Service（服务）的公共接口，通常表现为运行在互联网计算机的Canister的程序。Candid的主要优点之一是它与编程语言无关，并且允许使用不同编程语言（包括Motoko，Rust和JavaScript）来编写Service与前端之间进行交互操作的程序。

Candid中的典型接口描述可能如下所示：

```text
service counter : {
 add : (nat) -> ();
 subtract : (nat) -> ();
 get : () -> (int) query;
 subscribe : (func (int) -> ()) -> ();
}
```

在这个例子中，命名为counter（计数器） 的service（服务），包含了以下的公共方法（method）：

- Add方法和subtract方法改变counter的值。

- Get方法读取了Counter的当前数值

- Subscribe方法可用于调用另一个函数，例如，每次Counter的值更改时调用"通知回复"方法。

_如本示例所示，每个方法（method）都有一系列参数和结果类型。 方法（method）还包括用于特定于互联网计算机的Annotations（注释）， 如本示例中所示的query（查询）。_

_有了这个简单的接口描述，您就可以直接从命令行或通过基于Web的前端或通过Rust程序以编程方式或通过另一种编程或脚本语言调用Counter这个service（服务）。_

_除了互操作性之外，Candid还可以通过精确识别哪些变更可以执行并且不破坏现有客户数据，来支持服务接口的升级。 例如，您可以安全地向Service（服务）添加新的可选参数，而不会失去与现有客户端的兼容性。_

**为什么创建新的IDL？**

_第一眼看到这个的时候，你也许会想其他的语言，例如JSON，XML，或者Protobuf，已经足够了。然而，Candid拥有一个独特的融合特点，是这些技术所没有的。这个特点让Candid特别适合开发运行在互联网计算机上的应用，包括如下：_

*   _JSON，XML和Protobuf等许多语言仅描述如何将单个值映射到字节或字符。这些数据描述语言无法整体描述service（服务）的内容。 这些语言专注于要传输的数据类型，而不是使用这些数据类型的方法。_
*  _Candid实现将Candid值直接映射到Host语言的类型和值。 使用Candid，程序员无需构造或解构某些抽象的Candid值。_
*  _Candid定义了有关如何以合理且有条理的方式升级服务及其接口的规则。_
*  _Candid本质上是一种高级语言。 使用Candid，您不仅可以传递纯数据，还包括对服务和方法的引用。 Candid支持更高级别的安全升级。_
* _Candid内置了支持互联网计算机的功能，例如`query`_ 

**Candid** **类型和值**

_Candid是一个强类型的系统，具有一组规范地涵盖大多数用途的类型。 它有：_

* _无界整数类型（nat, int）_
* _有界整数类型\(nat8, nat16, nat32, nat64, int8, int16, int32, int64\)_
* _浮点类型\(float32, float64\)_
* _布尔类型（bool）_
* _文本（text）和二进制（blob）数据的类型_
* _容器类型，包括变量（opt，vec，record，variant）_
* _引用类型（service, func, principal）_
* _特殊的空值，保留和空类型_

_所有类型均在“_[_参考_](can-kao.md)_”这一章中进行了详细描述_

_这组类型背后的理念是，它们能充分描述数据的结构，因此可以对信息进行编码，传递和解码，但有意不描述超出描述所需要的语义约束。 例如，无法表达数字应该是偶数，向量具有一定的长度或向量的元素已排序。_

**Candid的service（服务）描述**

_如果你熟悉了Candid类型，就可以使用它们来描述service（服务）。  Candid的service描述文件（.DID文件）可以手工编写，也可以从service执行中生成。_

_在探索如何为特定host语言生成service（服务）描述之前，让我们仔细研究一下service例子的描述的结构及其组成部分。_

_最简单的service描述是没有公共method（方法）的service，如下所示：_

_**`service : {}`**_

_这个service并没有什么功能，所以让我们增加一个简单的method，ping进去。_

_**`service : {`**_

  _**`ping : () -> ();`**_

_**`}`**_

_这个例子说明了一个service支持一个名称为ping的公共method（方法）。Method的名称可以是任意字符串，并且如果它们不是纯标识符，则可以将它们前后加上引号（“method with space”）。_

_Method声明了参数和结果类型的序列。 这个ping，不传递任何参数且不返回任何结果，因此空序列\`（）\`既用于参数又用于结果。_

_现在，您已经看到了最简单的例子，让我们考虑一个稍微复杂的service（服​​务）描述。 该服务由两个method（方法）-reverse和-divMod组成，每个方法都包含一系列参数和结果类型：_

_**`service : {`**_

  _**`reverse : (text) -> (text);`**_

  _**`divMod : (dividend : nat, divisor : nat) -> (div : nat, mod : nat);`**_

_**`}`**_

_方法reverce 需要输入一个text类型的参数，并返回一个text类型的值。_

_divMod方法需要输入两个均为nat类型的参数，并返回两个均为nat类型的值。_

**命名参数和结果**

_在前面的示例中，divMod方法的签名包括了参数和返回值的名称。 给某个method（方法）的参数或结果命名纯粹是出于文档目的。 您使用的名称不会更改方法的类型或所传递的值。 取而代之的是，参数和结果通过其位置来标识，而与名称无关。_

_特别地，Candid不会阻止您将类型更改为：_

  _divMod : \(dividend : nat, divisor : nat\) -&gt; \(mod : nat, div : nat\);_

_或将上面的divMod传递给需要首先返回值为mod的一种method（方法）的service（服务）。_

_因此，这与语义上相关的命名记录字段有很大不同。_

