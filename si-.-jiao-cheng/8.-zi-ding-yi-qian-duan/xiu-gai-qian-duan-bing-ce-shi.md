# 修改前端并测试

查看前端后，可以进行一些修改

修改步骤

1. 编辑器中打开index.jsx文件，并修改style设置。例如，你可能想要修改字体并在输入框使用占位文字，可以像下面一样修改

```text
// Modify the front-end in the React JavaScript
class MyHello extends React.Component {
 constructor(props) {
 super(props);
 this.state = {
 name: '',
 message: '',
 };
 }
 async doGreet() {
 const greeting = await custom_greeting.greet(this.state.name);
 this.setState({ ...this.state, message: greeting });
 }
 onNameChange(ev) {
 this.setState({ ...this.state, name: ev.target.value });
 }
 render() {
 return (
 <div style={{ "font-family": "sans-serif" }}>
 <div style={{ "font-size": "30px" }}>
 <p>Greetings, from DFINITY!</p>
 <p> Type your message in the Name input field, then click <b> Get Greeting</b> to display the result.</p>
 <div style={{ "margin": "30px" }}>
 <input id="name" placeholder="Type text here" value={this.state.name} onChange={ev => this.onNameChange(ev)}></input>
 <button onClick={() => this.doGreet()}>Get Greeting!</button>
 </div>
 <div>Greeting is: "<span style={{ "color": "green" }}>{this.state.message}</span>"</div>
 </div>
 </div>
 );
 }
}
render(<MyHello />, document.getElementById('app'));

```

  2. 运行下面的命令重新构建项目

```text
dfx build
```

   3. 运行下面的命令部署项目

```text
dfx canister install --all --mode reinstall
```

    4. 刷新浏览器显示custom\_greeting\_assets canister的页面查看结果

例如

![](https://uploader.shimo.im/f/EKXeeWoNCjRheNfF.png!thumbnail)

    5. 输入新的消息查看结果

![](https://uploader.shimo.im/f/BNCmkB32DjAqUjEu.png!thumbnail)

