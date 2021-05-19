# 注册Canister标识符

根据您喜欢的开发工作流程，可以在准备编译程序之前或之后注册一个唯一的Canister标识符。 例如，如果要在编写任何代码之前为子网上的程序保留唯一的标识符，可以通过运行dfx canister create命令来实现。 此命令实际上创建了一个空的Canister占位符，您以后可以在其中安装代码。

为Canister注册唯一标识符：

1. 在本地计算机打开终端
2.  通过运行与以下命令类似的命令，为计划创建的Canister创建一个新项目：

**`dfx new YOUR-PROJECT-NAME`**

请注意，默认情况下，您用于项目的名称也用作Canister名称。

    3. 进入新项目目录

    4. 打开dfx.json配置文件，并设置要使用的Internet Computer网络的主机和端口。

如果您将本地主机用作Internet Computer网络提供者，则可以跳过此步骤。

如果您想在编译代码前为其他Canister创建标识符，在配置文件中可以随意修改Canister名字或添加Canister设置

    5. 运行以下命令启动Internet Compter网络

**`dfx start --background`**

在大多数情况下，仅当您在本地运行Internet Computer网络时，才需要执行此步骤。

如果要注册要在远程网络上运行的Canister，则应包括--network命令行选项，以在该网络上执行任务。

    6. 通过运行以下命令，为dfx.json中定义的Canister注册唯一标识符：

**`dfx canister create --all`**

该命令创建.dfx/local目录，并将canister\_ids.json文件添加到该目录。

