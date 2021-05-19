# 修改默认程序



为了编写电话号码查询程序，创建一个新的main.mo文件

源码修改步骤

1. 编辑器中打开src/phonebook/main.mo 源码文件
2. 复制粘贴下面的示例代码到main.mo文件

```text
// Import standard library functions for lists
import L "mo:base/List";
import A "mo:base/AssocList";
// The PhoneBook actor.
actor {
 // Type aliases make the rest of the code easier to read.
 public type Name = Text;
 public type Phone = Text;
 // The actor maps names to phone numbers.
 flexible var book: A.AssocList<Name, Phone> = L.nil<(Name, Phone)>();
 // An auxiliary function checks whether two names are equal.
 func nameEq(l: Name, r: Name): Bool {
 return l == r;
 };
 // A shared invokable function that inserts a new entry
 // into the phone book or replaces the previous one.
 public func insert(name: Name, phone: Phone): async () {
 let (newBook, _) = A.replace<Name, Phone>(book, name, nameEq, ?phone);
 book := newBook;
 };
 // A shared read-only query function that returns the (optional)
 // phone number corresponding to the person with the given name.
 public query func lookup(name: Name): async ?Phone {
 return A.find<Name, Phone>(book, name, nameEq);
 };
};
```

代码中有几个重点

* Name和Phone定义为自定义Text类型，像这样创建自定义类型可以增强代码可读性
* insert函数是一个update调用，lookup函数是一个query调用
* Phone类型通过？Phone定义为可选值

