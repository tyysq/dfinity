# 修改Cargo配置文件



Cargo.toml文件为每个Rust包提供一个清单。清单包含了包的配置明细。为准备Rust项目运行在Internet Computer上，我们需要拷贝默认的Cargo.toml文件并修改一些详细配置信息。

修改Cargo.toml文件：

1. 如果有必要，运行pwd命令来检查您是否在项目的根目录下。
2. 运行以下命令拷贝默认的Cargo.toml文件到src目录：

**`cp Cargo.toml src/Cargo.toml`**

在Internet Computer上运行的项目通常使用一个项目级别的Cargo.toml文件为项目的Canister成员设置工作区，并在源代码目录中使用第二个Cargo.toml文件为每个Canister配置参数。

    3. 用文本编辑器打开项目根目录下的Cargo.toml文件

默认情况下，该文件包含\[package\]和\[dependencies\]部分。

    4. 用类似以下\[workspace\]部分来替换\[package\]：

```text
[workspace]
members = [
 "src/my_rust_program",
]
```

有关\[workspace\]部分和键值信息，请参阅[\[workspace\]](https://doc.rust-lang.org/cargo/reference/workspaces.html)。有关Cargo.toml配置的其他部分和键值，请参阅[清单格式](https://doc.rust-lang.org/cargo/reference/manifest.html)。

    5. 删除\[dependencies\]部分

    6. 保存并关闭文件

    7. 在文本编辑器中打开src/Cargo.toml文件

    8. 增加类似以下带有主要源代码目录的\[lib\]

```text
[lib]
path = "main.rs"
```

    9. 更新\[dependencies\]部分的依赖项

    10. 保存并关闭文件

