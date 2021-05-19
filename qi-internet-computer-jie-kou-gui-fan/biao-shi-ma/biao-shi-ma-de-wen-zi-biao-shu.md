# 标识码的文字表述



> **注意：**

> 该文本表示形式实际上并未显示在界面中（界面中永远为blob），因此它只是建议的约定。

我们指定_规范的文本格式_，在需要以文本格式打印或阅读主体时（例如在日志消息，事务浏览器，命令行工具，源代码中）建议使用此格式。

blob 的文本表述 b 为 rouped\(Base32\(CRC32\(b\) · b\)\)其中

* CRC32是一个四字节的校验序列，按照ISO 3309，ITU-T V.42和[其他](https://www.w3.org/TR/2003/REC-PNG-20031110/#5CRC-algorithm)规定定义
* Base32是[RFC 4648中](https://tools.ietf.org/html/rfc4648#section-6)定义的Base32编码，未添加填充字符。
* 中间的点表示连接。
* Grouped接受一个ASCII字符串，并-每5个字符插入一个分隔符（破折号）。最后一组可能包含少于5个字符。分隔符永远不会出现在开头或结尾。

文本表示通常以_小写字母_打印，但不区分大小写地进行解析。

因为标识码的最大大小为29个字节，所以文字表述将不超过63个字符（10乘以5加3个字符，中间有10个分隔符）。

> 提示：

> canister的ID 0xABCD01 有检查顺序 0x233FF206（[在线计算器](https://crccalc.com/?crc=ABCD01&method=crc32&datatype=hex&outtype=hex)）；因此，最终ID为em77e-bvlzu-aq。

> bash中从十六进制编码到十六进制的示例编码（可以将以下内容粘贴到终端中）：

```text
function textual_encode() {
  ( echo "$1" | xxd -r -p | /usr/bin/crc32 /dev/stdin;     echo -n "$1" ) |
  xxd -r -p | base32 | tr A-Z a-z |
  tr -d = | fold -w5 | paste -sd'-' -
}
function textual_decode() {
  echo -n "$1" | tr -d - | tr a-z A-Z |
  fold -w 8 | xargs -n1 printf '%-8s' | tr ' ' = |
  base32 -d | xxd -p | tr -d '\n' | cut -b9- | tr a-z A-Z
}
```

