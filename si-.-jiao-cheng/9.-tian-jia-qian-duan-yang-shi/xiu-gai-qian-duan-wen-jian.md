# 修改前端文件



现在可以为程序创建新的前端了

1. 编辑器中打开webpack配置文件（webpack.config.js）
2. 修改前端项用index.jsx替换默认index.html

```text
entry: {
 // The frontend.entrypoint points to the HTML file for this build.
 // Use the next line to change the extension. For example, the
 // default configuration changes the extension to `.js`.
 index: path.join(__dirname, info.frontend.entrypoint).replace(/\.html$/, ".jsx"),
},
```

    3. 定位plugins项上面的module键的注释例子，然后将下面的几行取消注释

```text
module: {
 rules: [
 { test: /\.(js|ts)x?$/, loader: "ts-loader" },
 { test: /\.css$/, use: ['style-loader','css-loader'] }
 ]
},
```

这些配置允许你的程序使用ts-loader编译器并导入css文件

    4. 保存webpack.config.js文件并退出

    5. 项目根目录下创建新的tsconfig.json文件

    6. 打开tsconfig.json文件，然后复制粘贴下面的内容到文件

```text
{
 "compilerOptions": {
 "target": "es2018", /* Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019' or 'ESNEXT'. */
 "lib": ["ES2018", "DOM"], /* Specify library files to be included in the compilation. */
 "allowJs": true, /* Allow javascript files to be compiled. */
 "jsx": "react", /* Specify JSX code generation: 'preserve', 'react-native', or 'react'. */
 },
 "include": ["src/**/*"],
}
```

    7. 保存修改并关闭tsconfig.json文件继续

