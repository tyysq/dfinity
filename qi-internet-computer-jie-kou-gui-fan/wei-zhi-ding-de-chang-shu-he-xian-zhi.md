# 未指定的常数和限制

本规范可能引用某些常量和限制，但未指定其具体值（暂时），即它们是由实现定义的。许多资源限制仅与指定系统的错误处理行为有关（如上所述，在本文​​档中也没有对此进行精确描述）。此列表不完整。

* MAX\_CYCLES\_PER\_MESSAGE

尝试执行一条消息之前，canister必须具有的周期数，这将从消息执行之前的canister余额中扣除。请参阅[消息执行](https://sdk.dfinity.org/docs/interface-spec/index.html#rule-message-execution)。

* MAX\_CANISTER\_BALANCE

最大canister周期余额。任何多余的余额都将被抛弃。小于2^64。

