# 在Canister中验证计算函数



现在，项目已经部署到本地ICP网络，并且可以使用dfx canister call命令进行测试。

测试部署的程序步骤如下

1. 使用dfx canister call命令调用calc Canister中的add函数并传递参数10

```text
dfx canister call calc add '(10)'
```

当传递单引号包含的参数，接口描述语言（IDL）会解析参数类型，因此无需指定参数类型

验证命令返回值是否符合add函数执行结果的期望。例如，程序输出为

```text
(10)
```

    2. 运行下面的命令调用mul函数并传递参数3

```text
dfx canister call calc mul '(3)'
```

 验证命令返回值是否符合mul函数执行结果的期望。例如，程序输出为

```text
(30)
```

    3. 运行下面的命令调用sub函数并传递参数5

```text
dfx canister call calc sub '(5)'
```

 验证命令返回值是否符合sub函数执行结果的期望。例如，程序输出为

```text
(25)
```

    4. 运行下面的命令调用div函数并传递参数5

```text
dfx canister call calc div '(5)'
```

 验证命令返回值是否符合div函数执行结果的期望。例如，程序输出为

```text
(opt 5)
```

注意到div函数返回了一个可选的结果。程序会输出可选值可以使div函数在出现除零错误时返回null

因为cell变量是一个整数，可以调用函数并输入负数。例如，运行下面的命令

```text
dfx canister call calc mul '(-4)'
```

 返回

```text
(-20)
```

    5. 运行下面的命令调用clearall函数并验证cell变量重置为0

```text
dfx canister call calc clearall
```

程序输出为

```text
(0)
```

