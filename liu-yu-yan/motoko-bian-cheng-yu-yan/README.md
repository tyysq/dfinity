# Motoko 编程语言

_Motoko_ _编程语言将随着_ _DFINITY Canister SDK_ _的每个版本的更新和_ _Motoko_ _编译器的更新而不断发展。定期查看更新内容，并尝试新的功能。_

Motoko 编程语言是一种新的、现代的、可靠的编程语言，专为希望构建可以直接在互联网计算机上运行的下一代应用程序和服务上的开发人员而设计。Motoko 是专门设计来支持互联网计算机的独特功能，并提供一个熟悉但强大的编程环境。作为一种新的语言，Motoko 不断进化以支持新特性和不断改进。 请保持跟踪 Motoko 的更新和开源项目的公告。

**原生支持** **Canister**

Motoko 原生支持互联网电脑的“Canister”，这些“Canister”用 actors 来表示，是指封装了其状态，并采用异步通讯的具有自治对象。

```text
actor Counter {
 var value = 0;
 public func inc() : async Nat {
 value += 1;
 return value;
 };
}
```

\*\*\*\*

**顺序式结构编程**

在互联网计算机上，Canister调用其他的Canister是异步的, 但是Motoko语言可以让你顺序式结构对系统进行编程。调用函数返回的未来的值是异步信息，await架构可以将这些函数调用链接起来，就像他们是同步的一样。

```text
actor Factorial {
 var last = 1;
 public func next() : async Nat {
 last *= await Counter.inc();
 return last;
 }
};
ignore await Factorial.next();
ignore await Factorial.next();
await Factorial.next();
```



**现代型系统**

Motoko 对于熟悉 Javascript 和其他流行的语言的人来说是没有障碍的，并且提供了先进的功能，比如可靠性，通用性，可变性和模型匹配。

```text
type Tree<T> = {
 #leaf : T;
 #branch : {left : Tree<T>; right : Tree<T>};
};
func iterTree<T>(tree : Tree<T>, f : T -> ()) {
 switch (tree) {
 case (#leaf(x)) { f(x) };
 case (#branch{left; right}) {
 iterTree(left, f);
 iterTree(right, f);
 };
 }
};
// Compute the sum of all leaf nodes in a tree
let tree = #branch { left = #leaf 1; right = #leaf 2 };
var sum = 0;
iterTree<Nat>(tree, func (leaf) { sum += leaf });
sum
```



**自动生成** **IDL** **文件**

SDK 会以一种称为 Candid 的语言中性格式导出您的接口定义。因此，其他具有权限的 Canister，浏览器驻留的代码和智能手机应用程序都可以调用您的函数。Motoko 编译器还可以读取和写入接口定义文件，从而允许 Motoko 与使用其他语言编程的容器无缝交互。

例如前面的 命名为 Counter（计数器） 的 actor \( 罐子 Canister\), 会产生下面这个 Candid IDL：

```text
service Counter : {
 inc : () -> (nat);
}
```

\*\*\*\*

**永久独立保存**

Internet 计算机会保留运行容器的内存页面。 因此，Actor 的状态及其所有内存数据结构会无限期地存活，因此无需特地“保存”它们。

例如，在这个为文本名称分配顺序 ID 的注册表服务中，即使在多个节点之间复制 Canister 的状态，并且不驻留在内存中，哈希表的状态也会在调用之间保留。

```text
import Text "mo:base/Text";
import Map "mo:base/HashMap";
actor Registry {
 let map = Map.HashMap<Text, Nat>(10, Text.equal, Text.hash);
 public func register(name : Text) : async () {
 switch (map.get(name)) {
 case null {
 map.put(name, map.size());
 };
 case (?id) { };
 }
 };
 public func lookup(name : Text) : async ?Nat {
 map.get(name);
 };
};
await Registry.register("hello");
(await Registry.lookup("hello"), await Registry.lookup("world"))
```

\*\*\*\*

**更新**

Motoko 提供了许多功能来帮助您利用永久独立保存，其中包括一些语言功能，这些功能可以在升级容器软件时使堆自动迁移。

例如，Motoko 允许您将某些变量声明为稳定变量。 稳定变量的值会在软件升级过程中自动保留。

看一下这个定义为stable（稳定）的Counter（计数器）：

```text
actor Counter {
 stable var value = 0;
 public func inc() : async Nat {
 value += 1;
 return value;
 };
}
```

它被安装后，在数值递增了 n 次后，不需要中断就可以升级增加更多命令：

```text
actor Counter {
 stable var value = 0;
 public func inc() : async Nat {
 value += 1;
 return value;
 };
 public func reset() : async () {
 value := 0;
 }
}
```

因为数值被定义为 stable，因此升级后将保留计数器的当前状态 n。 计数将从 n 开始，而不是从 0 重新开始。

因为新界面与先前界面兼容，所以引用该服务的现有客户端将继续工作，但是新客户端将能够利用其升级功能（附加的重置功能）。

对于仅靠稳定变量无法解决的情况，Motoko 提供了用户可定义的升级挂钩，在升级之前和之后立即运行，并允许您将任意状态迁移到稳定变量。

**还有更多...**

Motoko 提供了许多其他提高开发人员生产力的功能，包括子类型化，任意精度算术和垃圾回收。

Motoko 并非（也不打算成为）实现容器的唯一语言。 如果它不适合您的需求，我们也正在努力为 SDK 添加 Rust 支持。 我们的目标是使任何语言（使用针对 WebAssembly 的编译器）都能够生成可在 Internet 计算机上运行的容器，并通过与语言无关的 Candid 接口与其他（可能是外国的）容器进行互操作。

其量身定制的设计意味着 Motoko 至少在可预见的将来，应该成为在 Internet 计算机上进行编码的最简单，最安全的语言。



