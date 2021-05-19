# 在部署的Canister中调用方法

部署完canister后，可以模拟一个终端用户调用canister提供的方法了。本章节中，激活get方法查询counter值，increment方法增加couter值，set方法传一个参数更新counter到任意输入的值。

测试部署的程序步骤如下

1. 运行下面的命令调用get函数，该函数会读取在部署的canister当前的currentValue值

```text
dfx canister call my_counter get
```

命令输出currentValue值为0

```text
(0)
```

    2. 运行下面的命令调用increment函数，该函数会将部署的canister当前的currentValue值加1

```text
dfx canister call my_counter increment
```

这个命令会将变量加一-改变状态-但不会有返回值

    3. 再次运行下面的命令获取currentValue当前的值

```text
dfx canister call my_counter get
```

 命令返回currentValue值为1

```text
(1)
```

    4. 运行额外的命令并使用不同的参数来测试其他方法

例如，运行类似下面的命令设置并返回counter值

```text
dfx canister call my_counter set '(987)'
dfx canister call my_counter get
```

 返回值为987

```text
dfx canister call my_counter increment
dfx canister call my_counter get
```

 返回值为988

