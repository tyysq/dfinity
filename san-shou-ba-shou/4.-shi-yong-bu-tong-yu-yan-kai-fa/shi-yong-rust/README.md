# 使用Rust

您可以使用Cargo编译程序并使用WebAssembly作为输出来创建一个Rust项目运行在Internet Computer上。

本节总结了在Internet Computer上将Rust程序作为Canister部署时所涉及的关键步骤。然而，您应该知道，此处描述的步骤仅说明了一种方法，其他的实现方式也是可能的。

请注意，[Rust Canister开发工具包（Rust CDK）](https://github.com/dfinity/cdk-rs)提供了一些快捷方式，可简化编写查询和更新函数调用的过程，并提供了一些[示例](https://github.com/dfinity/cdk-rs/tree/next/examples)来帮助您开始构建基于Rust的项目，但您也可以为Internet Computer开发应用程序而不使用Rust CDK。

