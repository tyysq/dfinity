# 为身份分配角色



要将管理员角色分配给ic\_admin身份，请执行以下操作：

1. 通过运行以下命令，将默认用户设置为当前活动用户：

```text
dfx identity use default
```

    2. 通过使用Candid语法运行类似于以下内容的命令，将admin角色 分配给ic\_admin身份：

```text
dfx canister call access_hello assign_role '((principal "c5wa6-3irl7-tuxuo-4vtyw-xsnhw-rv2a6-vcmdz-bzkca-vejmd-327zo-wae"),opt variant{admin})'
```

注意：确保将身份哈希替换为ic\_admin身份的dfx identity get-principal命令返回的哈希。

（可选项）您可以重新运行命令以调用my\_role函数以验证角色分配。

```text
dfx --identity ic_admin canister --no-wallet call access_hello my_role
```

必须使用--no-wallet选项才能查看分配给ic\_admin身份的角色，而不是Cycles钱包。 该命令显示的输出类似于以下内容：

**`(opt variant { admin })`**

1. 通过运行以下命令，使用刚刚分配了admin角色的ic\_admin用户身份调用greet函数：

```text
dfx --identity ic_admin canister --no-wallet call access_hello greet "Internet Computer Admin"
```

输出类似以下内容：

```text
(
  "Hello, Internet Computer Admin. You have a role with administrative privileges.",
)
```

