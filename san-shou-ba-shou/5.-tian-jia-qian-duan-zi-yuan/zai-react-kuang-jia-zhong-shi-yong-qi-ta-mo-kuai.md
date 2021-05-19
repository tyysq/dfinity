# 在React框架中使用其他模块

[示例库](https://github.com/dfinity/examples)中的一些教程和示例项目说明了如何使用npm install命令添加React模块。 您可以使用这些模块来构造要在项目中使用的用户界面组件。 例如，您可以运行以下命令来安装react-router模块：

**`npm install --save react react-router-dom`**

然后，您可以使用该模块构造类似于以下内容的导航组件：

```text
import React from 'react';
import { NavLink } from 'react-router-dom';
const Navigation = () => {
 return (
 <nav className="main-nav">
 <ul>
 <li><NavLink to="/myphotos">Remember</NavLink></li>
 <li><NavLink to="/myvids">Watch</NavLink></li>
 <li><NavLink to="/audio">Listen</NavLink></li>
 <li><NavLink to="/articles">Read</NavLink></li>
 <li><NavLink to="/contribute">Write</NavLink></li>
 </ul>
 </nav>
 );
}
export default Navigation;
```

