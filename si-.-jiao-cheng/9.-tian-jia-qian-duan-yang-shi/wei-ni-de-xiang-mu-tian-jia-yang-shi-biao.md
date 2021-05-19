# 为你的项目添加样式表



你现在可以创建一个新的CSS文件并添加到你的项目

添加步骤

1. 导航到src/contacts\_assets/assets目录

```text
cd src/contacts_assets/assets/
```

    2. 重命名main.css文件到mycontacts.css

```text
mv main.css mycontacts.css
```

    3. 打开mycontacts.css文件并删除已有内容

    4. 定义一些样式属性

```text
html {
    background-color: bisque;
}


body {
    font-family: Arial, Helvetica, sans-serif;
    display: block;
    margin: 10px;
}


h1 {
    color: darkblue;
    font-size: 32px;
}


div.new-entry {
    margin: 30px 20px 30px 20px;
}


.new-entry > div {
    margin-bottom: 15px;
}


table {
    margin-top: 12px;
    border-top: 1px solid darkblue;
    border-bottom: 1px solid darkblue;
}


#form {
    margin: 30px 0 30px 20px;
}


button {
    line-height: 20px;
}


#lookupName {
    margin-right: 
```

    5. 保存更改并关闭mycontacts.css文件继续

    6. 导航到src/contacts\_assets/src目录

```text
cd ../src
```

    7. 编辑器中打开默认的index.js文件并删除已有内容

    8. 复制粘贴下面的示例代码到index.js文件

```text
import { Actor, HttpAgent } from '@dfinity/agent';
import { idlFactory as contacts_idl, canisterId as contacts_id } from 'dfx-generated/contacts';
import * as React from 'react';
import { render } from 'react-dom';
import '../assets/mycontacts.css'; // Import custom styles
const agent = new HttpAgent();
const contacts = Actor.createActor(contacts_idl, { agent, canisterId: contacts_id });
class Contact extends React.Component {
 constructor(props) {
 super(props);
 this.state = {
 };
 }
 async doInsert() {
 let name = document.getElementById("newEntryName").value;
 let add1 = document.getElementById("newEntryAddress1").value;
 let add2 = document.getElementById("newEntryAddress2").value;
 let email = document.getElementById("newEntryEmail").value;
 let phone = document.getElementById("newEntryPhone").value;
 contacts.insert(name, add1, add2, email, parseInt(phone, 10));
 }
 async lookup() {
 let name = document.getElementById("lookupName").value;
 contacts.lookup(name).then(opt_entry => {
 let entry;
 if (opt_entry.length == 0) {
 entry = { name: "", description: "", phone: ""};
 } else {
 entry = opt_entry[0]
 }
 document.getElementById("newEntryName").value = entry.name;
 document.getElementById("newEntryAddress1").value = entry.address1;
 document.getElementById("newEntryAddress2").value = entry.address2;
 document.getElementById("newEntryEmail").value = entry.email;
 document.getElementById("newEntryPhone").value = entry.phone.toString();
 });
 }
 render() {
 return (
 <div class="new-entry">
 <h1>My Contacts</h1>
 <div>
 Add or update contact information:
 <form id="contact">
 <table>
 <tr><td>Name:</td><td><input id="newEntryName"></input></td></tr>
 <tr><td>Address 1 (street):</td><td><input id="newEntryAddress1"></input></td></tr>
 <tr><td>Address 2 (city and state):</td><td><input id="newEntryAddress2"></input></td></tr>
 <tr><td>Email:</td><td><input id="newEntryEmail"></input></td></tr>
 <tr><td>Phone:</td><td><input id="newEntryPhone" type="number"></input></td></tr>
 </table>
 </form>
 </div>
 <div>
 <button onClick={() => this.doInsert()}>Add Contact</button>
 </div>
 <div>
 Lookup name: <input id="lookupName" style={{ "line-height": "20px" }}></input>
 <button onClick={() => this.lookup()}>Lookup</button>
 </div>
 </div>
 );
 }
}
document.title = "DFINITY CONTACT EXAMPLE";
render(<Contact />, document.getElementById('contacts'));
```

    9. 运行下面的命令重命名修改的index.js文件为index.jsx

```text
mv index.js index.jsx
```

    10. 编辑器中打开默认的src/contacts\_assets/src/index.html文件，然后替换main.css为mycontacts.css样式文件，并更新body内容为&lt;div id="contacts"&gt;/div&gt;

例如

```text
<!doctype html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width">
 <title>contacts</title>
 <base href="/">
 <link type="text/css" rel="stylesheet" href="mycontacts.css" />
</head>
<body>
 <div id="contacts"></div>
</body>
</html>
```

    11. 回到项目根目录

例如

```text
cd ../../..
```

