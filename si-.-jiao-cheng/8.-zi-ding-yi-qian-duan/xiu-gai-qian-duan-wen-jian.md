# 修改前端文件

现在为默认程序创建一个新的前端

准备前端文件步骤

1. 编辑器中打开webpack配置文件（webpack.config.js）
2. 用index.jsx替换前端配置项index.html

```text
entry: {
 // The frontend.entrypoint points to the HTML file for this build, so we need
 // to replace the extension to `.js`.
 index: path.join(__dirname, info.frontend.entrypoint).replace(/\.html$/, ".jsx"),
},
在plugin上添加下面的module
module: {
 rules: [
 { test: /\.(js|ts)x?$/, loader: "ts-loader" }
 ]
},
```

    3. 在项目根目录创建tsconfig.json文件

    4. 编辑器中打开tsconfig.json，复制粘贴下面的内容

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

    5. 保存修改并关闭tsconfig.json文件继续

    6. 打开默认的src/custom\_greeting\_assets/src/index.js文件，删除7-12行

    7. 复制粘贴下面的示例代码

```text
// Insert these lines after the import statements for
// importing an agent and an actor
import * as React from 'react';
import { render } from 'react-dom';
// Replace the default index.js content with
// React JavaScript
class MyHello extends React.Component {
 constructor(props) {
 super(props);
 this.state = {
 name: 'Name',
 message: '',
 };
 }
 async doGreet() {
 const greeting = await custom_greeting.greet(this.state.name);
 this.setState({ ...this.state, message: greeting });
 }
 onNameChange(ev) {
 this.setState({ ...this.state, name: ev.target.value });
 }
 render() {
 return (
 <div style={{ "font-size": "30px" }}>
 <div style={{ "background-color": "yellow" }}>
 <p>Greetings, from DFINITY!</p>
 <p> Type your message in the Name input field, then click <b> Get Greeting</b> to display the result.</p>
 </div>
 <div style={{ "margin": "30px" }}>
 <input id="name" value={this.state.name} onChange={ev => this.onNameChange(ev)}></input>
 <button onClick={() => this.doGreet()}>Get Greeting!</button>
 </div>
 <div>Greeting is: "<span style={{ "color": "blue" }}>{this.state.message}</span>"</div>
 </div>
 );
 }
}
render(<MyHello />, document.getElementById('app'));
```

    8. 运行下面的命令将index.js文件重命名为index.jsx

```text
mv src/custom_greeting_assets/src/index.js src/custom_greeting_assets/src/index.jsx
```

    9. 打开src/custom\_greeting\_assets/src/index.html文件，将body内容替换为&lt;div id="app"&gt;&lt;/div&gt;

例如

```text
<!doctype html>
<html lang="en">
 <head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width">
 <title>custom_greeting</title>
 <base href="/">
 <link type="text/css" rel="stylesheet" href="main.css" />
 </head>
 <body>
 <div id="app"></div>
 </body>
</html>
```

