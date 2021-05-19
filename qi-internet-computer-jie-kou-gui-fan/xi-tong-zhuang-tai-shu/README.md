# 系统状态树

系统状态的一部分是公开的（例如，通过[请求：读状态](https://sdk.dfinity.org/docs/interface-spec/index.html#http-read-state)或[认证数据](https://sdk.dfinity.org/docs/interface-spec/index.html#system-api-certified-data)）的验证方法（见[认证](https://sdk.dfinity.org/docs/interface-spec/index.html#certification)中机械证明）。本节会抽象地描述系统状态的内容。

从概念上讲，系统状态是一棵带有标签子枝的树，叶中有值。等效地，系统状态是从路径（标签序列）到值的映射，其中的域是无前缀的。

标签始终是二进制大对象（但通常具有人类可读的表现形式）。在本文档中，建议使用斜线作为分隔符来编写路径。实际的编码实际上并没有使用斜杠作为分隔符，并且标签可能正常包含了0x2F字节（ASCII /）。值可以是自然数，文本值或二进制大对象。

本节指定了树中与公共相关的路径。

