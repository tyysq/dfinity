# 如何使用默认模板

就像您在教程中可能已经注意到的那样，项目默认包含一个模板webpack.config.js文件。 因为webpack是基于JavaScript的应用程序的流行且高度可配置的模块捆绑器，所以默认的webpack.config.js文件使添加要使用的特定模块（如react和markdown）变得容易。

默认情况下，模板webpack.config.js文件还会根据项目dfx.json文件中的条目创建Canister别名。 如果查看模板webpack.config.js文件中的代码，您会发现它使用以下代码块执行此别名创建任务：

```text
// List of all aliases for canisters. This creates the module alias for
// the `import ... from "ic:canisters/xyz"` where xyz is the name of a
// canister.
const aliases = Object.entries(dfxJson.canisters)
 .filter(([name,value]) => value.main)
 .reduce((acc, [name,value]) => {
 const outputRoot = path.join(__dirname, dfxJson.defaults.build.output, name);
 const filename = path.basename(value.main, ".mo");
 return {
 ...acc,
 ["ic:canisters/" + name]: path.join(outputRoot, filename + ".js"),
 ["ic:idl/" + name]: path.join(outputRoot, filename + ".did.js"),
 };
}, {});
```

