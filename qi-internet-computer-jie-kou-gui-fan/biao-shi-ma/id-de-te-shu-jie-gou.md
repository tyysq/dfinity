# ID的特殊结构

在本节中，H表示SHA-224，·表示blob联系，\|p\|表示p以字节为单位的长度，编码为单个字节。

id有几种类别：

1.  _不透明ID_。

这些总是由系统生成的，并且在系统外部没有任何有意义的结构。

> **注意：**

> 通常，这些以byte 0x01结尾，但是IC的用户不必关心这一点。

1. _自我认证ID_。

格式：H\(public\_key\) · 0x02 （29字节）。

 如果外部用户拥有相应的私钥，则可以将这些ID作为 sender 用作请求的ID 。公钥使用[签名](https://sdk.dfinity.org/docs/interface-spec/index.html#signatures)中的编码之一。

1. _派生ID_

格式：H\(\|registering\_principal\| · registering\_principal · derivation\_nonce\) · 0x03（29字节）。

当一个ID需要注册时，将对这些ID进行特殊处理。在这样的请求中，请求ID的人都可以提供derivation\_nonce。通过将其与请求方的标识码进行拼凑，每个标识码都有一个ID空间，只有他们才能从中注册ID。

> **注意：**

> 派生ID当前未在本文档中明确使用，但可以在内部或将来使用。

1. _匿名ID_

格式为0x04，用于匿名调用方。可以在没有签名的情况下用于调用和查询请求。

当系统创建一个_新的_ ID时，它永远不会创建一个自我认证ID，匿名ID或着是可能来自容器或用户的ID。

