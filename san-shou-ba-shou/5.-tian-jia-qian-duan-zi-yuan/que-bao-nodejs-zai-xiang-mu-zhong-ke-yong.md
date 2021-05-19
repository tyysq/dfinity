# 确保nodejs在项目中可用



由于项目依赖于webpack为默认的前端提供框架，因此您必须在开发环境中安装node.js并在项目目录中对其进行访问。

* 如果要在不使用默认Webpack配置和Canister别名的情况下开发项目，则可以从dfx.json文件中删除资源Canister，也可以使用特定的Canister名称来构建项目。

  **`dfx build hello`**

* 如果您使用默认的Webpack配置并且运行dfx build失败，则应尝试在项目目录中运行npm install，然后重新运行dfx build。
* 如果在项目目录中运行npm install不能解决问题，则应检查webpack.config.js文件的配置是否存在语法错误。

