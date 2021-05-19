# 修改默认程序



在本教程中，您将修改模板源代码，以包含用于接受Cycles和检查余额的新功能。

1. 在文本编辑器中打开src/cycles\_hello/main.mo文件，然后删除现有内容。
2. 将以下示例代码复制并粘贴到文件中：

```text
import Nat64 "mo:base/Nat64";
import Cycles "mo:base/ExperimentalCycles";
shared(msg) actor class HelloCycles (
 capacity: Nat
 ) {
 var balance = 0;
//Return the current cycle balance
 public shared(msg) func wallet_balance() : async Nat {
 return balance;
 };
//Return the cycles received up to the capacity allowed
 public func wallet_receive() : async { accepted: Nat64 } {
 let amount = Cycles.available();
 let limit = capacity - balance;
 let accepted =
 if (amount <= limit) amount
 else limit;
 let deposit = Cycles.accept(accepted);
 assert (deposit == accepted);
 balance += accepted;
 { accepted = Nat64.fromNat(accepted) };
 };
//Return the greeting
 public func greet(name : Text) : async Text {
 return "Hello, " # name # "!";
 };
//Return the principal of the caller/user identity
 public shared(msg) func owner() : async Principal {
 let currentOwner = msg.caller;
 return currentOwner;
 };
};
```

让我们看一下该程序的一些关键要素：

* 该程序导入Motoko基础库ExperimentalCycles，该库提供处理Cycles的基本功能。
* 该程序使用一个actor类，而不是单个actor，以便它可以具有多个actor实例，以接受不同的Cycles数量，直至所有实例的容量。
* 容量作为参数传递给actor类。
* msg.caller标识与该调用关联的账户。

    3. 保存并关闭文件

