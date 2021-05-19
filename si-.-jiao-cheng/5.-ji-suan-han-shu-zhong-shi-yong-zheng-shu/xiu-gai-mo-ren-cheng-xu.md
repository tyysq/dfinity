# 修改默认程序



在本章节中，需要用执行基本算数操作的程序替换默认程序。

源码修改步骤

1. 检查是否当前目录为项目根目录
2. 运行下面的命令从模板mai n.mo文件创建calc\_main.mo新文件

```text
cp src/calc/main.mo src/calc/calc_main.mo
```

    3. 编辑器中打开src/calc/calc\_main.mo文件并删除已有内容

    4. 复制粘贴下面的代码到calc\_main.mo文件

```text
// This single-cell calculator defines one calculator instruction per
// public entry point (add, sub, mul, div).


// Create a simple Calc actor.
actor Calc {
  flexible var cell : Int = 0;


  // Define functions to add, subtract, multiply, and divide
  public func add(n:Int) : async Int { cell += n; cell };
  public func sub(n:Int) : async Int { cell -= n; cell };
  public func mul(n:Int) : async Int { cell *= n; cell };
  public func div(n:Int) : async ?Int {
    if ( n == 0 ) {
      // null encodes div-by-zero error
      return null
    } else {
      cell /= n; ?cell
    }
  };


    // Clear the calculator and reset to zero
    public func clearall() : async Int {
    if (cell : Int != 0)
       cell -= cell;
    return cell
    };
```

示例代码中使用了整数类型，允许使用正数或负数。如果想要使代码只处理正数，可以将数据类型改为自然数（Nat）

    5. 保存修改并关闭文件继续

