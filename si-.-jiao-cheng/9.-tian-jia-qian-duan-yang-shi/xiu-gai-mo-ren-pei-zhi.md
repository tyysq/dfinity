# 安装React框架



如果你不了解React框架，可以在[React网站](https://reactjs.org/)进行探索。

安装React模块步骤如下

1. 运行下面的命令安装React模块

```text
npm install --save react react-dom
```

    2. 运行下面的命令安装Typescript加载器

```text
npm install --save typescript ts-loader
```

 Note

另一个安装模块的方法是，你可以编辑package.json文件来添加模块

```text
{
  "name": "custom_greeting_assets",
  "version": "0.1.0",
  "description": "",
  "keywords": [],
  "scripts": {
    "build": "webpack"
  },
  "devDependencies": {
    "@dfinity/agent": "0.7.1",
    "assert": "2.0.0",
    "buffer": "6.0.3",
    "events": "3.3.0",
    "html-webpack-plugin": "5.3.1",
    "process": "0.11.10",
    "stream-browserify": "3.0.0",
    "terser-webpack-plugin": "5.1.1",
    "util": "0.12.3",
    "webpack": "5.24.4",
    "webpack-cli": "4.5.0"
  },
  "dependencies": {
    "react": "^17.0.2",
    "react-dom": "^17.0.2",
    "ts-loader": "^8.1.0",
    "typescript": "^4.2.4"
  }
}
```

