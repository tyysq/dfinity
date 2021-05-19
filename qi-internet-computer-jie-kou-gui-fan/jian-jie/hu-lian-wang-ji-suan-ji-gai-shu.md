# 互联网计算机概述

如果要使用Internet Computer作为应用程序的开发人员，则首先需要创建一个Canister_模块_，其中包含应用程序的WebAssembly代码和配置，然后使用[HTTP接口](https://sdk.dfinity.org/docs/interface-spec/index.html#http-interface)进行部署。您更加方便可以使用Motoko语言和SDK创建容器。但是，如果您想使用自己的工具包，那么本文档将描述[容器模块看起来是什么样的](https://sdk.dfinity.org/docs/interface-spec/index.html#canister-module-format)以及[WebAssembly代码如何与系统交互](https://sdk.dfinity.org/docs/interface-spec/index.html#system-api)。

一旦您的应用程序在Internet Computer上运行，​​它就是一个_容器_，用户可以与它进行交互。他们可以根据[系统API](https://sdk.dfinity.org/docs/interface-spec/index.html#system-api)使用[HTTP接口](https://sdk.dfinity.org/docs/interface-spec/index.html#http-interface)与容器进行交互。

用户还可以使用HTTP接口发出只读查询，该查询速度更快，但无法更改容器的状态。

![](https://uploader.shimo.im/f/485sfRPORXoN0j4v.png!thumbnail)

_图1. Internet Computer的典型用法。（这是一个简化的视图；箭头表示多个交互步骤或轮询。）_

“ [HTTPS接口](https://sdk.dfinity.org/docs/interface-spec/index.html#http-interface)”和“[容器接口（系统API）](https://sdk.dfinity.org/docs/interface-spec/index.html#system-api) ”的部分描述了这些接口，并简要说明了它们的作用。之后，您将找到对Internet计算机的[更正式的描述](https://sdk.dfinity.org/docs/interface-spec/index.html#abstract-behavior)，该描述更严格地描述了其抽象行为。

