# 为拥有一个Canister设置身份

在大多数情况下，第一次运行dfx canister create命令时会自动为您创建一个默认用户身份。此默认身份包括为您的本地用户帐户生成的公钥和私钥对。通常，此默认标识还是您创建的所有项目和您部署的所有Canister的默认所有者。但是您可以创建和使用您选择的用户来代换默认用户。

例如，以下场景说明了创建一个registered\_owner身份，该身份随后用于注册，构建，部署和调用pubs项目。

为项目设置身份：

1. 运行以下命令创建新项目：

**`dfx new pubs`**

    2. 运行以下命令进入项目目录：

**`cd pubs`**

    3. 运行以下命令在后台启用Internet Computer网络：

**`dfx start --background`**

    4. 运行以下命令创建一个新的身份

**`dfx identity new registered_owner`**

    5. 运行以下命令，将当前用户设置为registered\_owner

**`dfx identity use registered_owner`**

    6. 运行以下命令为项目注册，构建和部署Canister：

**`dfx canister create --all`**

**`dfx build --all`**

**`dfx canister install --all`**

这些命令使用registered\_owner身份运行，从而使该用户成为已部署Canister的所有者。

    7. 运行以下命令，通过调用greet函数以验证部署是否成功：

**`dfx canister call pubs greet '("Sam")'`**

