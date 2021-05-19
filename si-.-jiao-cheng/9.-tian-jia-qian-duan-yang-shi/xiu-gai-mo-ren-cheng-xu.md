# 修改默认程序



本章节中，你将会修改主程序，运行你保存查询联系信息

修改源码步骤如下

1. 打开src/contacts/main.mo文件并删除已有内容
2. 复制粘贴下面的代码

```text
import List "mo:base/List";
import AssocList "mo:base/AssocList";
actor Contact {
 flexible var contact: ContactsMap = List.nil<(Name, Entry)>();
 type Name = Text;
 type Phone = Nat;
 type Entry = {
 name: Name;
 address1: Text;
 address2: Text;
 email: Text;
 phone: Phone;
 };
 type ContactsMap = AssocList.AssocList<Name, Entry>;
 func nameEq(lhs: Name, rhs: Name): Bool {
 return lhs == rhs;
 };
 public func insert(name0: Name, address10: Text, address20: Text, email0: Text, phone0: Phone): async () {
 let newEntry : Entry = {
 name = name0;
 address1 = address10;
 address2 = address20;
 email = email0;
 phone = phone0;
 };
 let (newContacts, _) = AssocList.replace<Name, Entry>(
 contact,
 name0,
 func(n: Name, m: Name) = n == m,
 ?newEntry
 );
 contact := newContacts;
 };
 public query func lookup(name: Name): async ?Entry {
 return AssocList.find<Name, Entry>(contact, name, nameEq);
 };
};
```

    3. 保存修改并关闭main.mo文件继续

