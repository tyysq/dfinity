# 创建新项目

 创建新项目需要用到 dfx 命令

    创建新项目步骤如下

1. 打开终端
2. 进入工作目录
3. 运行下面的命令来创建项目

**`dfx new explore_hello`**

    这条命令会创建一个新的 explore\_hello 项目，包含一个默认的项目目录结构，同时会初始化为一个 git 仓库。如果安装了 node.js，还会包含前端代码和相关依赖

为了保证兼容性，项目名称只能使用字母和下划线。

    4. 运行下面的命令查看默认目录结构

      **`ls -l explore_hello`**

      项目目录结构中默认包含至少一个 src 子目录，一个模板 README.md 文件和一个默认的 dfx.json 配置文件

      如果安装了 node.js，项目目录下会包含以下文件

      **`explore_hello/`**

**`├── README.md      # default project documentation`**

**`├── dfx.json       # project configuration file`**

**`├── node_modules   # libraries for front-end development`**

**`├── package-lock.json`**

**`├── package.json`**

**`├── src            # source files directory`**

**`|   └── explore_hello`**

**`│       ├── main.mo`**

**`│       └── public`**

**`│           └── index.js`**

**`└── webpack.config.js`**

     默认项目目录包含以下文件

* 默认的 README 文件，用于项目说明
* 默认的 dfx.json 配置文件，用于项目配置
* 默认的 src 目录，存放应用源码文件

    默认的 src 目录包含模版文件 main.mo，你可以修改来包含核心程序逻辑

    这个教程内容很基础，只需要用到 main.mo 文件。如果安装了 node.js，项目目录会包含应用前端相关的文件和目录。前端开发和 public 目录下的模板文件会在后续教程中解释。

