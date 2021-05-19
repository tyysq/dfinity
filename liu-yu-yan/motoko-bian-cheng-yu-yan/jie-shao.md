# 介绍

Motoko是一个现代编程语言，可用于在[Internet  Computer](https://sdk.dfinity.org/docs/developers-guide/concepts/what-is-ic.html#ic-overview)平台上的程序，也可用在其他平台的程序上。

**适用性**

Motoko是一种现代语言，旨在供那些对JavaScript或其他现代编程语言（例如Rust，Swift，TypeScript，C＃或Java）中的现代面向对象和/或函数式编程习惯有基本了解的程序员使用。

**异步通讯和安全运行**

Motoko允许使用现代的编程习惯，包括针对分布式应用程序的特殊编程。 每个应用程序都包含一个与其他actor通信的Actor，无需使用共享状态，而是使用（异步）消息传递。  Motoko的基于actor的编程程序允许人类可读的消息传递模式，并且它们强制每个网络交互服从某些规则并避免某些常见错误。

Motoko允许使用现代的编程习惯，包括针对分布式应用程序的特殊编程。 每个应用程序都包含一个与其他actor通信的Actor，无需使用共享状态，而是使用（异步）消息传递。  Motoko的基于actor的编程程序允许人类可读的消息传递模式，并且它们强制每个网络交互服从某些规则并避免某些常见错误。

为了执行，Motoko静态地编译为[WebAssembly](https://sdk.dfinity.org/docs/language-guide/about-this-guide.html#wasm)，这是一种可移植的二进制格式，可以在现代计算机硬件上清晰地运行，因此可以在Internet和[Internet Computer](https://sdk.dfinity.org/docs/developers-guide/concepts/what-is-ic.html#ic-overview)上广泛执行。

**每个microservice都充当actor**

Motoko为开发人员提供了基于actor的编程模型，以表达服务器的行为，包括Internet和[Internet computer](https://sdk.dfinity.org/docs/developers-guide/concepts/what-is-ic.html#ic-overview)上的microservice。

一个actor类似于一个对象，但是特别之处在于它的孤立状态是远程存在的，并且它与世界的交互是异步的。

Actor之间的所有通信都涉及使用Internet计算机的消息传递协议通过网络异步传递消息。 Actor的消息是按顺序处理的，因此状态修改绝不会引起资源竞争。

InternetComputer提供的基础计算平台可确保每个基于消息的同步都将结束，但这样做可能由于分布式系统中出现的常见原因（包括超时）而导致每个同步失败。

**异步的Actor**

与其他现代编程语言一样，Motoko允许使用人体工程学语法进行组件之间的异步通信。

在Motoko编写的程序中，每个交流组件都是一个演actor。

作为使用actor的示例，也许本身是一个actor，请看以下三行程序：

```text
let result1 = service1.computeAnswer(params);
let result2 = service2.computeAnswer(params);
finalStep(await result1, await result2)
```

我们可以将这个程序的执行总结为3个步骤：

1. 该程序向两个不同的服务发出两个请求（第1行和第2行），每个服务都在内部作为actor（或是说对象）运行。
2. 在每个结果值上使用关键字await，程序会等待每个结果准备就绪（第3行）。
3. 程序通过调用finalStep函数在最后一步（第3行）中使用两个结果。

一般来说，服务交错执行而不是互相等待，因为这样做可以减少整体延迟。 但是，如果我们尝试在没有特殊语言支持的情况下以这种方式减少延迟，则这种交错执行的方式将迅速牺牲清晰度和简单性。

即使在没有交错执行的情况下（例如，如果上面只有一个调用，而不是两个），出于相同的原因，程序仍然允许清晰和简单。 就是说，它们向编译器发出信号，指示在何处转换程序，从而使程序员从扭曲程序逻辑的过程中解放出来，以便将其执行与底层系统的消息传递循环相交织。

在这里，该程序使用第3行中的await以一种简单的方式来表达这种交织行为，这就是一种Motoko提供的人类可读语法。

在缺少这些功能的语言设置中，开发人员不仅会直接调用这两个函数，而且会采用非常高级的编程模式，可能会在系统提供的“事件处理程序”中注册开发人员提供的“回调函数”。 每个回调将在异步事件的运行结果完成时触发。 这种系统级编程功能强大，但非常容易出错，因为它会将高级数据流分解为通过共享状态进行通信的低级系统事件。 有时，这种样式是必需的，但在这里却不是。

相反，我们的程序避开了这种繁琐的编程风格，采用了更为自然，直接的风格，让每个请求都类似于一个普通的函数调用。 像当今大多数现代软件一样，这种更简单，风格化的编程形式已变得越来越流行，用于表达与外部环境交互的实用系统。 但是，它需要特殊的编译器和类型系统支持，我们将在下面更详细地讨论。

**支持异步运行**

在异步计算设置中，允许程序及其运行环境执行彼此同时发生的内部计算。

具体来说，异步程序是指那些程序，向其他程序发出请求时，不需要等待就可以继续执行自己的程序。 同时，允许程序在等待时（也许是在主动地）在此环境中进行继续执行。 在上面的示例中，程序发出第二个请求，同时仍在等待第一个微服务。

相应的，环境（其他程序）对该程序发来的请求也不需要等待，环境（其他程序）在等待该回答的同时也可以继续运行。

我们上面没有显示这种“通知”模式的示例，因为它使用了回调（以及高阶函数和控制流），因此更加复杂。

**async和await的语法形式**

为了满足清晰和简单的需求，Motoko采用了越来越常见的程序结构async和await，这为程序员提供了一种结构化语言，用于描述潜在复杂的异步依赖关系图。

[异步语法](https://sdk.dfinity.org/docs/language-guide/language-manual.html#exp-async)引入了期货的概念。 将来值表示将在将来某个时候异步传递的结果的“承诺”（在上面的第一个示例中未显示）。 当我们在'[Actors and async data](https://sdk.dfinity.org/docs/language-guide/actors-async.html)'中介绍actor时，您将了解有关期货的更多信息。

在这里，我们仅使用调用service1.computeAnswer（params）和service2.computeAnswer（params）所产生的代码。

Await语句在同步未来的数值，并可能暂停计算，直到生产者（外界的程序）将这个未来值计算出来为止。 我们在上面的示例中展示了await语句的用了2次，它们正在等待两种服务的结果。

当开发人员使用这些关键字时，编译器会根据需要对程序进行转换，通常会对程序的控制流和数据流进行复杂的转换，而手工操作将很繁琐。 同时，Motoko的类型（type）系统对这些结构强制使用某些正确的使用模式，包括在消费者和生产者之间流动的类型始终一致，并且允许在服务之间发送的数据类型在此处流动，并且不（例如）包含 [私有可变状态](https://sdk.dfinity.org/docs/language-guide/mutable-state.html)。

**类型是静态的**

与其他现代编程语言一样，Motoko允许每个变量携带函数的值，对象的值或原始数据的值（例如，字符串，单词或整数）。 还存在[其他类型的值](https://sdk.dfinity.org/docs/language-guide/basic-concepts.html#intro-values)，包括记录，元组和称为变量的\`\`标记数据''。

Motoko享有类型安全性的正式属性，也称为类型安全性。 我们通常用以下短语来概括这个想法：[井井有条的Motoko程序不会出错](https://sdk.dfinity.org/docs/language-guide/basic-concepts.html#intro-type-soundness)，这意味着它们不会通过将程序结构视为错误类型来滥用它们。

例如，Motoko程序中的每个变量都带有一个关联的类型，并且在程序执行之前静态地知道该类型。 编译器会检查每个变量的每次使用，以防止运行时类型错误，包括空指针错误。

从这个意义上说，Motoko类型在程序源代码中提供了一种经过编译器验证的可信文档形式。

通常，动态测试可以检查Motoko类型系统无法达到的性能。 虽然是现代的，但Motoko类型系统不是以任何新方式，来故意显示'先进'或与众不同。 相反，Motoko的类型系统整合了现代但易于理解的实用类型系统的经验教训，为[通用的分布式编程](https://sdk.dfinity.org/docs/language-guide/about-this-guide.html#modern-types)提供了一种易于上手但又数学精确的语言。

