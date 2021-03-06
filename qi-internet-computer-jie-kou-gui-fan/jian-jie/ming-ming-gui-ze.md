# 命名规则

为了使本文档具有一定的一致性，我们尝试精确地使用以下术语：

我们避免使用“客户端（client）”一词，因为它可能是Internet Computer的客户端，也可能是组成Internet Computer的分布式网络中的客户端。取而代之的是，我们使用术语“_用户（user）”_来表示与Internet Computer交互的外部实体，即使在大多数情况下它将会是代表（人类）用户的某些代码（有时称为“代理（agent）”）。

Canisters的公共入口\(public entry point\)称为_方法（method）_。可以将方法声明为_更新方法\(_ _update methods_ _\)_（保留状态变化）或_查询方法（query method）_（丢弃状态变化，无法进行进一步的调用）。

方法可以被_称为_从请求方到_被请求方_，并最终招致_响应_ 既不是一个 返回\(reply\) 或 拒绝\(reject\)。方法可能具有_参数_，这些_参数_在方法的调用中提供了具体的_参数数据_。

内部容器（inter-canister）间调用不能区分更新方法和查询方法。内部容器的调用可以保留状态变化，因此类似于更新方法调用。请注意，canister向自身发出的调用\(call\)也算作“内部容器”。外部调用可以是可同时调用两种方法的：_更新调用_ 和仅可调用查询方法的_查询调用_。

在内部，调用或响应作为_消息\(message\)_从_发送方\(sender\)_发送到_接收方\(receiver\)_。消息是没有响应\(response\)的。

WebAssembly _函数_由WebAssembly模块导出或由System API提供。这些函数可以被_调用，_并且可以_捕获_或_返回_（可能带有返回值）。函数也具有并带有参数。

外部_用户\(user\)_通过在HTTPS接口上发出_请求\(request\)_来与系统交互。请求的响应可以是正常返回\(repliy\)，也可以是拒绝\(reject\)。某些请求会创建内部消息。

容器，用户等由_标识码\(principal\)_（有时也称为_id）标识_。

