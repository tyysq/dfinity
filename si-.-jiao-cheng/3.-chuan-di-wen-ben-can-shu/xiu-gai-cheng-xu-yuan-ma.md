# 修改程序源码

为了充分理解本章节的内容，可以修改源码来尝试不同的结果。例如，可以修改location函数返回多个城市名称。

修改代码实验步骤

1. 打开dfx.json配置文件，修改默认的location\_hello设置为favorite\_cities   这个步骤中，canister名称和主程序路径都要使用favorite\_cities
2. 保存并关闭dfx.json文件
3. 运行下面的命令复制location\_hello源文件目录来匹配dfx.json配置文件

**`cp -r src/location_hello src/favorite_cities`**

    4. 打开src/favorite\_cities/main.mo文件

    5. 复制粘贴下面的代码用2个替换location函数

```text
actor {
  public func location(cities : [Text]) : async Text {
    return "Hello, from " # (debug_show cities) # "!";
  };
  public func location_pretty(cities : [Text]) : async Text {
    var str = "Hello from ";
    for (city in cities.vals()) {
      str := str # city #", ";
    };
    return str # "bon voyage!";
  }
};
```

 注意代码中的Text被中括号包裹。在这里，Text代表UTF-8字符集。被中括号包裹的类型表示这是该类型的数组。在这里，\[Text\]代表UTF-8字符集类型的数组，允许程序接收并返回多个字符串。

对array使用apply操作的示例代码如下

```text
public func apply<A, B>(fs : [A -> B], xs : [A]) : [B] {
    var ys : [B] = [];
    for (f in fs.vals()) {
      ys := append<B>(ys, map<A, B>(f, xs));
    };
    ys;
};
```

想了解更多关于数组相关操作的内容，请查看Moto编程语言参考中的数组模块。在快速开始的示例部分也有数组使用的示例。

    6. 运行下面的命令注册构建并部署应用

**`dfx deploy`**

    7. 运行下面的命令调用location方法并使用Candid接口描述规则传递city参数

**`dfx canister call favorite_cities location '(vec {"San Francisco";"Paris";"Rome"})'`**

命令使用Candid接口描述规则\(vec { val1; val2; val3; }\) 来返回一组值。需要更多关于Candid接口描述语言的信息，请查看Candid语言章节。

命令输出示例

**`("Hello, from ["San Francisco", "Paris", "Rome"]!")`**

    8. 运行下面的命令调用location\_pretty方法并使用Candid接口描述规则传递city参数

```text
dfx canister call favorite_cities location_pretty '(vec {"San Francisco";"Paris";"Rome"})'
```

 命令输出

```text
("Hello from San Francisco, Paris, Rome, bon voyage!")
```

