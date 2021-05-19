# 修改默认程序



在[探索默认项目](../1.-tan-suo-mo-ren-xiang-mu/)章节，已经介绍了创建新项目会创建一个默认的src目录，并包含一个main.mo程序模板文件。

源码修改步骤

1. 编辑器中打开src/location\_hello/main.mo 源码文件
2. 修改默认源码，用有city参数的location函数替换greet函数

例如

```text
actor {
 public func location(city : Text) : async Text {
 return "Hello, " # city # "!";
 };
};
```

    3. 保存并关闭文件

