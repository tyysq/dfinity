# 添加Canister配置文件



当您用DFINITY Canister SDK创建一个新项目时，dfx new命令自动添加一个默认dfx.json配置文件到项目目录。因为他们已经使用Cargo来创建Rust项目，所以您需要手工在项目目录下创建该文件。

添加dfx.json配置文件：

1. 如有必要，用pwd命令来检查您是否仍在项目目录下。
2. 在项目根目录下创建一个dfx.json配置文件。
3. 在文本编辑器中打开dfx.json文件。
4. 添加类似以下设置的version和canisters键到dfx.json文件

```text
{
 "version": 1,
 "canisters": {
 "my_rust_program": {
 "type": "custom",
 "candid": "src/my_rust_program.did",
 "wasm": "target/wasm32-unknown-unknown/debug/my_rust_program.wasm",
 "build": "cargo build --target wasm32-unknown-unknown --package my_rust_program"
 }
 }
}
```

让我们详细看看这些配置

* version用于标识创建项目软件的版本号
* canisters部分指定项目的Canister名字。在本例中，仅有一个名为my\_rust\_program的Canister
* 因为不是可标识的canister类型之一（motoko或assets），type键设置为custom
* candid键指定用于此项目的Candid接口描述文件的名称和位置。
* wasm键指定cargo编译命令生成的WebAssembly文件路径
* build键指定用于编译输出的cargo命令
* These are the minimum settings required. As you build more complex programs, you might need to include additional configuration details in the Cargo.toml file, the dfx.json file, or both files. 这些是最小配置需要。随着您构建更复杂的程序，您会需要在Cargo.toml, dfx.json中进行其他详细配置

    5. 保存并关闭文件

