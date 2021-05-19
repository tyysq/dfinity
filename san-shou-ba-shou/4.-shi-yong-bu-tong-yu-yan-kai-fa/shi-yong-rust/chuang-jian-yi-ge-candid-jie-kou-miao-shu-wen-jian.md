# 创建一个Candid接口描述文件

除了dfx.json配置文件之外，您还需要一个Candid接口描述文件（例如，my\_rust\_program.did），以映射程序输入参数和返回值格式到Candid中伪代码表现形式。

添加Candid接口描述文件：

1. 如有必要，用pwd命令来检查您是否仍在项目目录下。
2. 在项目的src目录下创建一个新的Candid接口描述文件（例如my\_rust\_program.did）
3. 在文本编辑器中打开这个描述文件并且为程序中每一个函数添加描述

例如，如果my\_rust\_program是一个简单的计数器程序，使用increment, read和write函数，my\_rust\_program.did看起来象这样：

```text
service : {
 "increment": () -> ();
 "read": () -> (nat) query;
 "write": (nat) -> ();
}
```

