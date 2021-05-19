# 入口和输出配置

创建容器别名后，模板webpack.config.js文件将生成一个Webpack配置，该配置将Canister别名作为导入的模块自动添加到项目dfx.json文件中定义的默认前端入口点中。例如，使用默认设置，将类似于以下内容的导入添加到src/CANISTER\_assets/public/index.js文件中：

**`import CANISTER-ALIAS from 'ic:canisters/CANISTER-ALIAS';`**

