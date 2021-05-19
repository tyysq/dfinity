# 探索connected的源代码



社交链接canister connectd由下面的文件构成：

* digraph.mo文件提供创建一个有向的点线图来描述用户的连接关系
* main.mo包含actor和定义用户连接关系的关键函数，可以被linkedUp示例应用调用
* types.mo文件定义自定义类型，可以映射一个点到一个用户信息，这在digraph和main程序文件中有使用

