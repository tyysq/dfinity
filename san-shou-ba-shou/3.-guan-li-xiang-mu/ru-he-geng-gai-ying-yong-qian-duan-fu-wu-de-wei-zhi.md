# 如何更改应用前端服务的位置

您可以通过修改dfx.json配置文件中的设置来更改默认的主机名和端口号，以运行本地Internet Computer副本进程并为应用程序前端提供服务。

例如：

```text
"start": {
 "port": 8000,
 "address": "127.0.0.1",
 "serve_root": "src/hello/public/"
```

\`\`

