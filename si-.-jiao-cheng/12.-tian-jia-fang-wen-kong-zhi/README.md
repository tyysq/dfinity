# 12.添加访问控制

应用程序通常需要基于角色权限来控制不同用户可以执行的操作。

为说明如何创建和切换用户身份，本教程创建一个简单的程序，对不同角色用户显示不同的问候。

此例子中，有三个命名角色-owner, admin 和 authorized

* 具有admin角色的用户显示You have a role with administrative privileges
* 具有authorized角色的用户显示Would you like to play a game?
* 没有分配这些角色的用户显示Nice to meet you!

此外，只有安装Canister的用户才授予owner角色，只有owner和admin角色才能分配角色 给其他用户

在较高级别上，每个用户都有一个公用/专用密钥对。 用户访问的公用密钥与容器标识符结合在一起，形成一个安全主体，然后可以用作消息调用方来验证对在Internet Computer上运行的容器进行的功能调用。 下图提供了有关用户身份如何认证消息调用者的简化视图。

![](../../.gitbook/assets/image%20%2821%29.png)

