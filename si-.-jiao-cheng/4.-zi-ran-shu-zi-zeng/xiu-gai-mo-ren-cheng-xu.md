# 修改默认程序



到目前为止，只修改了项目主程序的名称。接下来需要修改src/my\_counter/increment\_counter.mo文件来定义一个名为Counter的actor并实现increment ，get 和set函数。

源码修改步骤

1. 检查是否当前目录为项目根目录
2. 编辑器中打开src/my\_counter/increment\_counter.mo 源码文件，并删除已有内容
3. 复制粘贴下面的示例代码到increment\_counter.mo文件

```text
// Create a simple Counter actor.
actor Counter {
 stable var currentValue : Nat = 0;
 // Increment the counter with the increment function.
 public func increment() : async () {
 currentValue += 1;
 };
 // Read the counter value with a get function.
 public query func get() : async Nat {
 currentValue
 };
 // Write an arbitrary value with a set function.
 public func set(n: Nat) : async () {
 currentValue := n;
 };
}
```

示例代码解析

* 实例中定义的currentValue变量包含stable关键字代表状态-这个值可以被修改增加并获取-也就是可维护

这个关键字保证了变量值在程序升级后不可改变

* currentValue定义也指定其类型为自然数（Nat）
* 程序包含2个公共update方法-increment和set函数-以及一个query方法，在这里是get函数

需要更多关于stable和flexible变量的信息，请 在[_Motoko Programming Language Guide_](http://language-guide:motoko.html)查看[Stable variables and upgrade methods](http://language-guide:upgrades.html) 

    4. 保存并关闭文件

