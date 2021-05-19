# 查看默认前端文件



本篇教程中，你将使用默认的main.mo文件，只需要修改前端代码。在修改代码前，让我们看一看默认的前端代码。

查看前端代码步骤

1. 编辑器中打开src/custom\_greeting\_assets/src/index.html文件                                          这个前端文件是应用的默认入口，由dfx.json文件的frontend.entrypoint指定。                这个文件包含标准HTML代码和指向CSS的引用以及位于src/custom\_greeting\_assets/assets目录的图片。默认的index.html文件也包含了一个输入框和一个可点击按钮的标准HTML语法。                                                                               这个前端和[Viewing the default front-end](../1.-tan-suo-mo-ren-xiang-mu/)章节一样

    2. 编辑器中打开src/custom\_greeting\_assets/src/index.js文件

```text
import { Actor, HttpAgent } from '@dfinity/agent';
import { idlFactory as custom_greeting_idl, canisterId as custom_greeting_id } from 'dfx-generated/custom_greeting';


const agent = new HttpAgent();
const custom_greeting = Actor.createActor(custom_greeting_idl, { agent, canisterId: custom_greeting_id });


document.getElementById("clickMeBtn").addEventListener("click", async () => {
  const name = document.getElementById("name").value.toString();
  const greeting = await custom_greeting.greet(name);


  document.getElementById("greeting").innerText = greeting;
}
```

* * 默认的index.js的第一个import语句使用JavaScript Agent库创建一个actor和一个agent实例
  * 第二个import语句会准备custom\_greeting canister来构造actor
  * 接下来的2个语句构造了agent和actor
  * 剩余的代码提供了处理默认程序的文档对象

1. 关闭index.js继续

