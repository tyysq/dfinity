# 关于本语言的指导

《 Motoko编程语言指南》介绍了通用Motoko编程语言的主要功能，并提供了示例和参考信息，以帮助您了解该语言的细微差别以及如何应用该语言的实际含义。

Motoko编程语言经过优化，用于开发在InternetComputer平台上运行的程序，并可以与DFINITY的Canister软件开发套件（SDK）一起使用。 但是，您也可以使用Motoko为其他平台编写程序，并在其他程序中运行。本指南将会介绍Motoko适用于InternetComputer的专用特点和适用于其他平台的通用特点。

**目标听众**

本指南为想要探索或计划使用Motoko编程语言的程序员提供参考信息和示例。 无论您是开发要在InternetComputer平台上运行的程序还是使用DFINITY Canister SDK的程序，本指南中的大多数信息均适用。

该指南假定您熟悉基本的编程原理和术语，并且至少具有使用高级编程语言（例如C ++或Rust）编写程序的经验，或者具有使用脚本语言（例如JavaScript或TypeScript）的实践经验。 另外，Motoko结合了函数式编程的某些方面，因此您可能会发现一些有关函数式编程设计原理的知识，这些知识有助于学习使用Motoko。

尽管本指南旨在帮助来自不同背景的读者理解Motoko的基本设计原理和语义，但您应记住，语言实现和文档也在不断发展。

**使用本指南**

为了提供学习Motoko的框架，您可能要先回顾一下'[Engineering values and goals](https://sdk.dfinity.org/docs/language-guide/about-this-guide.html#_engineering_values_and_goals)'。 '[Engineering values and goals](https://sdk.dfinity.org/docs/language-guide/about-this-guide.html#_engineering_values_and_goals)'描述了Motoko编程语言开发和发展的核心设计考虑因素。

考虑到这些考虑因素，您可以开始在简单的代码示例和小型程序中探索基本概念，包括type（类型）和type annotation（类型注释）的作用。

熟悉基本概念和术语后，后面的部分将介绍以更有趣的方式进行计算的程序，包括函数抽象，用户定义的type（类型），用户定义的actor和异步通信。

本指南中的大多数代码示例都是相互关联的：您可以实时编辑示例，在浏览器中解释代码并查看结果。 提供口译员是出于教育目的。 尽管解释器支持大多数语言功能，但它们与真正的编译器并不完全相同。 例如，对于中等大小的输入，您可能会出现堆栈溢出，而实际的编译器会很好地处理输入。 不完全支持某些系统功能，例如循环，导入Canister和调用状态更改查询。

**文档约定**

本指南中使用以下约定

* 固定宽度的字体用于示例代码，程序名称，程序输出，文件名以及您在命令行中键入的命令。
* **粗体**文本用于强调命令，按钮或用户界面文本，并引入新术语。
* _斜体_用于书名并强调特定的单词或术语。
* CAUTION样式用于指示缺少或不完整的内容。
* WARNING样式用于指示内容过时或潜在不正确的位置。
* NOTE样式用于指示描述了尚不支持但计划用于将来版本的功能的内容。

**工程价值和目标**

Motoko设计和实施背后的工程工作是由一组核心价值观和目标驱动的。  DFINITY工程组织使用这些价值观和目标来定义语言功能并确定其优先级，并在进行中的语言开发过程中对其进行添加和改进。

为了使指导工程工作的原则透明化，工程组织确定了以下核心值和次要值集，以驱动Motoko编程语言的发展。

核心价值

以下指导原则按优先顺序代表了工程组织的核心价值：

1. 与[InternetCompute](https://sdk.dfinity.org/docs/developers-guide/concepts/what-is-ic.html#ic-overview)r平台的无缝连接可确保Motoko为基于角Actor的模型，异步消息传递，数据持久性，接口描述语言的互操作性和其他功能提供完整的语言支持。
2. 人机工程学，以确保Motoko包含熟悉性，简单性，清晰性，明确性和其他人为因素。
3. 形式上的正确性，以确保Motoko保持状态隔离，安全类型系统和类型安全性，精度，模式匹配，适当的默认值以及编码最佳实践。

次要价值

以下原则代表了工程组织的次要价值，这些次要价值被认为是重要的，但不是主要的驱动因素：

1. 富有表现力，因此Motoko提供了一流的功能，多态性，模式匹配等，并且随着语言的发展而不断扩展。
2. 性能，因此Motoko最初可以提供合理的快速操作，并且随着语言的发展而不断提高。
3. 准备就绪，因此Motoko以库和示例的形式附带了“包括电池”，并通过DFINITY Canister SDK进行了现成的集成。

非目标

作为对核心价值观和目标的反对，工程组织还确定了以下属于工程工作范围之外的“非目标”：

1. 具有更高级的类型系统和更复杂的类型。
2. 在设计或执行中简化功能（“Worse is Better”的方法）。
3. 与现有智能合约平台的互操作性。

查找更多信息

有关将Motoko与DFINITY Canister SDK结合使用的信息，请参阅SDK开发人员工具。

与Motoko 的设计，使用，部署或语言的设计本身有关的各种主题的背景信息，请考虑以下资源作为起点：

WebAssembly

* [WebAssembly home page](https://webassembly.org/).
* [WebAssembly overview video \(youtube\)](https://www.youtube.com/watch?v=fvkIQfRZ-Y0).

现代类型系统

* [Practical Foundations for Programming Languages](http://www.cs.cmu.edu/~rwh/pfpl/) by Robert Harper. Cambridge University Press, 2016.
* [Types and Programming Languages](https://www.cis.upenn.edu/~bcpierce/tapl/) by Benjamin C. Pierce. The MIT Press.

获得更多帮助

如果您正在寻找更多信息或技术支持，请访问DFINITY网站，以快速访问常见问题，技术文章，开发人员更新和其他资源。 在网站上，您可以搜索知识库文章，打开和查看支持案例，注册新闻通讯，阅读最新的博客文章，查看操作方法视频，下载软件更新或与社区成员交流想法。

除了网站上提供的资源外，您还可以使用社交媒体与DFINITY或其他开发人员联系，或者访问DFINITY社区论坛，并加入对话。

